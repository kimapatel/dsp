[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

from __future__ import print_function, division

#%matplotlib inline

import numpy as np

import nsfg
import first
import thinkstats2
import thinkplot

preg = nsfg.ReadFemPreg()
live = preg[preg.outcome == 1]

firsts = live[live.birthord == 1]
others = live[live.birthord != 1]

mean = live.totalwgt_lb.mean()
var = live.totalwgt_lb.var()
std = live.totalwgt_lb.std()

print(firsts.totalwgt_lb.mean(), others.totalwgt_lb.mean())

#Output = (7.201094430437772, 7.325855614973262) --> first babies are lighter than others

#Question - Using Cohen's d, quantify the difference between groups
from __future__ import print_function, division

#%matplotlib inline

import numpy as np

import nsfg
import first
import thinkstats2
import thinkplot

preg = nsfg.ReadFemPreg()
live = preg[preg.outcome == 1]

firsts = live[live.birthord == 1]
others = live[live.birthord != 1]

mean = live.totalwgt_lb.mean()
var = live.totalwgt_lb.var()
std = live.totalwgt_lb.std()


def CohenEffectSize(group1, group2):
    """Computes Cohen's effect size for two groups.
    
    group1: Series or DataFrame
    group2: Series or DataFrame
    
    returns: float if the arguments are Series;
             Series if the arguments are DataFrames
    """
    diff = group1.mean() - group2.mean()

    var1 = group1.var()
    var2 = group2.var()
    n1, n2 = len(group1), len(group2)

    pooled_var = (n1 * var1 + n2 * var2) / (n1 + n2)
    d = diff / np.sqrt(pooled_var)
    return d

print(CohenEffectSize(firsts.totalwgt_lb, others.totalwgt_lb) )
#Output  = -0.088672927072602

#Question - How does it compare to the difference in pregnancy length?
#The difference in weight between first babies and other babies is smaller than the difference in length
