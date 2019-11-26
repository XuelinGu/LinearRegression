# LinearRegression

  <!-- badges: start -->
  [![Travis build status](https://travis-ci.org/XuelinGu/LinearRegression.svg?branch=master)](https://travis-ci.org/XuelinGu/LinearRegression)
  <!-- badges: end -->
  <!-- badges: start -->
  [![Codecov test coverage](https://codecov.io/gh/XuelinGu/LinearRegression/branch/master/graph/badge.svg)](https://codecov.io/gh/XuelinGu/LinearRegression?branch=master)
  <!-- badges: end -->
  
# LinearRegression
testPkg is a R package for fitting linear regression model using Least Squares Method.

For linear regression model with similar function form below:
$Y_{i} = \beta_{0} + \beta_{1} X_{1i} + \beta_{2} X_{2i} + \epsilon_{i}$,
where Y is respond variable and X's are predictors, the estimated equation is following:
$\hat{Y_{i}} = \hat{\beta_{0}} + \hat{\beta_{1}} X_{1i} + \hat{\beta_{2}} X_{2i}$
based on the observation samples of respond Y and predictor X's.

Least Squares Method aimed to estimate the coefficients above by minimizing residual sum of squares.

## Installation

Use package devtools to install testPkg package.

```r
library(devtools)
devtools::install_github("XuelinGu/LinearRegression", build_vignettes = T)
library(testPkg)
```

## Usage

There is one main function lr() in this package. Basically, you can use the add formula to the argument which includes respond variable left, predictor variable right and connects previous two elements with ~, to run the function lr():

```r
y = c(23, 24, 26, 37, 38, 25, 36, 40)
x1 = c(1, 2, 3, 4, 5, 6, 7, 8)
x2 = c(23, 32, 34, 20, 24, 56, 34, 24)
result = lr(y ~ x1 + x2)
result
```
And the result will return a list of estimates and inference results: "Coefficients", "F test and R square", "Fitted values", "Residuals", "Sum of Squares", "X inverse matrix", and "Coefficients Variance".

For fully knowing the usage and characteristics of this package or lr(), you could check vignettes with:

```r
browseVignettes("testPkg")
```

or check the help page with

```r
?lr
```