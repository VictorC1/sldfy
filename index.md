---
title       : Week 4 assigment
subtitle    : 
author      : 
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Week 4

Reproducible Pitch Presentation
Poisson prediction model and analysing unknown Markets for deeper analysis.

 ○ Dataset:: package(ISLR) Smarket
    ○Variables = Lag (Percentage return for (n) previous days. In this data goes up to 5
    ○Volume = Volume of shares traded (in billions)
    ○Direction = Indicates if closing volume was that given day
    
Hypothesis:
Portfolio to benchmark with the unknown Index.

"What the years between 2001 - 2005
can present with it's volume and previous Percentage return?"
 ○ Would be wise to predict what are the odds to high volatility days?
 ○ Looking at the odds the risk can be hedged and profitable?
 
 
---




##Statistical Inference:
Poisson model choosed from other prediction models for the direct calculation of what to expect for selected days. Allowing us to have a glimpse of what expect from the market with certain environments. Althought poisson be a discrete prediction. With more detailed data a more precise prediction can be conducted.


---

##Analysis
Probability of holding stock position with %return of previous day higher than 2%

```r
library(ISLR)
```

```
## Warning: package 'ISLR' was built under R version 3.5.3
```

```r
z <- ppois(Smarket$Volume > 500, Smarket$Lag1 >2, lower.tail = FALSE)
z <- ppois(Smarket$Volume > 1000, Smarket$Lag1 >2, lower.tail = FALSE)
z <- ppois(Smarket$Volume < 0.2, Smarket$Lag1 > 2, lower.tail = FALSE)
z <- ppois(Smarket$Volume < 0.7, Smarket$Lag1 > 2, lower.tail = FALSE)
```
Only with setting up the size dealt with the next day we can predict what outcome can be expected.
Volume lower than 0.7 shown smaller probability with having a previous day with high volatility.

---
linear Model prediction

```
## 
## Call:
## lm(formula = Volume ~ Lag1, data = Smarket)
## 
## Residuals:
##      Min       1Q   Median       3Q      Max 
## -1.12438 -0.21477 -0.05378  0.15966  1.66346 
## 
## Coefficients:
##             Estimate Std. Error t value Pr(>|t|)    
## (Intercept)  1.47826    0.01019 145.097   <2e-16 ***
## Lag1         0.01297    0.00897   1.446    0.148    
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 0.3602 on 1248 degrees of freedom
## Multiple R-squared:  0.001674,	Adjusted R-squared:  0.0008737 
## F-statistic: 2.092 on 1 and 1248 DF,  p-value: 0.1483
```

---

Shiny App + Prediction Models

The layout and interactive way this shiny app presents it's to offer a faster method to analyze possible hypothesis to be studied with deeper detail





