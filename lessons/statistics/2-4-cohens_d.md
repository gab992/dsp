[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

Cohen's d for the difference in effect on total birth weight in points for first babies and other live births is -0.06911936019885215.

The code I used is as follows...

import pandas as pd  
import numpy as np  
import thinkstats2  
import nsfg  
import thinkplot  
import math  

preg=nsfg.ReadFemPreg()  
live=preg[preg.outcome == 1]  
first=live[live.pregordr == 1]  
other=live[live.pregordr != 1]  
diff = first['totalwgt_lb'].mean() - other['totalwgt_lb'].mean()  
var_first = first['totalwgt_lb'].var()  
var_other = other['totalwgt_lb'].var()  
n1, n2 = len(first['totalwgt_lb']), len(other['totalwgt_lb'])  
pooled_var = (n1 * var_first + n2 * var_other) / (n1 + n2)  
d = diff / math.sqrt(pooled_var) 

Cohen's d for pregnancy length was 0.029. This is different from cohen's d for birth weight in that it is positive, meaning non-first pregnancies are more often longer than first pregnancies, but yield a lower birth weight. Neither of these results, however, can be taken too seriously because the effects are very small and would likely not be noticeable.
