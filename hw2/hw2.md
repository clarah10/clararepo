hw2
================
jiyeon
September 12, 2016

3.2.1 Exercises
---------------

1.  As you can see in the below, the ggplot gives the empty plot. This is because the "mpg" data include more than two varibles.

``` r
library(ggplot2)
library(tibble)
ggplot(data = mpg)
```

![](hw2_files/figure-markdown_github/cars-1.png)

1.  According to the help, drv variable has three categories. 'f' means front-wheel drive, 'r' means rear wheel drive, and '4' means 4wd.

2.  

``` r
plot(mpg$hwy, mpg$cyl)
```

![](hw2_files/figure-markdown_github/unnamed-chunk-1-1.png)

1.  This command does not work, giving an error. This is because x and y variables are non-numeric variables.

3.3.1 Exercises
---------------

1.  The following command gives the blue points. Since the 'aes' command generates how variables in the data are mapped to visual 'properties' of geoms, the color command in aes should be the function of x or y. But we just need to draw blue points here. So we should move out the color command from aes command.

``` r
ggplot(data = mpg) + 
  geom_point(mapping = aes(x = displ, y = hwy), color = "blue")
```

![](hw2_files/figure-markdown_github/unnamed-chunk-2-1.png)

1.  categorical: manufacturer, model, trans, drv, fl, class continuous: displ discrete: year, cyl, cty, hwy If you run the data, the head of the data shows the types of variables; <chr>, <dbl>, <int> <chr> (character) is a categorical variable, <dbl> (double precision) is a continuous variable, and <int> (integer) is a discrete variables.

2.  

``` r
ggplot(data=mpg)+geom_point(mapping=aes(x=cty, y=hwy, color=displ))
```

![](hw2_files/figure-markdown_github/unnamed-chunk-3-1.png)

``` r
ggplot(data=mpg)+geom_point(mapping=aes(x=cty, y=hwy, color=drv))
```

![](hw2_files/figure-markdown_github/unnamed-chunk-3-2.png)

``` r
ggplot(data=mpg)+geom_point(mapping=aes(x=cty, y=hwy, size=displ))
```

![](hw2_files/figure-markdown_github/unnamed-chunk-4-1.png)

``` r
ggplot(data=mpg)+geom_point(mapping=aes(x=cty, y=hwy, size=drv))
```

    ## Warning: Using size for a discrete variable is not advised.

![](hw2_files/figure-markdown_github/unnamed-chunk-4-2.png)

``` r
ggplot(data=mpg)+geom_point(mapping=aes(x=cty, y=hwy, shape=factor(as.integer(displ))))+scale_shape_manual(values=c(1:7))
```

![](hw2_files/figure-markdown_github/unnamed-chunk-5-1.png)

``` r
ggplot(data=mpg)+geom_point(mapping=aes(x=cty, y=hwy, shape=drv))
```

![](hw2_files/figure-markdown_github/unnamed-chunk-5-2.png)

1.  

``` r
ggplot(data=mpg)+geom_point(mapping=aes(x=cty, y=hwy, color=drv, shape=drv))
```

![](hw2_files/figure-markdown_github/unnamed-chunk-6-1.png)

``` r
ggplot(data=mpg)+geom_point(mapping=aes(x=cty, y=hwy, color=fl, shape=drv))
```

![](hw2_files/figure-markdown_github/unnamed-chunk-6-2.png)

1.  

``` r
ggplot(data=mpg)+geom_point(mapping=aes(x=cty, y=hwy, color=displ), shape=21, stroke=2)
```

![](hw2_files/figure-markdown_github/unnamed-chunk-7-1.png)

1.  

``` r
ggplot(data=mpg)+geom_point(mapping=aes(x=cty, y = hwy, shape=displ<5))
```

![](hw2_files/figure-markdown_github/unnamed-chunk-8-1.png)

3.5.1 Exercises
---------------

1.  

``` r
ggplot(data = mpg)+geom_point(mapping=aes(x=cty, y=hwy))+facet_wrap(~displ)
```

![](hw2_files/figure-markdown_github/unnamed-chunk-9-1.png)

1.  

``` r
ggplot(data = mpg)+geom_point(mapping=aes(x=cty, y=hwy))+facet_grid(drv~cyl)
```

![](hw2_files/figure-markdown_github/unnamed-chunk-10-1.png)

1.  

``` r
ggplot(data = mpg) + 
  geom_point(mapping = aes(x = displ, y = hwy)) +
  facet_grid(drv ~ .)
```

![](hw2_files/figure-markdown_github/unnamed-chunk-11-1.png)

``` r
ggplot(data = mpg) + 
  geom_point(mapping = aes(x = displ, y = hwy)) +
  facet_grid(. ~ cyl)
```

![](hw2_files/figure-markdown_github/unnamed-chunk-11-2.png)

1.  

``` r
ggplot(data = mpg) + 
  geom_point(mapping = aes(x = displ, y = hwy)) + 
  facet_wrap(~ class, nrow = 2)
```

![](hw2_files/figure-markdown_github/unnamed-chunk-12-1.png)

1.  2.  

