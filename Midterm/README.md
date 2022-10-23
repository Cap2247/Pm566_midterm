Midterm
================
Camille Parchment
2022-10-23

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

## Introduction

#### During the COVID-19 pandemic, mental health services were disrupted, causing profound consequences for individuals in need of consistent mental health care. The pandemic exacerbated the need for mental health services which expanded an existing unmet demand. In addition to a shortage of mental health professionals, mental health providers needed to adjust service delivery to comply with safety protocols, which further inhibited access to care for some individuals. Further, at the onset of the pandemic, several state and local governments issued stay-at-home orders to reduce viral spread. These orders resulted in increased emotional distress e.g., anxiety, depression, and loss of employment. Employers are the leading providers of health insurance in the United States, suggesting that newly unemployed individuals may have lost access to secure healthcare coverage. The growing demand for mental health services, possible reduction in coverage, and changing delivery systems, may have decreased access to necessary mental health services during the COVID-19 pandemic. Therefore, the primary aim of this study is to establish insurance-related patterns of mental healthcare utilization. Specifically, did the absence of health insurance decrease access to mental health services during the COVID-19 pandemic?

## Methods

### Database

#### The Household Pulse Survey (HPS) is a self-report online survey which measures in real time the social and economic impacts of the COVID-19 pandemic. In this study we analyzed HPS data from week 18, October 28, 2021 – November 9, 2021.

### Sample

#### Our study sample were all individuals who needed mental health services and either received services or did not between October 28, 2021, and November 9, 2021. Mental health services were Our insurance variable was coded for both private and public insurance, public insurance only, private insurance only, or none. Region was coded for Midwest, Northeast, South, and West depending on the census region. I subset the data from the larger data frame to include only the variables relevant to the study question (Identification number, gender, region, public health insurance, private health insurance, marital status, mental health service received, mental health service not received). We recoded the missing (-99) and non-answered (-88, 3) responses as NA in all variables.

    ## 
    ##                   both           No Insurance Private insurance only 
    ##                   7773                   2709                  22219 
    ##  Public insurance only                   <NA> 
    ##                   5559                      0

    ##                        
    ##                              both No Insurance Private insurance only
    ##   Services Not Recieved  1.615264     1.484579               6.596968
    ##   Services Recieved     18.700993     5.595923              51.476738
    ##                        
    ##                         Public insurance only
    ##   Services Not Recieved              2.017773
    ##   Services Recieved                 12.511762

    ##                        
    ##                          both No Insurance Private insurance only
    ##   Services Not Recieved   618          568                   2524
    ##   Services Recieved      7155         2141                  19695
    ##                        
    ##                         Public insurance only
    ##   Services Not Recieved                   772
    ##   Services Recieved                      4787

![](README_files/figure-gfm/unnamed-chunk-18-1.png)<!-- -->

![](README_files/figure-gfm/unnamed-chunk-19-1.png)<!-- -->
![](README_files/figure-gfm/unnamed-chunk-20-1.png)<!-- -->

![](README_files/figure-gfm/unnamed-chunk-24-1.png)<!-- -->

## Conclusion

#### The results indicate that 6% (n= 2524) of individuals with private insurance who needed mental health services did not receive services. Conversely, 2% (n= 772) of people with public insurance who needed mental health services did not receive services. Our findings suggest that although mental health services were delayed during the pandemic a higher percentage of people who needed mental health service but did not receive it consisted of people with private insurance. Further research is needed to identify service and diagnosis-specific patterns in mental health care.
