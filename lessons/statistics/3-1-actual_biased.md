[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

#Question 2: Chapter 3 Exercise 1
#Use NSFG respondent variable to construct actual and biased distro for number of children under 18 in households

from __future__ import print_function, division


import numpy as np

import nsfg
import first
import thinkstats2
import thinkplot

resp = nsfg.ReadFemResp()

pmf = thinkstats2.Pmf(resp.numkdhh, label='numkdhh')

biased = BiasPmf(pmf, label='biased')
thinkplot.PrePlot(2)
thinkplot.Pmfs([pmf, biased])
thinkplot.Config(xlabel='Number of children', ylabel='PMF')

print('Actual mean', pmf.Mean())
print('Observed mean', biased.Mean())

#Compute means of actual and biased distributions
#Output = PMF Mean: 1.0242; Biased Mean: 2.4036
