[Think Stats Chapter 4 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2005.html#toc41) (a random distribution)

Import necessary packages...  

import pandas as pd  
import numpy as np  
import thinkstats2  
import thinkplot  

Create series of uniformly distributed from 0 to 1 random numbers

random_series = pd.Series(np.random.random(1000)) 

Create and plot pmf and cdf

pmf = thinkstats2.Pmf(random_series)  
cdf = thinkstats2.Cdf(random_series)  
thinkplot.Pmf(pmf)  
thinkplot.Cdf(cdf)  

The series is in fact uniformly distributed. In the pmf you can see that the probability of a number being any specific value within the range is the same as the probability of it being any other specific value in the range (the pmf is horizontal). The cdf is a straight diagonal line, which indicates, as said in the textbook, ten percent of the sample is below the 10th percentile and so on.
