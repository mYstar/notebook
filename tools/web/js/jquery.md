
- `$(document).ready(function(){});`: event callback, triggered when page is loaded
- `$.ajax`: builds a request
- `$('form').serialize()`: builds a URL encoded notation (GET) from form
    - e.g.: `var=value&var2=value2&var3=value3`
- `collection<element>.filter('selector'||function(index, element));`: reduces the collection to the elements that match the selector or return true

# selectors
- usage: `$('selector')`
- id: `#id`
- class: `.class`
- tagname: `tag`
- attribute: `tag[attr="val"]`
- compound: `tag.class childtag`
- avoid: `.class:not(.otherclass)`: excludes otherclass from result
- custom selectors:
    - position in list: `tag:odd` `tag:even` `tag:first` `tag:last`
    - form input elements: `form :text` `form :submit` `form :password`

# elements
- select: `$('element')`
- `element.attr('attrname')`: set/get attributes (also: `removeAttr()`)
- `element.val()`: set/get value of form input fields
- `element.text()`: set/get the text between the tags
- `element.html()`: set/get the whole html content of the element
- `element.click(function)`: set the onClick callback
- `element.find('selector');`: searches the descendants of element for a matching selector
- `element.show("fast"|"slow"|ms)`: shows hidden element (also `hide()`, `toggle()`, `fadeIn()`, `fadeOut()`, `fadeToggle()`, `slideUp()`, `slideDown`, `slideToggle`)
- `element.animate([css values], duration, callback)` (also: `stop()`)
    - concatenate .animate for stepped animation
    - relative animation: `[property: "+=50px"]`
    - activate/deactivate properties: `[property: "hide|show|toggle"]`
- manipulate classes: `addClass()` `removeClass()` `toggleClass()`
- sizes:
    - every function is setter|getter (inner... and outer... calculate width change acounting to the surroundings)
    - `width()` `height()`: without padding margin border
    - `innerWidth()` `innerHeight()`: with padding
    - `outerWidth()` `outerHeight()`: with padding + border
    - `outerWidth(true)` `outerHeight(true)`: with padding + border + margin


# events
- create: `$('selector').<event>(function)`
- event functions:
    - `element.off('handler');`: deletes an event handler
    - `element.click(...)` --> deprecated use: `element.trigger()` und `element.on()`
        - `ready`: when element is rendered (also: `resize`, `scroll`)
        - `click`: on mouseclick (also: `dblclick`, `hover`, `mouseenter`, `mouseleave`)
        - `keypress`: printing key pressed (also: `keydown` all keys, `keyup`)
        - `focus`: element is focused (opposite: `blur`)
        - `change`: on form change (also: `submit`)

# DOM manipulation
- all actions performed on selected elements
- `append()` `prepend()`: inside the element tag
- `before()` `after()`: outside the element
- `html()` `text()`
- `wrap()`: new tag around the element
- destructive: `remove()` `empty()` `unwrap()`
- traversing:
    - `parent()`: selects direct parent (also: `closest('selector')`, `parents()` `parentsUntil()`)
    - `children()`: selects all direct children
    - `find(selector)`: selects all descendants of the element
    - `siblings()`
    - `next()` `prev()`: select the following/leading sibling (also: `nextAll()`, `nextUntil()`, `prevAll()`, `prevUntil()`) 

# css
- `element.css("width":"newval", ...)`: gets|sets the property value

# jquery-UI
- `element.dialog()`: implements alert and confirm functionality as modal