[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

Finding the pmf from the provided data...  

import numpy as np  
import pandas as pd  
import nsfg  
import thinkstats2  
import thinkplot  

fem = nsfg.ReadFemResp()  
pmf = thinkstats2.Pmf(fem['numkdhh'])  

Computing the biased pmf, as though children were surveyed about the number of children in their hoousehold including themselves.

biased_pmf = pmf.Copy()  
for x, p in pmf.Items():  
    biased_pmf.Mult(x, x)  
        
biased_pmf.Normalize()  

Plotting the two pmfs...

thinkplot.preplot(2)
thinkplot.Pmf(pmf)
thinkplot.Pmf(biased_pmf)

Calculating means...

pmf.Mean()
1.024205155043831

biased_pmf.Mean()
2.403679100664282

One key difference in the biased pmf, in addition to the issue discussed in the class size example, is that it ignores households with no children. This explains why the mode of the unbiased pmf is zero and the biased pmf has no zeroes.
