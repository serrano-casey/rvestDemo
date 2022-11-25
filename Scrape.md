Scrape
================

``` r
library(dplyr)
```

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

``` r
library(rvest)
```

# Scraping directly from a table

``` r
wiki = read_html("https://en.wikipedia.org/wiki/List_of_Academy_Award-winning_films")
print(wiki)
```

    ## {html_document}
    ## <html class="client-nojs" lang="en" dir="ltr">
    ## [1] <head>\n<meta http-equiv="Content-Type" content="text/html; charset=UTF-8 ...
    ## [2] <body class="skin-vector-legacy mediawiki ltr sitedir-ltr mw-hide-empty-e ...

``` r
movies <- wiki %>%
  html_elements("tbody") %>%
  html_table()
```
