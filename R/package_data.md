# Package Data

## raw data
To include raw data (the dataframe) in a package:

1. `library(usethis); use_data_raw()`
2. `x <- <generate data>`
3. `use_data(x, compress = ...)` 
4. document: <data>.R 
    * @title
    * @description
    * @format 
        \describe{
          \item{x}{...}
          \item{y}{...}
        "name of datasource"}

# files

include a *.csv*-file like so:

1. copy to */inst/extdata*
2. get: `system.file('folder', 'filename', package = '<pkg>')`

useful for unit testing.
