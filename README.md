# BreakoutDetection R package

BreakoutDetection is an open-source R package that makes breakout detection simple and fast. The BreakoutDetection package can be used in wide variety of contexts. For example, detecting breakout in user engagement post an A/B test, detecting [behavioral change](http://wiki.cbr.washington.edu/qerm/index.php/Behavioral_Change_Point_Analysis), or for problems in econometrics, financial engineering, political and social sciences.

## How the package works
The underlying algorithm – referred to as E-Divisive with Medians (EDM) – employs energy statistics to detect divergence in mean. Note that EDM can also be used detect change in distribution in a given time series. EDM uses [robust statistical metrics](http://www.wiley.com/WileyCDA/WileyTitle/productCd-0470129905.html), viz., median, and estimates the statistical significance of a breakout through a permutation test. 

In addition, EDM is non-parametric. This is important since the distribution of production data seldom (if at all) follows the commonly assumed normal distribution or any other widely accepted model. Our experience has been that time series often contain more than one breakout. To this end, the package can also be used to detect multiple breakouts in a given time series.

## How to get started
Download the package by cloning the git repo via the following command. 
```
git clone https://github.com/twitter/breakout.git
```
Install the R package using the following commands on the R console:

### Install the dependencies
```
install.packages(c(“ggplot2”, “stringr”, “scales”, “Rcpp”))
library(c(“ggplot2”, “stringr”, “scales”, “Rcpp”))
```
### Install the package from source
```
install.packages("BreakoutDetection_1.0.1.tar.gz", repos=NULL, type='source') 
library(BreakoutDetection)
```

The function breakout is called to detect one or more statistically significant breakouts in the input time series. The documentation of the function breakout, which can be seen by using the following command, details the input arguments and the output of the function breakout.

```
help(breakout)
```

## A simple example
To get started, the user is recommended to use the example dataset which comes with the packages. Execute the following commands:

```
data(Scribe)
res = breakout(Scribe, min.size=24, method='multi', beta=.001, degree=1, plot=TRUE)
res$plot
```

From the plot, we observe that the input time series experiences a breakout and also has quite a few anomalies. The two red vertical lines denote the locations of the breakouts detected by the EDM algorithm. 

## Copyright and License

Copyright 2014 Twitter, Inc and other contributors.

Licensed under the Apache License, Version 2.0: http://www.apache.org/licenses/LICENSE-2.0
