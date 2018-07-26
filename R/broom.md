# Broom

convert messy output of statistical tools to tidy dataframes
Just experiment with the functions in every specific case and see what they give you.

used functions:
* `lm`  
* `kmeans`
* `aov`
* `tukey_hsd`

## tidy

uses the output object of a statistical function (like a linear model) and turns the essential part into a dataframe.

```R
carmodel <- lm(mpg ~ wt+cyl, mtcars)
df_carmodel <- tidy(carmodel)

#          term  estimate std.error statistic      p.value
# 1 (Intercept) 39.686261 1.7149840 23.140893 3.043182e-20
# 2          wt -3.190972 0.7569065 -4.215808 2.220200e-04
# 3         cyl -1.507795 0.4146883 -3.635972 1.064282e-03
```

## augment

adds some extra columns to the source data of the model.
contains more statistical information.

```R
carmodel <- lm(mpg ~ wt+cyl, mtcars)
cardata <- augment(carmodel)

#              .rownames  mpg    wt cyl  .fitted   .se.fit      .resid       .hat
# 1            Mazda RX4 21.0 2.620   6 22.27914 0.6011667 -1.27914467 0.05482311
# 2        Mazda RX4 Wag 21.0 2.875   6 21.46545 0.4976294 -0.46544677 0.03756521
# 3           Datsun 710 22.8 2.320   4 26.25203 0.7252444 -3.45202624 0.07978891
# 4       Hornet 4 Drive 21.4 3.215   6 20.38052 0.4602669  1.01948376 0.03213611
#      .sigma      .cooksd  .std.resid
# 1  2.601105 0.0050772590 -0.51244825
# 2  2.611423 0.0004442585 -0.18478693
# 3  2.522911 0.0567764620 -1.40157794
# 4  2.605613 0.0018029260  0.40360828
```

this will give for every datapoint the fitted value and some error values.
**Cooks-distance** detects unusual values for example.


## glance

constructs a one row summary of the object.

```R
carmodel <- lm(mpg ~ wt+cyl, mtcars)
cardata <- glance(carmodel)

#   r.squared adj.r.squared    sigma statistic      p.value df    logLik      AIC
# 1 0.8302274     0.8185189 2.567516  70.90836 6.808955e-12  3 -74.00503 156.0101
#       BIC deviance df.residual
# 1 161.873  191.172          29
```
