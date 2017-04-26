Visualization
========================================================
author: Sri Sehadri
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
 - Cummins Data
 
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
    <span style = "color:Red">GEOM_FUNCTION</span>(mapping = aes(<span style = "color:Red">MAPPINGS</span>) 
   


 
Slide With Code
========================================================


```r
summary(cars)
```

```
     speed           dist       
 Min.   : 4.0   Min.   :  2.00  
 1st Qu.:12.0   1st Qu.: 26.00  
 Median :15.0   Median : 36.00  
 Mean   :15.4   Mean   : 42.98  
 3rd Qu.:19.0   3rd Qu.: 56.00  
 Max.   :25.0   Max.   :120.00  
```

Slide With Plot
========================================================

![plot of chunk unnamed-chunk-3](Visualization-figure/unnamed-chunk-3-1.png)