3.6.1 Exercises
---------------

1.  geom\_line geom\_box geom\_histogram geom\_area

2.  

``` r
ggplot(data = mpg, mapping = aes(x = displ, y = hwy, color = drv)) + 
  geom_point() + 
  geom_smooth(se = FALSE)
```

![](hw2_files/figure-markdown_github/unnamed-chunk-13-1.png)

1.  2.  3.  

``` r
ggplot(data = mpg, mapping = aes(x = displ, y = hwy)) + 
  geom_point() + 
  geom_smooth()
```

![](hw2_files/figure-markdown_github/unnamed-chunk-14-1.png)

``` r
ggplot() + 
  geom_point(data = mpg, mapping = aes(x = displ, y = hwy)) + 
  geom_smooth(data = mpg, mapping = aes(x = displ, y = hwy))
```

![](hw2_files/figure-markdown_github/unnamed-chunk-14-2.png)

1.  

``` r
ggplot(data = mpg, mapping = aes(x = displ, y = hwy)) + 
  geom_point() + 
  geom_smooth(aes(group = drv), se = FALSE)
```

![](hw2_files/figure-markdown_github/unnamed-chunk-15-1.png)

``` r
ggplot(data = mpg, mapping = aes(x = displ, y = hwy)) + 
  geom_smooth(aes(group = drv), se = FALSE) +
  geom_point()
```

![](hw2_files/figure-markdown_github/unnamed-chunk-15-2.png)

``` r
ggplot(data = mpg, mapping = aes(x = displ, y = hwy, color = drv)) + 
  geom_point() + 
  geom_smooth(se = FALSE)
```

![](hw2_files/figure-markdown_github/unnamed-chunk-15-3.png)

``` r
ggplot(data = mpg, mapping = aes(x = displ, y = hwy)) + 
  geom_point(aes(color = drv)) + 
  geom_smooth(se = FALSE)
```

![](hw2_files/figure-markdown_github/unnamed-chunk-15-4.png)

``` r
ggplot(data = mpg, mapping = aes(x = displ, y = hwy)) + 
  geom_point(aes(color = drv)) +
  geom_smooth(aes(linetype = drv), se = FALSE)
```

![](hw2_files/figure-markdown_github/unnamed-chunk-15-5.png)

``` r
ggplot(data = mpg, mapping = aes(x = displ, y = hwy)) + 
  geom_point(size = 4, colour = "white") + 
  geom_point(aes(colour = drv))
```

![](hw2_files/figure-markdown_github/unnamed-chunk-15-6.png)

3.7.1 Exercises
---------------

1.  

``` r
ggplot(data = diamonds) + 
  geom_bar(mapping = aes(x = cut, y = ..prop..))
```

![](hw2_files/figure-markdown_github/unnamed-chunk-16-1.png)

``` r
ggplot(data = diamonds) + 
  geom_bar(mapping = aes(x = cut, y = ..prop..,group=1))
```

![](hw2_files/figure-markdown_github/unnamed-chunk-17-1.png)

1.  According to help, by default, geom\_bar uses stat="count" which makes the height of the bar proportion to the number of cases in each group (or if the weight aethetic is supplied, the sum of the weights).

3.8.1 Exercises
---------------

1.  overlapping problem

``` r
ggplot(data = mpg, mapping = aes(x = cty, y = hwy)) + 
  geom_point()
```

![](hw2_files/figure-markdown_github/unnamed-chunk-18-1.png)

1.  

``` r
ggplot(data = mpg, mapping = aes(x = cty, y = hwy)) + 
  geom_point() + geom_jitter()
```

![](hw2_files/figure-markdown_github/unnamed-chunk-19-1.png)

``` r
ggplot(data = mpg, mapping = aes(x = cty, y = hwy)) + 
  geom_point() + geom_count()
```

![](hw2_files/figure-markdown_github/unnamed-chunk-20-1.png)

1.  

``` r
  ggplot(mpg, aes(drv,displ)) + 
      geom_boxplot()
```

![](hw2_files/figure-markdown_github/unnamed-chunk-21-1.png)

3.9.1 Exercises
---------------

1.  

``` r
pie<-ggplot(data=mpg, aes(x = factor(1), fill = factor(cyl))) +
 geom_bar(width = 1)
pie+coord_polar(theta="y")
```

![](hw2_files/figure-markdown_github/unnamed-chunk-22-1.png)

1.  Change axis labels and legend titles

2.  3.  

``` r
ggplot(data = mpg, mapping = aes(x = cty, y = hwy)) +
  geom_point() + 
  geom_abline() +
  coord_fixed()
```

![](hw2_files/figure-markdown_github/unnamed-chunk-23-1.png)

4.4 Exercises
-------------

1.  'i' character

2.  type: dota-&gt;data

``` r
library(ggplot2)
library(dplyr)
```

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

``` r
ggplot(data = mpg) + 
  geom_point(mapping = aes(x = displ, y = hwy))
```

![](hw2_files/figure-markdown_github/unnamed-chunk-24-1.png)

1.  Tools-&gt;Keyboard Shortcuts Help
