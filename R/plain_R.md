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

## reproducible examples (for stackoverflow)

* use package `reprex`
    * [https://github.com/tidyverse/reprex](reprex)
