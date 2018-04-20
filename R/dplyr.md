# dplyr

Is a library for databases and datatables.
cheatsheet: [https://www.rstudio.com/wp-content/uploads/2015/02/data-wrangling-cheatsheet.pdf]()

Use `tbl_df()` when working with a data-frame.
It is easy to work with *discards rownames* and *prints nicely*.

There are different base functions:

## filter

Shows rows matching some critera.
**Tip:** transform into a `mutate()` for viewing the result of checks.

```R
flights[flights$month==1 & flights$day==30, ]
# -->
filter( flights, month==1, day==30)
# logical OR
filter( flights, month==1 || day==30)
# lists
filter( flights, month %in% c(1:3) || day==30)
# xor
filter( flights, xor(month==1, day==30))
```

filter a range:

```R
flights %>% filter(year >= 2000, year <= 2003)
# -->
flights %>% filter(between(year, 2013, 2014))
```

deal with `NA`:

```R
flights %>% filter(!is.na(dep_time))
```

### slice

filters rows by index range (== more flexible `head()` and `tail()`)

```R
# get 3 rows from every group
flights %>%
  group_by(month, day) %>%
  slice(1:3)
# ... 3 random rows
  sample_n(3)
# the 3 rows with max dep_delay
  top_n(3, dep_delay)
```

### unique/distinct

removes duplicate rows  

```R
flights %>%
  select(year) %>%
  unique()
# ... more performant
  distinct
```

## select

Selects columns by name. Renaming possible.

```R
flights[, c("Time", "Month", "Day"]
# -->
select(name = flights, clock = Time, Month, Day)
# ranges
  Time:Day  
# text search:
  contains()
  starts_with()
  ends_with()
  matches(<regex>)
```

unselect columns with **-**, and also combine with the **:** and `contains()` and stuff

```R
flights %>% select(-day, -month)
```

rename in select and keeping all the other cols with `rename()`

```R
flights %>% select(tail = tailnum)
flights %>% rename(tail = tailnum)
```

select from a list

```R
cols <- c("day", "month", "year")
flights %>% select(one_of(cols))
```

## arrange  

order the table by column values.
*!Beware: very costly, because data has to be copied for that!*

```R
flights[order(flights$Delay), c("UniqueCarrier", "Delay")]
# -->
flights %>%
  select(UniqueCarrier, Delay) %>%
  arrange(desc(Delay)) #default: ascending
```

## mutate

adds new columns.

```R
flights$Speed <- flights$Distance/flights$air_time*60
# -->
flights %>%
  mutate(Speed = Distance/air_time*60)
```

`transmute` selects only the new row  

```R
flights %>%
  transmute(speed = distance/air_time*60)
```

## summarize

groups data together and aggregates with a function.
*Very complicated in R. Use: tapply() or aggregate()*

Grouping does not copy the data. 
Instead an index is build (uses a little more memory).

```R
flights %>%
  group_by( Destination ) %>%
  summarise( arrdel = mean(ArrivalDelay) )
```

`mean()` logical vectors to get the fraction of `TRUE` values.

`summarise_each` summarises for multiple columns.

```R
flights %>%
  group_by( UniqueCarrier ) %>%
  summarise_each( funs(mean), Cancelled, Diverted )
# powerful selection
  funs(min, max(., na.rm=TRUE)), matches("Delay")
# uses different funcs (appends _min, _max to result column)
# and performs them on all columns with delay in the name
```

### summarize functions 

`n()` counts the rows for a group 

```R
flights %>%
  group_by( UniqueCarrier ) %>%
  summarise( count = n() )
# OR  
  tally(sort = TRUE) # colname will be 'n'
# count unique values 
  n_distinct()
```

create a table with column for every value (think: factors)

```R
flights %>%
  group_by( Destination ) %>% # for every destination
  select( Cancelled ) %>% # get the Cancelled column
  table  # display every unique value and its count
```

counting can be even easier than `tally()`.

```R
flights %>%
  count(month, sort=TRUE)
# ... or use it to sum
  count(month, wt=distance)
```

`summarize`  and other reduce-function always remove a grouping level.
So if `arrange()` is called, `ungroup` could be necessary.
(When a `group_by()` with multiple categories is involved.)

### custom summarise functions with DO  

Is slower, but can run arbitrary code.
Uses `.` to represent current Group.

```R
flights %>%
  group_by(dep_delay) %>%
  do(
    mod = lm( ., ... )
    # calculate a linear model for each day 
    # has to be named, because it does not return DF
  )
  # without naming
  do( head(., 2) )
```

### group calculations

count the group members and return a **vector**.

```R
flights %>%
  group_by(month) %>%
  group_size
# count number of groups
  n_groups
```

### grouped filtering/selection 

The grouping of a DF is consistent, event if the `print()` does not show it.
It is appended as an attribute to the DF.
I.e. when you store a grouped DF and after that `filter()` it, you can use summarisation functions.

```R
planes  <- flights %>%
  group_by(plane) 

# this performs mean and sd per group 
# here: per plane
planes %>%
  mutate( z_delay = (arr_delay - mean(arr_delay)) / sd(arr_delay) ) 
```


## window functions 

take n values and returns n values (like: `rank()`)
But do not operate row by row (need more input).

Types:
* ranking and ordering
* offsets
* accumulate aggregates

```R
flights %>%
  group_by() %>%
  select() %>%
  filter(min_rank(desc(DepDelay))<=2) %>%
  #     | ranks the delays      |
  #| takes only the biggest 2 values|
  arrange()
# -->
  top_n(2)
```

different dealing with ties:
* `dense_rank()` is like `min_rank()` only it does not skip numbers after ties.
* `row_number()` gives an ordering, randomly deciding ties.

lag uses the value from the last row.
In contrast to `diff()` it takes **n** arguments and produces **n** results (first is `NA`).
Arguments: 
* `default=` sets the value for the fist row (e.g. `0.0`).
* `order_by=` sets an ordering column (to avoid `arrange`)

```R
flights %>%
  group_by() %>%
  tally() %>%
  mutate( change = n -          lag(n)       )
#                     | takes the last value |
# next value
  mutate( change = lead(n) - n )
```

`sample_n` gives n randomly selected rows 

`sample_frac(replace=TRUE)` gives a fraction of the rows randomly

## joins

automatically use similar named cols.
multiple variants available:
* inner_join
* full_join (not defined values --> NA)
* right_join
* left_join
* semi_join (only shows cols of 1st, but removes rows that don't match 2nd)
* anti_join (opposite of `semi_join` in terms of rows)

match different named cols:

```R
a %>% inner_join(b, by=c("color", "colour"))
```

# Databases

init: `my_db <- src_sqlite("...")`, use: `create=TRUE` to create a new one.
Put data into the database: `copy_to(..., indexes= list(...), temporary=FALSE)`

get table: (just sets up a connection)

```R
flights_tbl <- tbl(my_db, "flights")
                         |tablename|
```

execute sql: `tbl(my_db, "statement")`
get the SQL code: `%>% explain`


# additional Tips:

## deal with rownames

`add_rownames` removes the rownames and creates an own column for it.
*This is considered a good data modeling practice. 
And DFs created with `tbl_df()` don't show them either.*

```R
# before: models are stored as rownames
mt_cars %>%
  add_rownames("model")
# after: these are located in a col named: model
```

## displaying data  

`str(DF)` --> `glimpse(DF)` for nicer formatting

printing a number of rows:

```R
flights %>%
  print(n = 15)
# ... with all rows
  print(n = Inf)
# ... with all columns
  print(width = Inf)
```

use a viewer for data: (only RStudio, standard viewer is garbage)

```R
flights %>%
  View()
```

change dplyr default printing:

```R
# change view width and number of rows displayed
options( dplyr.width = Inf, dplyr.print_min=6 )

# default values
options( dplyr.width = NULL, dplyr.print_min=10 )
```

## create datastructures

Create DFs with `data_frame()` instead of `data.frame`.

```R
data_frame(
  a=1:6,
  b=2*a, # this works!
  c="string" # is not build into a factor
  "d+e" = 1 # name is not changed
```

Read in `.csv` files with:

```R
name <- tbl_df(read.csv("<file>"))
