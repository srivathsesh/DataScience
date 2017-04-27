Visualization
========================================================
author: Sri Seshadri
date: 28th April 2017
autosize: true
css:custom.css

Data Analysis process
========================================================
<!-- ![pyramid](./Visualization-figure/pyramid.png) -->
<div class = "midcenter" style = "margin-left:300px; height:2000px">
<img src = "./Visualization-figure/pyramid.png"></img>
</div>

Extraction and Transformation
========================================================
<br>
Rahul Sangole walked us through how to use <span style = "color:red"> tidyverse / dplyr <span>
* Read file into a dataframe or tibble
* Pipe (magrittr)
* mutate (dplyr) dataframe to add additional attributes to the data.

If you need recall package from Rahul's presentation, reachout to either:
- <span style = "color:blue">Priti Mane </span>
- <span style = "color:blue">Rahul Sangole </span>

Exploratory Data Analysis using R
=======================================================
- Why Code?
  + Frequently changing data
  + May save you a bunch of clicks
  + Reproducibility

- Why code in R
  + Its free (I am not rich)
  + Lots of resources out there
- Can be annoying too
  + While documentations have been standardized, it still can be a pain sometimes!
  + <span style = "color:blue">Don't worry, you still be fine </span>
  
 Packages
=========================================================
 <br>
 - base
 - ggplot2 (Hadley Wickham & Garrett Grolemund)
 - plotly (Plotly technologies Inc.)
 
 Datasets
 - iris
 - mpg
 - diamonds
 
 ***
 
 ![book] (./Visualization-figure/cover.png)
 
If you are wondering why this presentation looks different?
==========================================================
<br>
Or why is this poorly formatted...?

This presentation is made using <span style = "color:Red"> R </span> code 

And... I still have my training wheels on

Training wheels: Google, Stackoverflow, GitHub, <span style = "color:Red"> You </span>

ggplot2
=======================================================

```r
#install.packages("ggplot2")
library(ggplot2)
```
(Wickham & Grolemund, 2017,p.6)

<br>
ggplot template
  - ggplot(data = <span style = "color:Red">data </span>) + <br>
    <span style = "color:Red">GEOM_FUNCTION</span>(mapping = <span style = "color:blue">aes</span>(<span style = "color:Red">MAPPINGS</span>) 
   
<i>An <span style = "color:blue">aes</span>thetic is a visual property of the objects in your plot. Aesthetics include things like size,shape or color of your points.</i>

 
How does the "mpg" data look?
========================================================
<br>

|manufacturer |model | displ| year| cyl|trans      |drv | cty| hwy|fl |class   |
|:------------|:-----|-----:|----:|---:|:----------|:---|---:|---:|:--|:-------|
|audi         |a4    |   1.8| 1999|   4|auto(l5)   |f   |  18|  29|p  |compact |
|audi         |a4    |   1.8| 1999|   4|manual(m5) |f   |  21|  29|p  |compact |
|audi         |a4    |   2.0| 2008|   4|manual(m6) |f   |  20|  31|p  |compact |
|audi         |a4    |   2.0| 2008|   4|auto(av)   |f   |  21|  30|p  |compact |
|audi         |a4    |   2.8| 1999|   6|auto(l5)   |f   |  16|  26|p  |compact |
|audi         |a4    |   2.8| 1999|   6|manual(m5) |f   |  18|  26|p  |compact |
<br>
try the command  "<span style = "color:blue">head(mpg)</span>"

What are the data types?
========================================================
<br>

```r
str(mpg)
```

```
Classes 'tbl_df', 'tbl' and 'data.frame':	234 obs. of  11 variables:
 $ manufacturer: chr  "audi" "audi" "audi" "audi" ...
 $ model       : chr  "a4" "a4" "a4" "a4" ...
 $ displ       : num  1.8 1.8 2 2 2.8 2.8 3.1 1.8 1.8 2 ...
 $ year        : int  1999 1999 2008 2008 1999 1999 2008 1999 1999 2008 ...
 $ cyl         : int  4 4 4 4 6 6 6 4 4 4 ...
 $ trans       : chr  "auto(l5)" "manual(m5)" "manual(m6)" "auto(av)" ...
 $ drv         : chr  "f" "f" "f" "f" ...
 $ cty         : int  18 21 20 21 16 18 18 18 16 20 ...
 $ hwy         : int  29 29 31 30 26 26 27 26 25 28 ...
 $ fl          : chr  "p" "p" "p" "p" ...
 $ class       : chr  "compact" "compact" "compact" "compact" ...
```
Histograms
=========================================================

```r
library(ggplot2)
# What does ggplot(data = mpg) do?
ggplot(data = mpg) + geom_histogram(mapping = aes(x=hwy)) 
```

![plot of chunk unnamed-chunk-4](Visualization-figure/unnamed-chunk-4-1.png)
Aesthetics
=========================================================

```r
ggplot(data = mpg) + geom_histogram(mapping = aes(x=hwy),col="red", fill="red")
```

![plot of chunk unnamed-chunk-5](Visualization-figure/unnamed-chunk-5-1.png)
***

```r
ggplot(data = mpg) + geom_histogram(mapping = aes(x=hwy, col = "red", fill = "red"))
```

![plot of chunk unnamed-chunk-6](Visualization-figure/unnamed-chunk-6-1.png)
Aesthetics contd...
==========================================================
<font size = 5>

```r
ggplot(data = mpg) + geom_histogram(mapping = aes(x=hwy, fill = cyl))
```

![plot of chunk unnamed-chunk-7](Visualization-figure/unnamed-chunk-7-1.png)
</font>
***
<font size = 5>

```r
ggplot(data = mpg) + geom_histogram(mapping = aes(x=hwy, fill = as.factor(cyl)))
```

![plot of chunk unnamed-chunk-8](Visualization-figure/unnamed-chunk-8-1.png)
</font>

Move aesthetics to base layer of plot
============================================================
<font size = 5>

```r
mpg$cyl <- as.factor(mpg$cyl)
ggplot(data=mpg,aes(x=hwy,fill = cyl)) + geom_histogram() + theme_bw()
```

![plot of chunk unnamed-chunk-9](Visualization-figure/unnamed-chunk-9-1.png)
</font>
***
<font size = 5>

```r
library(ggplot2)
p <- ggplot(data = mpg, aes(x=hwy,fill=cyl))
p + geom_density(alpha = 0.3) + theme_classic() + labs(fill = "Cylinders", x = "Highway mpg")
```

![plot of chunk unnamed-chunk-10](Visualization-figure/unnamed-chunk-10-1.png)
</font>

Scatter Plots
==============================================================

