CE17B115.Assignment\_2
================
Pranav Hari
3 February 2019

1.The function should have the declaration: Piecewise&lt;-function(x,y), where x and y are number inputs. Calculate the following:

(a). Piecewise(2,2)

(b). Piecewise(2,-2)

(c). Piecewise(-2,2)

(d). Piecewise(-2,-2)

(e). Piecewise(0,0)

(f). Piecewise(0,2)

(g). Piecewise(0,-2)

(h). Piecewise(2,0)

``` r
Piecewise <- function(x,y){
  s=0
  if(x>=0 && y>0){
    s = 4*x + 4*y
  }
  else if(x<0 && y>=0){
    s = -4*x + 4*y
  }
  else if(x<=0 && y<0){
    s = -4*(x+y)
  }
  else if(x>0 && y<=0){
    s = 4*x + (-4*y)
  }
  else {
    s=0
  }
return (s)
}

print(Piecewise(2,2))
```

    ## [1] 16

``` r
print(Piecewise(2,-2))
```

    ## [1] 16

``` r
print(Piecewise(-2,2))
```

    ## [1] 16

``` r
print(Piecewise(-2,-2))
```

    ## [1] 16

``` r
print(Piecewise(0,0))
```

    ## [1] 0

``` r
print(Piecewise(0,2))
```

    ## [1] 8

``` r
print(Piecewise(0,-2))
```

    ## [1] 8

``` r
print(Piecewise(2,0))
```

    ## [1] 8

2.Write a function Days.in.Month to display the number of days in a given month. The function should have the header: Days.in.Month &lt;- function(month,leap), where the input month is an all-lower-case string denoting the first three letters of the month. The input leap has logical value (0 or 1) indicating the leap year. February has 28 days (29 days in leap year). The following months have 30 days: April, June, September and November. Other months have 31 days. In cases where the inputs are invalid, the output days should be the string Invalid inputs. Use switch statements.

``` r
Days.in.Month <- function(month,leap){
  switch(month,
         'jan' = 31,
         'mar' = 31,
         'apr' = 30,
         'may' = 31,
         'jun' = 30,
         'jul' = 31,
         'aug' = 31,
         'sep' = 30,
         'oct' = 31,
         'nov' = 30,
         'dec' = 31,
         'feb' = (if(leap == 1){
            29
         }
         else { 28
          }
         ),
         print("Invalid inputs")
      )   
}
Days.in.Month('jan',0)
```

    ## [1] 31

``` r
Days.in.Month('feb',0)
```

    ## [1] 28

``` r
Days.in.Month('feb',1)
```

    ## [1] 29

``` r
Days.in.Month('apr',0)
```

    ## [1] 30

``` r
Days.in.Month('aug',1)
```

    ## [1] 31

``` r
Days.in.Month('oct',0)
```

    ## [1] 31

``` r
Days.in.Month('nov',1)
```

    ## [1] 30

``` r
Days.in.Month('Dec',0)
```

    ## [1] "Invalid inputs"

1.  Write a function Trans using for loops to calculate the transpose of a matrix. The function should have the header: Trans &lt;- function(Mat), where the input Mat is a matrix. (Do not use the in-built transpose function). Take a 3×4 matrix and find its transpose.

``` r
Trans <- function(Mat){
  tmat = matrix(,dim(Mat)[2],dim(Mat)[1])
 for(i in 1:dim(Mat)[1]) {
    for(j in 1:dim(Mat)[2]) {
      tmat[j,i] = Mat[i,j]
    }
  }
return(tmat)
}

test_mat = matrix(1:12,3,4)
test_mat
```

    ##      [,1] [,2] [,3] [,4]
    ## [1,]    1    4    7   10
    ## [2,]    2    5    8   11
    ## [3,]    3    6    9   12

``` r
print(Trans(test_mat))
```

    ##      [,1] [,2] [,3]
    ## [1,]    1    2    3
    ## [2,]    4    5    6
    ## [3,]    7    8    9
    ## [4,]   10   11   12

1.  Write a program which uses a while loop to sum the cubes of positive integers (starting from 1) until the total exceeds 6000. Print the final total and the last number to be cubed and added.

``` r
total = 0
i=1
while(total<=6000){
  total = i*i*i + total
  i=i+1
}
total
```

    ## [1] 6084

``` r
i
```

    ## [1] 13
