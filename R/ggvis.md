# ggvis 

package for data visualization and exporation.
Ideas from:
* ggplot (language)
* shiny (interactivity)
* dplyr (pipe)
* vega.js (web)

There is a difference between **scaled** and **unscaled** values.
They are used via assignment (`=` = scaled, `:=` = unscaled).
Scaled will be converted into a values space (good for numbers, bad for strings, that code colors).
Unscaled will be left as is (colors work, numbers are used as pixel lengths from top left)

The `~` operator means: interpret the value in the context of the data.
Without it searches for a global variable with the name.

## plotting

2D-plot with x/y data
and a smoothed mean-line.
Different `layer_` functions are used for different graph-styles.

### Scatterplot

```R
both %>%
  ggvis( x= ~temp, y= ~delay ) %>%
  layer_points() %>%
  layer_smooths()
# use a variable to define a colorscale
  ggvis( ~temp, ~delay, fill = ~precip ) %>%
```

### Histogram

```R
both %>%
  ggvis( ~delay ) %>%
  layer_histograms()
```

## reactives

One reactive can use variables from another.
When the variable changes, the change will be forwarded to the other reactive.
A dependency graph is build.

![dependency graph](./img/dependency_graph.png "dependency graph")

When conditions in ancestors change, the descendants are recomputed.

### slider

```R
both %>%
  ggvis( ~delay ) %>%
  layer_histograms(binwidth = input_slider(1, 10, value=5))
```
