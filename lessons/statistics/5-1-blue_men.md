[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

The percentage of the male population that falls within the height range for the blue man group is 0.34274683763147457.

First I wrote a function to convert heighter in feet and inches into centimeters so I could find the cm height cutoff points for blue man group.

import scipy.stats  

def height_to_cm(feet, inches):  
    new_height = (12*feet + inches)*2.54  
    return new_height  

upper_height = height_to_cm(6, 1)  
lower_height = height_to_cm(5, 10)  

Then I used scipy.stats.norm.cdf to calculate the percentiles at the blue man cutoff heights.

upper_percentile = scipy.stats.norm.cdf(upper_height, loc=178, scale=7.7)  
lower_percentile = scipy.stats.norm.cdf(lower_height, loc=178, scale=7.7)  
print(upper_percentile)  
print(lower_percentile)  

The difference between the cutoff percentiles is then the percentage of the male population which fits the blue man group height requirements.

percentage_pop = upper_percentile - lower_percentile  
0.34274683763147457 or 34.274683763147457%
