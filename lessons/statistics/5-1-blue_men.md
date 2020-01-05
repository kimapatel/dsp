[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

#Question 4: Chapter 5 Exercise 1 - normal distribution of blue men

from __future__ import print_function, division

import numpy as np


import scipy.stats

#solve for only male population, use mu = 178 and sigma = 7.7
mu = 178
sigma = 7.7
dist = scipy.stats.norm(loc=mu, scale=sigma)
type(dist)


low = dist.cdf(177.8)    # insert 177.8 as 5'10" in cm
high = dist.cdf(185.4)   # insert 185.4 as 6'1" in cm
print(low, high, high-low)


#Output - (0.48963902786483265, 0.8317337108107857, 0.3420946829459531)
