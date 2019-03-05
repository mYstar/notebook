# ggplot2 

## components

* **data** (input) 
    * **aestetics** (mapping from data to layer elements)
* **layers** (visualization elements)
    * `geom`-functions
    * statistical informations
* scale
    * map data values to aestetic values (color, ...)
    * create legends and axes
* coordinates (visualization perspective, e.g. grid)
    * also: polar coordinates, map projection, ...
* faceting (visual drill down, like: pivot charts)
    * divides into subsets of the data, that are plotted individually
* themes (control the display)

## data 

* prepare by setting the factors

## plot

1. set the data 
2. map aestetics  
    * x and y for the axis mapping  
    * **fill** for the bar fillsize (continous variable)
    * **colour** for the color (categorial variable)
    * **shape** for the shape of e.g. points (categorial variable)
        * `'.'` = pixel sized 
        * `'1'` = hollow point
    * **group** forms multiple lines according to a categorial variable
        * `cut_width()` creates bins from a continous variable
    * **size** for the size of points (continous variable)
    * **alpha** opacity of the points
    * **weight** determines weighting, (alters: histogram, smooth, boxplot, densityplot)
    * conversion of data values to e.g. colors is done automatically
    * ordering can be altered by: `reorder()`
    * delete a mapping with `y=NULL`
3. set plottype
    * fixed (not scaled by data value) parameters here
    * e.g. `geom_point(colour="Blue")`
    * or use color to name plot elements `geom_point(colour='qc cycle')`
    * perform a (different) statistical calculation before displaying with `stat=`
        * `geom_point(stat='summary', fun.y='mean')`
4. save the plot  
    * with `ggsave()`
    * or: `saveRDS()` saves a raw plot object
        * can be manipulated later, without having the data
        * restore with `readRDS()`

### factor data

* **barplot**
```R
ggplot(titanic, aes(x=Survived)) +
  geom_bar()
```
    * counts the number of datapoints for bar height
    * vor precalculated heights use `geom_col()` 
        * also: the `y=` parameter + `stat='identity'` in the `geom`-function (alternative: `geom_point()`)
    * parameter: `stat=` can use other functions to determine the bar height  
        * `stat='summary_bin', fun.y=mean`

* multiple **groups**/faceting
    * used to draw the same plot for subsets of the data
    * display a plot for every group by: `facet_wrap(~ groupname) +` displays groups side by side 
    * `facet_wrap(group1 ~ group2) displays a grid with the combinations
    * `~` --> by

### continous data

* **timeseries**
    * with: `geom_line()`
    * x is time mostly
* **histogram** 
    * can be filled by factor data
```R
ggplot(titanic, aes(x=Age, fill=Survived)) +
  geom_histogram(binwidth = 5)
```
    * `geom_freqpoly()` is an alternative 
    * useful for: multiple histograms in one plot (through aestetics)
    * **density plots** `geom_density` are smoothed histograms
        * sums up little normal distributions
        * every desity estimate is standardized to 1 (absolute size is lost)
        * careful: many calculations and assumptions in the background -> hard to interpret
        * use the `alpha=` parameter to set opacity
    * for 2 connected data columns: `geom_bin2d()`
        * also useful for overplotting
        * alternative: `geom_hex()` (less artefacts)
* **conditional density plot**
    * is a variant of the histogram 
    * shows which group dominates in a specific area of the variable space
    * `position='fill'` does the trick
```R
ggplot(diamonds, aes(depth)) +
  geom_histogram(aes(fill = cut), binwidth = 0.1, position = "fill",
  na.rm = TRUE) +
  xlim(58, 68) +
  theme(legend.position = "none")
```

* **dotplot**
    * `geom_dotplot()`
    * displays a dot for each datapoint (no overlap)
    * useful for distribution of small datasets

* **boxplot** 
    * is a combination of factor and continous data
```R
ggplot(titanic, aes(x=Survived, y=Age)) +
  geom_boxplot(binwidth = 5)
