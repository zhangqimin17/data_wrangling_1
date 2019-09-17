Data Import
================
Qimin Zhang
9/17/2019

# Read csv files

``` r
library(tidyverse)
```

## Load the litters data

``` r
#Not to use read.csv!
litters_data = read_csv(file = "./data_import_examples//FAS_litters.csv")
#Reform the variable names
litters_data = janitor::clean_names(litters_data)
```

## Load the pups data

``` r
pups_data = read_csv(file = "./data_import_examples//FAS_pups.csv")
pups_data = janitor::clean_names(pups_data)
```

## Play with column parsing: define the type of viariables

``` r
litters_data = read_csv(file = "./data_import_examples//FAS_litters.csv",
  col_types = cols(
    Group = col_character(),
    `Litter Number` = col_character(),
    `GD0 weight` = col_double(),
    `GD18 weight` = col_double(),
    `GD of Birth` = col_integer(),
    `Pups born alive` = col_integer(),
    `Pups dead @ birth` = col_integer(),
    `Pups survive` = col_integer()
  )
)
tail(litters_data)
```

    ## # A tibble: 6 x 8
    ##   Group `Litter Number` `GD0 weight` `GD18 weight` `GD of Birth`
    ##   <chr> <chr>                  <dbl>         <dbl>         <int>
    ## 1 Low8  #79                     25.4          43.8            19
    ## 2 Low8  #100                    20            39.2            20
    ## 3 Low8  #4/84                   21.8          35.2            20
    ## 4 Low8  #108                    25.6          47.5            20
    ## 5 Low8  #99                     23.5          39              20
    ## 6 Low8  #110                    25.5          42.7            20
    ## # … with 3 more variables: `Pups born alive` <int>, `Pups dead @
    ## #   birth` <int>, `Pups survive` <int>

# Read excel files

``` r
library(readxl)
mlb11_data = read_excel("data_import_examples//mlb11.xlsx", n_max = 20)
head(mlb11_data, 5)
```

    ## # A tibble: 5 x 12
    ##   team   runs at_bats  hits homeruns bat_avg strikeouts stolen_bases  wins
    ##   <chr> <dbl>   <dbl> <dbl>    <dbl>   <dbl>      <dbl>        <dbl> <dbl>
    ## 1 Texa…   855    5659  1599      210   0.283        930          143    96
    ## 2 Bost…   875    5710  1600      203   0.28        1108          102    90
    ## 3 Detr…   787    5563  1540      169   0.277       1143           49    95
    ## 4 Kans…   730    5672  1560      129   0.275       1006          153    71
    ## 5 St. …   762    5532  1513      162   0.273        978           57    90
    ## # … with 3 more variables: new_onbase <dbl>, new_slug <dbl>, new_obs <dbl>

\#Read SAS files

``` r
library(haven)
pulse_data = read_sas("./data_import_examples//public_pulse_data.sas7bdat")
head(pulse_data, 5)
```

    ## # A tibble: 5 x 7
    ##      ID   age Sex   BDIScore_BL BDIScore_01m BDIScore_06m BDIScore_12m
    ##   <dbl> <dbl> <chr>       <dbl>        <dbl>        <dbl>        <dbl>
    ## 1 10003  48.0 male            7            1            2            0
    ## 2 10015  72.5 male            6           NA           NA           NA
    ## 3 10022  58.5 male           14            3            8           NA
    ## 4 10026  72.7 male           20            6           18           16
    ## 5 10035  60.4 male            4            0            1            2
