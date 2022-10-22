Midterm
================
Camille Parchment
2022-10-21

``` r
library(data.table)
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.2 ──
    ## ✔ ggplot2 3.3.6     ✔ purrr   0.3.4
    ## ✔ tibble  3.1.8     ✔ dplyr   1.0.9
    ## ✔ tidyr   1.2.0     ✔ stringr 1.4.1
    ## ✔ readr   2.1.2     ✔ forcats 0.5.2
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::between()   masks data.table::between()
    ## ✖ dplyr::filter()    masks stats::filter()
    ## ✖ dplyr::first()     masks data.table::first()
    ## ✖ dplyr::lag()       masks stats::lag()
    ## ✖ dplyr::last()      masks data.table::last()
    ## ✖ purrr::transpose() masks data.table::transpose()

``` r
pulse18 <- fread("pulse2020_puf_18.csv")
```

``` r
MHdf <- subset(pulse18, select = c(SCRAM, TBIRTH_YEAR, MS, MH_SVCS, MH_NOTGET, EGENDER, ANYWORK, HLTHINS1, HLTHINS2, HLTHINS3, HLTHINS4, HLTHINS5, HLTHINS6, HLTHINS7, HLTHINS8))
```

``` r
pulse18[pulse18$MH_NOTGET == -88] <- NA
pulse18[pulse18$MH_NOTGET == -99] <- NA
pulse18[pulse18$MH_SVCS == -88] <- NA
pulse18[pulse18$MH_SVCS == -99] <- NA
pulse18[pulse18$MS == -88] <- NA
pulse18[pulse18$MS == -99] <- NA
pulse18[pulse18$ANYWORK == -88] <- NA
pulse18[pulse18$ANYWORK == -99] <- NA
pulse18[pulse18$HLTHINS1 == -88] <- NA
pulse18[pulse18$HLTHINS1 == -99] <- NA
pulse18[pulse18$HLTHINS2 == -88] <- NA
pulse18[pulse18$HLTHINS2 == -99] <- NA
pulse18[pulse18$HLTHINS3 == -88] <- NA
pulse18[pulse18$HLTHINS3 == -99] <- NA
pulse18[pulse18$HLTHINS4 == -88] <- NA
pulse18[pulse18$HLTHINS4 == -99] <- NA
pulse18[pulse18$HLTHINS5 == -88] <- NA
pulse18[pulse18$HLTHINS5 == -99] <- NA
pulse18[pulse18$HLTHINS6 == -88] <- NA
pulse18[pulse18$HLTHINS6 == -99] <- NA
pulse18[pulse18$HLTHINS7 == -88] <- NA
pulse18[pulse18$HLTHINS7 == -99] <- NA
pulse18[pulse18$HLTHINS8 == -88] <- NA
pulse18[pulse18$HLTHINS8 == -99] <- NA
```

``` r
summary(pulse18$HLTHINS1)
```

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max.    NA's 
    ##   1.000   1.000   1.000   1.338   2.000   2.000   20469

``` r
MHdf_2 <- subset(pulse18, select = c(SCRAM, REGION, PUBHLTH, PRIVHLTH, EST_ST, TBIRTH_YEAR, MS, MH_SVCS, MH_NOTGET, EGENDER, ANYWORK, HLTHINS1, HLTHINS2, HLTHINS3, HLTHINS4, HLTHINS5, HLTHINS6, HLTHINS7, HLTHINS8 ))
```

``` r
pulse18[pulse18$MH_NOTGET == -88] <- NA
pulse18[pulse18$MH_NOTGET == -99] <- NA
pulse18[pulse18$MH_SVCS == -88] <- NA
pulse18[pulse18$MH_SVCS == -99] <- NA
pulse18[pulse18$MS == -88] <- NA
pulse18[pulse18$MS == -99] <- NA
pulse18[pulse18$ANYWORK == -88] <- NA
pulse18[pulse18$ANYWORK == -99] <- NA
pulse18[pulse18$HLTHINS1 == -88] <- NA
pulse18[pulse18$HLTHINS1 == -99] <- NA
pulse18[pulse18$HLTHINS2 == -88] <- NA
pulse18[pulse18$HLTHINS2 == -99] <- NA
pulse18[pulse18$HLTHINS3 == -88] <- NA
pulse18[pulse18$HLTHINS3 == -99] <- NA
pulse18[pulse18$HLTHINS4 == -88] <- NA
pulse18[pulse18$HLTHINS4 == -99] <- NA
pulse18[pulse18$HLTHINS5 == -88] <- NA
pulse18[pulse18$HLTHINS5 == -99] <- NA
pulse18[pulse18$HLTHINS6 == -88] <- NA
pulse18[pulse18$HLTHINS6 == -99] <- NA
pulse18[pulse18$HLTHINS7 == -88] <- NA
pulse18[pulse18$HLTHINS7 == -99] <- NA
pulse18[pulse18$HLTHINS8 == -88] <- NA
pulse18[pulse18$HLTHINS8 == -99] <- NA
```

``` r
ins1_empl <- ifelse(MHdf$HLTHINS1 == "1", 1,0)
ins2_markt <- ifelse(MHdf$HLTHINS2 == "1", 1,0)
ins3_medicare <- ifelse(MHdf$HLTHINS3 == "1", 1,0)
ins4_medicaid <- ifelse(MHdf$HLTHINS4 == "1", 1,0)
ins5_tricare <- ifelse(MHdf$HLTHINS5 == "1", 1,0)
ins6_va <- ifelse(MHdf$HLTHINS6 == "1", 1,0)
ins7_indian <- ifelse(MHdf$HLTHINS7 == "1", 1,0)
ins8_other <- ifelse(MHdf$HLTHINS8 == "1", 1,0)
```

``` r
MHdf_2[MHdf_2$PUBHLTH == 3] <- NA
MHdf_2[MHdf_2$PRIVHLTH == 3] <- NA
```

``` r
pubins <- ifelse(MHdf_2$PUBHLTH == "1", "Has public insurance", "No public insurance")
privins <- ifelse(MHdf_2$PRIVHLTH == "1", "Has Private insuracne","No private insurance")
```

``` r
library(ggplot2)
```

``` r
region_2 <- ifelse(MHdf_2$REGION == "1", "Northeast",
            ifelse(MHdf_2$REGION == "2", "South",
            ifelse(MHdf_2$REGION == "3", "Midwest", "West")))
