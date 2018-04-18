# R Tipps

- keine Ausgaben von Befehlen mit: `suppressMessages()`
  * geil bei: `library()`

## chaining/pipe

Operator `%>%` connects many operators. Read as: *then*.

* passes left hand stuff as first argument (or where the `.` is)
* in chaining, you don't need `()`, when there are no arguments

```R
filter( select( flights, UniqueCarrier, DepDelay), DepDelay>60)
# -->
flights %>%
  filter( DepDelay>60 ) %>%
  select( UniqueCarrier, DepDelay )
```

