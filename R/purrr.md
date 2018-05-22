# purrr

implements a map reduce scheme, that can be used to perform a `apply`-like operation on data and then combine data to one block.

**example:**

```R
parameters <- info_files %>%
  map(read_params_file) %>%
  reduce(rbind)
```

This reads in multiple files and combines the dataframes via `rbind`.

**optimization:** If `map`, `reduce` is too slow try using `map_df` instead. 