```

``` r
table(region_2)
```

    ## region_2
    ##   Midwest Northeast     South      West 
    ##      8025      5566     11505     13164

``` r
head(region_2)
```

    ## [1] "South" NA      "South" "South" "South" "South"

``` r
MH_sum <- sum(MHdf_2$MH_NOTGET, na.rm = TRUE)
```

``` r
table(ins1_empl
    )
```

    ## ins1_empl
    ##     0     1 
    ## 26671 32058

``` r
prop.table(table(ins1_empl))
```

    ## ins1_empl
    ##         0         1 
    ## 0.4541368 0.5458632

``` r
table(ins2_markt)/length(ins2_markt)
```

    ## ins2_markt
    ##         0         1 
    ## 0.8091233 0.1908767

``` r
sd(ins1_empl)
```

    ## [1] 0.4978964

``` r
ggplot(MHdf_2, aes(x= region_2, fill = privins)) + geom_bar(position = position_dodge())
```

![](README_files/figure-gfm/unnamed-chunk-21-1.png)<!-- -->

``` r
ggplot(MHdf_2, aes(x= region_2, fill = pubins, na.rm= TRUE)) + geom_bar(position = position_dodge())
```

![](README_files/figure-gfm/unnamed-chunk-21-2.png)<!-- -->

``` r
Mh_ntgt_2 <- ifelse(MHdf_2$MH_NOTGET == "1", "Services Not Recieved", "Services Recieved")
Mh_svs_2 <- ifelse(MHdf_2$PUBHLTH == "1", "Recieved services", "No Services")
```

``` r
ggplot(MHdf_2, aes(x= region_2, fill = Mh_ntgt_2)) + geom_bar () 
```

![](README_files/figure-gfm/unnamed-chunk-23-1.png)<!-- -->

``` r
ggplot(MHdf_2, aes(x= Mh_ntgt_2, fill = privins)) + geom_bar(position = position_dodge())
```

![](README_files/figure-gfm/unnamed-chunk-24-1.png)<!-- -->

``` r
table(region_2, privins)
```

    ##            privins
    ## region_2    Has Private insuracne No private insurance
    ##   Midwest                    6416                 1609
    ##   Northeast                  4447                 1119
    ##   South                      8941                 2564
    ##   West                      10188                 2976

``` r
ggplot(MHdf_2, aes(x= privins, fill = Mh_ntgt_2, na.rm= TRUE )) + geom_bar () 
```

![](README_files/figure-gfm/unnamed-chunk-26-1.png)<!-- -->

``` r
ggplot(MHdf_2, aes(x= pubins, fill = Mh_ntgt_2)) + geom_bar () 
```

![](README_files/figure-gfm/unnamed-chunk-27-1.png)<!-- -->

``` r
insurance <- ifelse(MHdf_2$PUBHLTH == "1" & MHdf_2$PRIVHLTH == "1", "both", 
                    ifelse(MHdf_2$PUBHLTH == "1" & MHdf_2$PRIVHLTH == "2", "Public insurance only", 
                    ifelse(MHdf_2$PUBHLTH == "2" & MHdf_2$PRIVHLTH == "1", "Private insurance only", 
                    ifelse(MHdf_2$PUBHLTH == "2" & MHdf_2$PRIVHLTH == "2", "No Insurance", NA))))
                table(insurance, useNA = "always")
```

    ## insurance
    ##                   both           No Insurance Private insurance only 
    ##                   7773                   2709                  22219 
    ##  Public insurance only                   <NA> 
    ##                   5559                  20469

``` r
ggplot(MHdf_2, aes(x= Mh_ntgt_2, fill = insurance)) + geom_bar(position = position_dodge()) 
```

![](README_files/figure-gfm/unnamed-chunk-29-1.png)<!-- -->

``` r
library(knitr)
library(kableExtra)
```

    ## 
    ## Attaching package: 'kableExtra'

    ## The following object is masked from 'package:dplyr':
    ## 
    ##     group_rows

``` r
library(tinytex)
```

``` r
install.packages("kableExtra")
```

    ## Warning: package 'kableExtra' is in use and will not be installed

``` r
MHdf_2 <- na.omit(MHdf_2)
```

``` r
remove(public_insurance)
```

    ## Warning in remove(public_insurance): object 'public_insurance' not found
