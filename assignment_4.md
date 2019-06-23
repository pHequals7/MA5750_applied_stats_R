assignment4
================
Pranav Hari
25 February 2019

1.  A binary source generates digits 1 and 0 randomly with probabilities 0.6 and 0.4, respectively. (a). What is the probability that two 1's and three 0's will occur in a five-digit sequence?

``` r
library(distr)
```

    ## Warning: package 'distr' was built under R version 3.5.3

    ## Loading required package: startupmsg

    ## Warning: package 'startupmsg' was built under R version 3.5.3

    ## Utilities for Start-Up Messages (version 0.9.6)

    ## For more information see ?"startupmsg", NEWS("startupmsg")

    ## Loading required package: sfsmisc

    ## Object Oriented Implementation of Distributions (version 2.8.0)

    ## Attention: Arithmetics on distribution objects are understood as operations on corresponding random variables (r.v.s); see distrARITH().
    ## Some functions from package 'stats' are intentionally masked ---see distrMASK().
    ## Note that global options are controlled by distroptions() ---c.f. ?"distroptions".

    ## For more information see ?"distr", NEWS("distr"), as well as
    ##   http://distr.r-forge.r-project.org/
    ## Package "distrDoc" provides a vignette to this package as well as to several extension packages; try vignette("distr").

    ## 
    ## Attaching package: 'distr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     df, qqplot, sd

``` r
#binomial distribution
B <- Binom(prob=0.6,size=5)
d(B)(2)
```

    ## [1] 0.2304

1.  What is the probability that at least three 1's will occur in a five-digit sequence?

``` r
1-p(B)(2)
```

    ## [1] 0.68256

1.  Consider an experiment of tossing a fair coin repeatedly until the coin lands heads the sixth time. Find the probability that it takes exactly 10 tosses.

``` r
#negative binomial distribution 
A <- Nbinom(prob=0.5,size=6)
d(A)(4)
```

    ## [1] 0.1230469

1.  An experiment consists of observing the sum of the dice when two fair dice are thrown.

<!-- -->

1.  Find the probability that the sum is 7.

``` r
library(prob)
```

    ## Loading required package: combinat

    ## 
    ## Attaching package: 'combinat'

    ## The following object is masked from 'package:utils':
    ## 
    ##     combn

    ## Loading required package: fAsianOptions

    ## Loading required package: timeDate

    ## Loading required package: timeSeries

    ## Loading required package: fBasics

    ## Loading required package: fOptions

    ## 
    ## Attaching package: 'fAsianOptions'

    ## The following object is masked from 'package:distr':
    ## 
    ##     igamma

    ## 
    ## Attaching package: 'prob'

    ## The following object is masked from 'package:distr':
    ## 
    ##     prob

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, union

``` r
S <- rolldie(2,makespace = TRUE)
Prob(subset(S,X1+X2 == 7))
```

    ## [1] 0.1666667

(b). Find the probability that it will take less than six tosses to throw a 7.

``` r
G <- Geom(prob=0.1666667)
p(G)(5)
```

    ## [1] 0.6651021

(c). Find the probability that it will take more than six tosses to throw a 7.

``` r
1-p(G)(6)
```

    ## [1] 0.2790816

1.  Let X be a normal distribution with mean 15 and variance 16 (a). P(9???X???18)

``` r
library(visualize)
pnorm(18,15,4)-pnorm(9,15,4)
```

    ## [1] 0.7065654

``` r
visualize.norm(c(9,18),15,4,section = "bounded")
```

![](assignment_4_files/figure-markdown_github/unnamed-chunk-8-1.png) (b). P(9???X???18|X???15)

``` r
(pnorm(15,15,4)-pnorm(9,15,4))/pnorm(15,15,4)
```

    ## [1] 0.8663856

(c). P(|X???15|???0.6)

``` r
pnorm(14.4,15,4,lower.tail = TRUE) + pnorm(15.6,15,4,lower.tail = FALSE)
```

    ## [1] 0.8807646

Let X be a normal distribution with mean -1 and variance 9. (a). Find x such that P(X&gt;x)=0.42.

``` r
qnorm(0.58,-1,3)
```

    ## [1] -0.3943196

(b). Find x such that P(|X+1|&lt;x)=0.45

``` r
# 2*P(-1 < X < x) = 0.45 because of symmetry
# P(X < x) = 0.45/2 + 0.5 = 0.725
qnorm(0.275,-1,3)
```

    ## [1] -2.79328
