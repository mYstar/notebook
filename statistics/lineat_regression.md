<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS_HTML"></script>

# Linear Regression

* signifikant relationship between variables
* + Forecast new observations

## Variables

* **dependent variable**: to be explained or forecasted
    * values depend on other variables  
    * also: response variable
    * common: `y`
* **independent variable**: explains the other one
    * common: `x`

## Equation

![http://latex.codecogs.com/png.latex?\large&space;y=\beta_0&plus;\beta_1x](y = beta_0 + beta_1 x) is used.
Hence linear regression.

* `\beta_0` = intercept, constant
    * no intuitive explanation
* `\beta_1` = coefficient, slope
    * has an intuitive explanation

Linear Regression draws a line, that minimizes the distance of the slope to the data points.
The remaining distance is the error.

## Errors

`y = beta_0 + beta_1 x + epsilon` is including an error term.
This is also called the **residual**.
Can be calculated for every data point with: `r_i = y_i - (x_i * beta_1 + beta_0)`
Sum of squares is calculated to rate the fit of the model: `\sum (r_i)^2`

Also: **coefficient of determination** `R^2` can be used to rate the model. (1.0 is perfect, 0.0 is worst)

**Least squares regression** minimizes the sum of squares.

Plotting the residuals can reveal information, if the model is a good fit.
If there is no even distribution or a curvature, then a **transformation of the response variable** could be necessary.

## Transformations

Not every data set has a linear relationship.
When the data is transformed, other releationships can be tested with the linear formula.

Popular: Logarithmic, square root, reciprocal transformation.

against curvature of residual plot:
* log transformation of y (strong)
    * `log y = beta_0 + beta_1 x + epsilon`
* square root transformation of y (weaker)
    * `sqrt y = beta_0 + beta_1 x + epsilon`

 
