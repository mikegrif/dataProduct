---
title       : Car Mileage Presentation
subtitle    : Analysis of ggplot's mpg data
author      : mikeg
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Introduction

This presentation analyzes the **mpg** dataset in *ggplot2's* package to determine cars with the best and worst average mile per gallon. The average mile per gallon for each car is determined by taking the mean of its highway and city mile per gallon.

--- .class #id 



## Best Mileage

```r
require(ggplot2)

# select key columns from dataset
df <- subset(mpg, select = c(manufacturer,model,year,class))
df$mpg <- (mpg$hwy + mpg$cty)/2

# sort data in descending order based on mpg
df <- with(df, df[order(mpg, decreasing=TRUE),])
# display top 5 cars with best miles per gallon
head(df, n=5)
```

```
##     manufacturer      model year      class  mpg
## 222   volkswagen new beetle 1999 subcompact 39.5
## 213   volkswagen      jetta 1999    compact 38.5
## 223   volkswagen new beetle 1999 subcompact 35.0
## 197       toyota    corolla 2008    compact 32.5
## 100        honda      civic 1999 subcompact 30.5
```


---

## Worst Mileage

```r
# display bottom 5 cars with worst miles per gallon
tail(df, n=5)
```

```
##     manufacturer               model year  class  mpg
## 55         dodge   dakota pickup 4wd 2008 pickup 10.5
## 60         dodge         durango 4wd 2008    suv 10.5
## 66         dodge ram 1500 pickup 4wd 2008 pickup 10.5
## 70         dodge ram 1500 pickup 4wd 2008 pickup 10.5
## 127         jeep  grand cherokee 4wd 2008    suv 10.5
```

---

## Summary
1. Volkswagen makes cars with highest average miles per gallon (mpg)
2. Dodge and Jeep make cars with lowest average miles per gallon (mpg)
3. On average, compact and subcompact cars have better mpg than trucks and pickups