```
    * also good in this case: `geom_jitter()` and `geom_violin()`

* **smoothed line**
    * `geom_smooth(method=...)`
    * default algorithm (`loess`) is good for small datasets
    * for more points (>1000) use `gam`
    * for a straight line use a linear model: `lm` or more robust `rlm` from library `MASS`

## 3D data  

* contour, density and bubble plots 
    * `geom_contour()`
    * `geom_point(aes(size=<z-variable>))`
* **rasterplot**
    * `geom_raster()` draws points in a 2d raster 
    * `geom_bin2d()` is a wrapper for counting the bin members
    * = 2D variant of `geom_bar()` (color is the bar height)
    * `binwidth=x, stat="function"` determines the function to summarize for the color dimension 


## map data 
* maps are drawn with `geom_polygon`
    * `coord_quickmap()` prevents distortion of the map
```R
ggplot(mi_counties, aes(lon, lat)) +
  geom_polygon(aes(group = group), fill = NA, colour = "grey50") +
  coord_quickmap()
```

## error data 

* calculation of the error is up to the developer
    * variables `ymin` and `ymax` mark the error range
* example data:
```R
err <- ggplot(df, aes(x, y, ymin = y - se, ymax = y + se))
```
* to display use:
    * **with** middle point:
    * `geom_crossbar()`
    * `geom_pointrange()`
    * `geom_smooth(stat = "identity")`
    * **without** middle point:
    * `geom_errorbar()`
    * `geom_linerange()`
    * `geom_ribbon()`

## look 

* set **labels** by: `labs( y="name", title= ...) +`
    * set the value range of the axes by: `xlim(min, max)` and `ylim(min, max)`
    * a `NA` value defaults to the automatic detection
* **themes** for easy changes: `theme_bw() +`
* insert text with: `geom_text()` or `geom_label()` (for a box behind the text)
    * use x and y to position (standard: middle of text, change with `hjust` and `vjust`)
        * to divert every text in a direction (to label points, but not overlap them) use: `nudge_x`, `nudge_y`
        * `Inf` and `-Inf` refer to the limits of the plot
    * all measurements are in mm
    * `label` sets the text
    * fonts available everywhere: `'serif', 'sans', 'mono'`
```R
ggplot(df, aes(x, y)) +
geom_text(aes(label = text))
```
* other additional elements:
    * lines: `geom_line()`, `geom_path()`, `geom_segment()`, `geom_hline()`, `geom_vline()`, `geom_abline()`, 
    * polygons: `geom_rect()`

## scales

* map the values (defined in `aes()`) to optical properties (e.g. colors)
* in default ggplot2 already creates a scale for every data column
* they can be changed by the `scale_<aestetic>_<type>`-functions
    * `aestetic` can be: `x`, `y`, `color`
    * `type`  can be: `discrete`, `continous`, `identity`
        * there is a special scale: `brewer` for colors
* if there are colors already in the data use: `+ scale_color_identity()`

### customising

* standard: use `scale_x_continuous()`
    * alternatives: `x`|`y`|`color`|`fill`, `continous`|`discrete`|`log10`
    * `NULL` deletes the corresponding element (`''` does not remove whitespace)
    * first argument is the name  
    * `breaks=` defines tickmarks
    * `minor_breaks=` defines the guidelines between the tickmarks
    * `labels=` defines text at tickmarks (you must set `breaks` when using this)
        * for `discrete`: use named arguments (e.g. `labels=c(fileset1='standard', fileset2='machines 9')`)
* helper functions: `xlab()`, `ylab()`
    * `labs()` defines titles for all mappings in `aes()` (e.g. `color`-legend)

## stats  

* calculate a statistical operation on the data 
* generate new variables (in the form `..variable..`)
* see documentation of the `stat` for a list of the variables

## position

* changes the position of overlapping elements  
* mostly used for stacking
* used with `position = ''`:
    * for **bars**, **boxplots**, **areas**
    * `stack` just stacks the elements not changing their heights 
    * `fill` stacks elements but scales the height to 1.0
    * for **points**
    * `nudge` moves points by offset
    * `jitter` creates random movement
    * `dodgejitter` dodges the points (no overlap) and adds a random element to it
    * `dodge` displays the elements side by side
* instead of the string functions can be used, e.g.
    * `position_stack()`
    * `position_jitter()`
    * advantages: control over the parameters, autocompletion
