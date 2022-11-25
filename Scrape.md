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
wiki <- read_html("https://en.wikipedia.org/wiki/List_of_Academy_Award-winning_films")
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
movies <- movies[[1]]
```

\#Scraping from a non-table site

``` r
link <- read_html("https://www.thecrazytourist.com/15-best-things-to-do-in-athens-ga/")
print(link)
```

    ## {html_document}
    ## <html lang="en-US">
    ## [1] <head>\n<meta http-equiv="Content-Type" content="text/html; charset=UTF-8 ...
    ## [2] <body class="post-template-default single single-post postid-95201 single ...

``` r
ath2do <- link %>%
  html_elements(".entry-content h2") 

print(ath2do)
```

    ## {xml_nodeset (15)}
    ##  [1] <h2>1. Georgia Museum of Art</h2>
    ##  [2] <h2>2. State Botanical Garden of Georgia</h2>
    ##  [3] <h2>3. Downtown Athens</h2>
    ##  [4] <h2>4. The Tree That Owns Itself</h2>
    ##  [5] <h2>5. Terrapin Brewery</h2>
    ##  [6] <h2>6. The Athens Double-Barrelled Cannon</h2>
    ##  [7] <h2>7. Sandy Creek Nature Center</h2>
    ##  [8] <h2>8. American Football</h2>
    ##  [9] <h2>9. Amicalola Falls State Park</h2>
    ## [10] <h2>10. Live Music</h2>
    ## [11] <h2>11. Helen</h2>
    ## [12] <h2>12. Music History Walking Tours</h2>
    ## [13] <h2>13. Dahlonega Gold Museum</h2>
    ## [14] <h2>14. Wolf Mountain Vineyards</h2>
    ## [15] <h2>15. Oconee Hill Cemetery</h2>
