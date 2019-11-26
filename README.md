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
![equation](http://www.sciweavers.org/upload/Tex2Img_1574780243/render.png)
where Y is respond variable and X's are predictors, the estimated equation is following:
![equation](http://www.sciweavers.org/upload/Tex2Img_1574780406/render.png)
based on the observation samples of respond Y and predictor X's.

Least Squares Method aimed to estimate the coefficients above by minimizing residual sum of squares so that ![equation](http://www.sciweavers.org/upload/Tex2Img_1574780535/render.png). And this package uses RcppArmadillo to do matrix operation during estimation for efficiency.

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
The result will return a list of estimates and inference results: "Coefficients", "F test and R square", "Fitted values", "Residuals", "Sum of Squares", "X inverse matrix", and "Coefficients Variance".

In addition, there are 4 optional arguments for using lr() more flexily:
 
***data***: indicates the dataframe name where variables' data come from. 

***coding***: "reference"(by default) or "means", which indicates the **cell reference coding** or **cell means coding** method used when categorical X included. The revious one will take first appeared group of X as reference and reserve the intercept term while the latter one will eliminate the intercept of the model.

***intercept***: "TRUE"(by default) or "FALSE", which indicates whether the model will contains an intercept term

***reference***:  1 (by default take the first appeared group of X as reference) or any group value of included categorical X choosen as reference group.

```r
result1 = lr(y ~ x1 + x2 + x3) ##coding = "reference", intercept = TRUE, reference = 1

result2 = lr(y ~ x1 + x2 + x3, coding = "means") ##with cell means coding method

result3 = lr(y ~ x1 + x2 + x3, intercept = FALSE) ##elinimate intercept term

result4 = lr(y ~ x1 + x2 + x3, reference = "F") ##speficy "F" reference group

```

## Support

For fully knowing the usage and characteristics of this package or lr(), you could check vignettes with:

```r
browseVignettes("testPkg")
```

or check the help page with

```r
?lr
```

## Performance

Firstly, lr() havs same correctness performance with lm(). Secondly, lr() is more efficient and uses less memory than common used lm() regarding to small or big samples without categorical variables. When categorical samples included for estimating model, lr() is less efficient than lm(). However, lr() uses less memory than lm() and you can specify any group as reference flexibly. 

 