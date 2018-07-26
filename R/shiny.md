# Shiny

= interactive data visualization

## Architecture

* shiny-server: running R to calculate the data for the visualization 
    * code: server instructions
* client: displaying the visualization in browser
    * code: html (generated from R)
* all can be written inside one R-Script
* code run hierarchy:
    * outside shiny ui and server function: once per R session
    * inside server function: once per user
    * inside a reactive function: once per interaction

## UI Elements

Are written inside the `page`-function.
R functions write the html.

### Inputs

```R
sliderInput(inputId="num",
  label="choose number",
  value=25,
  min=1,
  max=100
  )
```

* all have `inputId`: 
* all have `label`: is displayed in the page
* then: additional arguments depending on type
* `actionButton()` can be used to trigger invalidates
    * stores the number of clicks in the input variable (don't use this number)
* they cannot be changed in the code

### Outputs

Place elements on the page. Called observers.

1. register in the `page`-function
2. create the element in the `server`-function

```R
  output$hist <- renderPlot({
    hist(rnorm(100))
  })
```

* `...Plot` function: determines the object to build
* code: builds the R object to transform
* `{}` braces are needed to define a unified code block

### static content

* added by R functions like: `tags$h1()` or `tags$a()`
    * give `<h1> </h1>` and `<a href=...></a>`
    * there are some wrapper functions to omit: `tags$`
* tags is a list of functions
* **usage**: `tags$a(href='www.google.de', 'google')
    * returns: `<a href='www.google.de'>google</a>`
    * every named argument will be made an atribute of the tag
    * unnamed args go inside the tag
* **text** does not need a tag
* important tags: `img`, `a`, `p`, `strong`, `code`, `italic`, `hr`, `br`, 
    * image files should be inside a `www/` folder (www must not be at the start of the path)
    * these files are accessible in a web browser
* **direct HTML** can be passed to the `HTML()` function

### Layout

* simple: `fluidPage()`
    * `fluidRow()` divides the page into different rows
    * together with `column(<width>, offset=<...>)` it can be build into a grid
        * a column is 12 units wide, that is connected to the `width` and `offset`
* **panels**
    * smallest grouping element
    * `wellPanel()` groups the insides into a grey well
    * `tabPanel()` is used for tabbed content
        * contained inside: `tabsetPanel()`, `navlistPanel()` or `navbarPanel()`
        * looks like: classic tabs, navigation menu (left), .??
    * `navbarMenu()` creates a drop down menu inside a tab-environment
        * the menu contains other `tabPanel`s
* layouts
    * there are prepackaged layouts in shiny:

```R
ui <- fluidPage(
  sidebarLayout(
    sidebarPanel(),
    mainPanel()
  )
)
```

* pages:
    * besides `fluidPage()` (responsive in size) there is `fixedPage()` (has three fixed sizes)
    * there are not many reasons to use: `fixedPage()`
    * `navbarPage()` creates a page with tabs
        * needs a **title**
        * consists of multiple `tabPanel`s
    * shinyDashboard is inside an extra package
```R
ui <- dashboardPage(
  dashboardHeader(),
  dashboardSidebar(),
  dashboardBody()
)
```

## Server Pattern 

### Reactivity

1. create a output object in the `page...`
2. build a `render...` object in the `server` function  (store it to the objects name)
3. use a `input$...` value in the `render...` function

* if some calculations are done, that are used by many observers: use `reactive()`
    * precalculate shared data e.g.: `new_data <- ...`
    * use the created object in the observers: `new_data()`
* reactive expressions cache their values

### prevent Reactivity  

* `isolate()` can be used for this
* calculate a value from an input field that does not change reactively
* **but** the value will be used if another input invalidates the observer

### trigger Invalidates

* use: `observerEvent(<input>, { code block })`
* all used input values in the code block are **isolated**
* another option is to use: `observe()`
    * no explicit `<input>`, the code block is not isolated

### delay Reactions

* with: `eventReactive()` 
    * combination of `observerEvent()` and `reactive()`
    * invalidates only if `<input>` is changed
    * stores the created object
    * notifies all observers, that use the object

### hidden reactive Values

* created by: `valuelist <- reactiveValues(<value> = <code>)`
    * use: `valueList$<value>`
* don't respond on any input
* have to be overwritten explicitly
    * e.g. link to one or more inputs (with: `observeEvent()`)

## Styling

Is done via CSS. Uses the `Bootstrap` R Module.

### global CSS  

* put CSS file into `www/` folder
* set the CSS-file in the `ui <- fluidPage()`-function
    * `theme = 'name.css',`
    * or  

```R
tags$head(
  tags$link(
    rel = 'stylesheet',
    type = 'text/css',
    href = 'name.css'
  )
)
```

### CSS in file 

* add the style information directly

```R
tags$style( HTML(
  p { color: red; }
) )
```

* source CSS into the file  
    * `readCSS('name.css')`
    * does not need to be in `www/`

### CSS for element

* edit the `style`-atribute of the elements 
    * `tags$h1('title', style='color:red;')`
