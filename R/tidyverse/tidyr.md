# tidyr 

## gather

Takes a **key** and the corresponding **values** and  
puts them in column form.

```R
# take data and look at it
library(EDAWR)
cases
#   country  2011  2012  2013
# 1      FR  7000  6900  7000
# 2      DE  5800  6000  6200
# 3      US 15000 14000 13000
```

**Problem:** colnames is used for values (variable should be "year").
Multiple observations are *gathered* in one row.
Clean this up with:

```R
library(tidyr)
cases %>% gather("year",              "n",                    2:4)
#               | name of key column | name of value column | column range to use |
```

## spread

Generates multiple columns from 2 columns (key : value).
The factors of the key-column are transformed into variables.

```R
# take data and look at it
library(EDAWR)
pollution
#       city  size amount
# 1 New York large     23
# 2 New York small     14
# 3   London large     22
# 4   London small     16
# 5  Beijing large    121
# 6  Beijing small     56
```

**Problem:** the size column describes on how to interpret amount.
One observation is *spread* over 2 columns.
Clean this up with:

```R
library(tidyr)
pollution %>% spread(size, amount)
#                   | key | values |
#       city large small
# 1  Beijing   121    56
# 2   London    22    16
# 3 New York    23    14
```

## separate 

Takes a single column and separates the values over multiple rows.

```R
# take data and look at it
library(EDAWR)
storms
# # tibble [6 × 4]
#   storm    wind pressure date      
#   <chr>   <int>    <int> <date>    
# 1 Alberto   110     1007 2000-08-03
# 2 Alex       45     1009 1998-07-27
# 3 Allison    65     1005 1995-06-03
# 4 Ana        40     1013 1997-06-30
# 5 Arlene     50     1010 1999-06-11
# 6 Arthur     45     1010 1996-06-17
```

**Problem:** date contains 3 informations: year, month, day.
Clean this up with:

```R
library(tidyr)
storms %>% separate(date, c("year", "month", "day"), sep="-")
                   | column| new names            | separator |
# # tibble [6 × 6]
#   storm    wind pressure year  month day  
#   <chr>   <int>    <int> <chr> <chr> <chr>
# 1 Alberto   110     1007 2000  08    03   
# 2 Alex       45     1009 1998  07    27   
# 3 Allison    65     1005 1995  06    03   
# 4 Ana        40     1013 1997  06    30   
# 5 Arlene     50     1010 1999  06    11   
# 6 Arthur     45     1010 1996  06    17   
```

## unite

opposite of separate.

```R
# reverse the above separation:
storms-separated %>%
  unite("date",   year, month, day, sep="-")
#      | colname | cols to combine | separator |
```

## unnest

combines a nested dataframe into a flat one
