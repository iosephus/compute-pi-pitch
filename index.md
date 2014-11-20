---
title       : Estimation of π
subtitle    : Coursera Developing Data Products course project
author      : Jose M. Perez-Sanchez
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## What is π?

The number π is a mathematical constant, the ratio of a circle's circumference to its diameter, approximately equal to 3.14159. It has been represented by the Greek letter "π" since the mid-18th century though it is also sometimes spelled out as "pi" (/paɪ/). (https://en.wikipedia.org/wiki/Pi)

![plot of chunk unnamed-chunk-1](assets/fig/unnamed-chunk-1-1.png) 



--- .class #id 

## Our estimation of π

General procedure:

* Estimate π using the formula for the area of the circle

* Estimate the area of the circle using a Monte Carlo method (random numbers)

Estimation of the area and π:

* For a circle inscribed in a square, the side of the square is twice the radius of the circle. The area of the square is the square of its side.

* For random points inside the square with a uniform distribution for each coordinate, the probability of a point falling inside the circle is equal to the ratio between the areas of the circle and the square.

* The ratio of the number of points inside the circle to the total number of points, multiplied by four, will converge to π as the number of point tends to infinity.

---
## Example


```r
num.points <- 1e6
set.seed(623)
x <- runif(num.points, -1, 1)
y <- runif(num.points, -1, 1)
# No square root needed for comparison since radius is one
count.inside <- sum(x^2 + y^2 < 1)
pi.est <- 4 * count.inside / num.points
```

```
## [1] "PI estimation:    3.141756"
```

```
## [1] "Reference value:  3.14159265358979"
```

```
## [1] "Error of this estimation:  0.0052 %"
```

---
## Wrap-up

* This method converges very slow compared to others, since you need many points to make a good estimation

BUT:

* This method is simple and is a very nice example for students. It shows a simple and straighforward application of Monte Carlo.

Check the web app:

* https://iosephus.shinyapps.io/Compute-Pi/
