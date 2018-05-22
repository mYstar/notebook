# Tidying Data  

structuring datasets

## Simple Rules

1. each variable is a column
2. each observation is a row
3. each type of observational unit is a table

## Problems

data tidying: 
* column headers are values (not variables)
* multiple variables in one column  
* variables stored in rows and columns  
* more than one observation per table 
* a single observation in multiple tables

tied to data cleaning:
* outliers
* date parsing
* missing values

## Definitions

* data = collection of **values** (mostly numbers or strings)
* **variable**: all values for an attribute (like temperature)
* **observation**: all measurements in one unit (like experiment)

## groups vs. variables

Make two or more measurements into N variables or use the varname as a grouping variable?

| Person | Treatment a | Treatment b |
| --- | --- | --- |
| Eric  | 10 | 20 |
| Martin  | 16 | 60 |

OR  

| Person | Treatment | result |
| --- | --- | --- |
| Eric  | a | 10 |
| Eric  | b | 20 |
| Martin  | a | 16 |
| Martin  | b | 60 |

Rule:

* variables: when functional relationship is possible ( calculations like: x / y = z)
* grouping: when comparisons between the groups will be made ( mean(x) vs. mean(y) )

## ordering

columns:
* fixed variables (experiment parameters): in front
* measured variables: in back
* related variables should be contiguous

rows:
* if columns are in order 
* just sort by first column (and then second)

## Solutions

### columns are variables 

| religion | \<$10k | $10-20k | $20-30k | $30-40k | $40-50k | $50-75k |
| --- |--- |--- |--- |--- |--- |--- |
| Agnostic |27 |34 |60 |81 |76 |137 |
| Atheist |12 |27 |37 |52 |35 |70 |
| Buddhist |27 |21 |30 |34 |33 |58 |
| Catholic |418 |617 |732 |670 |638 |1116 |
| Don’t know/refused |15 |14 |15 |11 |10 |35 |
| Evangelical Prot |575 |869 |1064 |982 |881 |1486 |
| Hindu |1 |9 |7 |9 |11 |34 |
| Historically Black Prot |228 |244 |236 |238 |197 |223 |
| Jehovah’s Witness |20 |27 |24 |24 |21 |30 |
| Jewish |19  |19  |25  |25  |30  |95 |

Solution:
* melt/stack the data 
* input: list of columns (that are all variables)
* creates: 2 different columns  
    1. column name
    2. value

**more complex:** one column is multiple variables. like this header:

| country | year | m014 | m1524 | m2534 | m3544 | m4554 | m5564 | m65 | mu | f014 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| AD | 2000 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | - | - | - |

Here the sex (`m|f`) and the age group (`1524` --> 15 to 24) is coded.

Solution:
1. melt 
2. split the variables in the header variables

### values are variable names 

There is a column (`element`), that describes for which variable (`tmax`, `tmin`) the next values stand:

| id | date | element | value |
| MX17004| 2010-01-30| tmax| 27.8 |
| MX17004| 2010-01-30| tmin| 14.5 |
| MX17004| 2010-02-02| tmax| 27.3 |
| MX17004| 2010-02-02| tmin| 14.4 |

Solution: Use a `cast` operation to make separate columns for all the different factors of `element`.

### multiple observations in one table  

Manifests itself through duplication of values.

| year | artist | time | track | date |week | rank |
| 2000| 2 Pac| 4:22| Baby Don’t Cry| 2000-02-26| 1| 87 |
| 2000| 2 Pac| 4:22| Baby Don’t Cry| 2000-03-04| 2| 82 |
| 2000| 2 Pac| 4:22| Baby Don’t Cry| 2000-03-11| 3| 72 |
| 2000| 2 Pac| 4:22| Baby Don’t Cry| 2000-03-18| 4| 77 |

Here: the title and ranking data are joined.

Solution: normalization (dividing the data)
For some use cases, the data has to be joined again temporarily.

### one type in multiple tables/files 

Sometimes every observation writes its own file. Then the files have to be combined into one table:

```R
paths <- dir("data", pattern = "\\.csv$", full.names = TRUE)
names(paths) <- basename(paths)
ldply(paths, read.csv, stringsAsFactors = FALSE)
```

Then other tidying can proceed.
*see:* [R/purrr.md](R/purrr.md) for a more dplyr way to do this (map, reduce)
