# R Tipps

- keine Ausgaben von Befehlen mit: `suppressMessages()`
  * geil bei: `library()`
* geladene Datensätze: `data()`
    * `package="ggplot2"` zeigt nur die eines packages an

## chaining/pipe

Available in package: `magrittr`.
Operator `%>%` connects many operators. Read as: *then*.

* passes left hand stuff as first argument (or where the `.` is)
* in chaining, you don't need `()`, when there are no arguments

```R
library(magrittr)
filter( select( flights, UniqueCarrier, DepDelay), DepDelay>60)
# -->
flights %>%
  filter( DepDelay>60 ) %>%
  select( UniqueCarrier, DepDelay )
```

Assignments van be made with `%<>%` as the first operator in a chain.
And `%$%` can be used for functions with **no data argument**.

```R
iris %>%
  subset(Sepal.Length > mean(Sepal.Length)) %$%
  cor(Sepal.Length, Sepal.Width)
```

Create a multiplication table with: `%o%`

* use: `<range> %o% <range>`
* e.g.: 

```
1:10 %o% 1:5

#       [,1] [,2] [,3] [,4] [,5]
#  [1,]    1    2    3    4    5
#  [2,]    2    4    6    8   10
#  [3,]    3    6    9   12   15
#  [4,]    4    8   12   16   20
#  [5,]    5   10   15   20   25
#  [6,]    6   12   18   24   30
#  [7,]    7   14   21   28   35
#  [8,]    8   16   24   32   40
#  [9,]    9   18   27   36   45
# [10,]   10   20   30   40   50
```

## reproducible examples (for stackoverflow)

* use package `reprex`
    * [https://github.com/tidyverse/reprex](reprex)

## Date handling

calculate from seconds to date type:

```R
# time in seconds
as.POSIXct(3600, origin = '2018-01-01', tz='GMT')
# time in days
as.Date(7, origin = '2018-01-01')
```

print a date: (format string, see: ~format)

```R
format(date_var, '%H:%M')
```
```
