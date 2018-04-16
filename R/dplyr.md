# dplyr
cheatsheet: [https://www.rstudio.com/wp-content/uploads/2015/02/data-wrangling-cheatsheet.pdf]()

## select

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

## filter

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

## slice

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

## unique/distinct

removes duplicate rows  

```R
flights %>%
  select(year) %>%
  unique()
# ... more performant
  distinct
```

## mutate

`transmute` selects only the new row  

```R
flights %>%
  transmute(speed = distance/air_time*60)
```

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

## summarize

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

## group calculations

count the group members and return a **vector**.

```R
flights %>%
  group_by(month) %>%
  group_size
# count number of groups
  n_groups
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

## displaying data  

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
