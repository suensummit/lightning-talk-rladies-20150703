---
title       : Linear Regression and Moneyball
subtitle    : Unit 2 of MITx 15.071x The Analytics Edge
author      : Summit Suen
job         : Taiwan R User Group
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## RLadies Lightning Talk

---

## MITx: 15.071x The Analytics Edge

---

## Linear Regression


```r
wine <- read.csv(file = "wine.csv", header = TRUE)
model1 <- lm(Price ~ AGST + HarvestRain + Age + FrancePop + WinterRain, data = wine)
summary(model1)
```

```
## 
## Call:
## lm(formula = Price ~ AGST + HarvestRain + Age + FrancePop + WinterRain, 
##     data = wine)
## 
## Residuals:
##      Min       1Q   Median       3Q      Max 
## -0.48179 -0.24662 -0.00726  0.22012  0.51987 
## 
## Coefficients:
##               Estimate Std. Error t value Pr(>|t|)    
## (Intercept) -4.504e-01  1.019e+01  -0.044 0.965202    
## AGST         6.012e-01  1.030e-01   5.836 1.27e-05 ***
## HarvestRain -3.958e-03  8.751e-04  -4.523 0.000233 ***
## Age          5.847e-04  7.900e-02   0.007 0.994172    
## FrancePop   -4.953e-05  1.667e-04  -0.297 0.769578    
## WinterRain   1.043e-03  5.310e-04   1.963 0.064416 .  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 0.3019 on 19 degrees of freedom
## Multiple R-squared:  0.8294,	Adjusted R-squared:  0.7845 
## F-statistic: 18.47 on 5 and 19 DF,  p-value: 1.044e-06
```

---

## Linear Regression


```r
model2 <- lm(Price ~ AGST + HarvestRain  + FrancePop + WinterRain, data = wine)
summary(model2)
```

```
## 
## Call:
## lm(formula = Price ~ AGST + HarvestRain + FrancePop + WinterRain, 
##     data = wine)
## 
## Residuals:
##      Min       1Q   Median       3Q      Max 
## -0.48252 -0.24636 -0.00699  0.22089  0.51949 
## 
## Coefficients:
##               Estimate Std. Error t value Pr(>|t|)    
## (Intercept) -3.768e-01  2.180e+00  -0.173 0.864529    
## AGST         6.011e-01  9.898e-02   6.073 6.17e-06 ***
## HarvestRain -3.958e-03  8.518e-04  -4.646 0.000156 ***
## FrancePop   -5.075e-05  1.704e-05  -2.978 0.007434 ** 
## WinterRain   1.042e-03  5.070e-04   2.055 0.053202 .  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 0.2943 on 20 degrees of freedom
## Multiple R-squared:  0.8294,	Adjusted R-squared:  0.7952 
## F-statistic:  24.3 on 4 and 20 DF,  p-value: 1.945e-07
```

---

## Linear Regression


```r
model3 <- lm(Price ~ AGST + HarvestRain  + Age + WinterRain, data = wine)
summary(model3)
```

```
## 
## Call:
## lm(formula = Price ~ AGST + HarvestRain + Age + WinterRain, data = wine)
## 
## Residuals:
##      Min       1Q   Median       3Q      Max 
## -0.45470 -0.24273  0.00752  0.19773  0.53637 
## 
## Coefficients:
##               Estimate Std. Error t value Pr(>|t|)    
## (Intercept) -3.4299802  1.7658975  -1.942 0.066311 .  
## AGST         0.6072093  0.0987022   6.152  5.2e-06 ***
## HarvestRain -0.0039715  0.0008538  -4.652 0.000154 ***
## Age          0.0239308  0.0080969   2.956 0.007819 ** 
## WinterRain   0.0010755  0.0005073   2.120 0.046694 *  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 0.295 on 20 degrees of freedom
## Multiple R-squared:  0.8286,	Adjusted R-squared:  0.7943 
## F-statistic: 24.17 on 4 and 20 DF,  p-value: 2.036e-07
```

---

## Linear Regression


```r
model4 <- lm(Price ~ HarvestRain+ WinterRain, data = wine)
summary(model4)
```

```
## 
## Call:
## lm(formula = Price ~ HarvestRain + WinterRain, data = wine)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -1.0933 -0.3222 -0.1012  0.3871  1.1877 
## 
## Coefficients:
##               Estimate Std. Error t value Pr(>|t|)    
## (Intercept)  7.865e+00  6.616e-01  11.888 4.76e-11 ***
## HarvestRain -4.971e-03  1.601e-03  -3.105  0.00516 ** 
## WinterRain  -9.848e-05  9.007e-04  -0.109  0.91392    
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 0.5611 on 22 degrees of freedom
## Multiple R-squared:  0.3177,	Adjusted R-squared:  0.2557 
## F-statistic: 5.122 on 2 and 22 DF,  p-value: 0.01492
```
