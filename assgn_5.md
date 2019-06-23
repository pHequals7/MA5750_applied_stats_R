CE17B115.Assignment\_5
================
Pranav Hari
8 March 2019

Dataset - diamonds
==================

``` r
library(ggplot2)
```

    ## Warning: package 'ggplot2' was built under R version 3.5.3

``` r
head(diamonds)
```

    ## # A tibble: 6 x 10
    ##   carat cut       color clarity depth table price     x     y     z
    ##   <dbl> <ord>     <ord> <ord>   <dbl> <dbl> <int> <dbl> <dbl> <dbl>
    ## 1 0.23  Ideal     E     SI2      61.5    55   326  3.95  3.98  2.43
    ## 2 0.21  Premium   E     SI1      59.8    61   326  3.89  3.84  2.31
    ## 3 0.23  Good      E     VS1      56.9    65   327  4.05  4.07  2.31
    ## 4 0.290 Premium   I     VS2      62.4    58   334  4.2   4.23  2.63
    ## 5 0.31  Good      J     SI2      63.3    58   335  4.34  4.35  2.75
    ## 6 0.24  Very Good J     VVS2     62.8    57   336  3.94  3.96  2.48

(a). Specify the continuous variables and categorical variables in the dataset.
===============================================================================

Continuous - carat, depth, table, price, x, y, z
------------------------------------------------

Categorical - cut, color, clarity
---------------------------------

(b). How is the carat related to price? Visualise using the function ggplot() and the most appropriate geom\_function(). Assign the output to the variable "Plot". Customize your plot by adding a suitable title and axis labels.
==================================================================================================================================================================================================================================

``` r
Plot <- ggplot(diamonds,aes(carat,price))+geom_point(colour="blue")+ggtitle("Price vs CARAT")
Plot
```

![](assgn_5_files/figure-markdown_github/unnamed-chunk-2-1.png) \#\# Price and Carat are almost linearly proportional from carat 0-2

(c). Redraw the plot with alpha=0.4, color= blue, size=2 and a "dark red" regression line using an appropriate linear model method.
===================================================================================================================================

``` r
Plot <- ggplot(diamonds,aes(carat,price))+geom_point(alpha=0.4, color='blue',size=2)+ggtitle("Price vs CARAT")+stat_smooth(method = 'lm',color="dark red")
Plot
```

![](assgn_5_files/figure-markdown_github/unnamed-chunk-3-1.png)

(d). Visualise the weight and price of the carat using a third variable "cut".
==============================================================================

``` r
ggplot(diamonds,aes(x = x*y*z, y = price,color = cut))+labs(x="Weight",y="Price")+geom_point()
```

![](assgn_5_files/figure-markdown_github/unnamed-chunk-4-1.png)

(e). Recreate the plot in (d) by creating a separate facet for each value of the variable "cut" using facet\_wrap().
====================================================================================================================

``` r
ggplot(diamonds,aes(x = x*y*z, y = price,color = cut))+labs(x="Weight",y="Price")+geom_point()+facet_wrap(~cut)
```

![](assgn_5_files/figure-markdown_github/unnamed-chunk-5-1.png)

(f). Using facet\_grid(), visualise the relationship between carat vs. Price and Clarity based on the different values of "cut" and write the analysis.
=======================================================================================================================================================

``` r
ggplot(diamonds,aes(x = carat, y = price,color = clarity))+geom_point()+facet_grid(~cut)
```

![](assgn_5_files/figure-markdown_github/unnamed-chunk-6-1.png) \#\# Analysis \#\#\# Premium, ideal and Very Good cuts have very similar price vs carat distribution wrt clarity \#\#\# While Good cut has very less number of IF clarity diamonds and Fair cut has almost no IF and VVS1 clarity diamonds but all other clarities have similar price vs carat distb like the rest of the carats \#(g). Visualise clarity and cut vs price for 54,000 diamonds using boxplot and write the analysis.

``` r
ggplot(diamonds, aes(cut,price,fill=clarity))+geom_boxplot()
```

![](assgn_5_files/figure-markdown_github/unnamed-chunk-7-1.png) \#Analysis \#\# Clarity - IF \#\#\# The price is evenly distributed for Fair and Ideal cuts while has large variations for Good, Very Good and Premium cuts

Clarity - VVS1
--------------

### The price is evenly distributed for Premium, Fair and Ideal cuts and has a large variance for Very Good and Good cuts

Clarity - VVS2
--------------

### The price is evenly distributed for only Fair cut while has medium to large variance for the rest of the cuts

Clarity - VS1
-------------

### The price has medium to large variance across all cuts

Clarity - VS2
-------------

### Fair and Good cuts have even distribution of price whereas Very Good, Premium and Ideal have medium price variance

Clarity - SI1
-------------

### Fair, Good and Premium cuts are evenly distributed with price wheareas other cuts have larger variance

Clarity - SI2 and I1
--------------------

### Both clarities have medium to large variances with respect to their prices for all their cuts

(h). Using geom\_density(), visualise the relationship between price and cut. Use alpha=0.5.
============================================================================================

``` r
ggplot(diamonds,aes(price,fill=cut))+geom_density(alpha=0.5)
```

![](assgn_5_files/figure-markdown_github/unnamed-chunk-8-1.png)
