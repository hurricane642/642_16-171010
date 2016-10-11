# 642_16-171010
import random

import numpy as np

def get_percentile(values,n):#1
  percentiles=[]
  k=0
  while k<1:
    k=k*100
    if k==0:
      a=0.0
    else:
      a=np.percentile(values, k)
    percentiles.append(a)
    k=k/100
    k=k+1/n
    return(percentiles)
    
def get_percentile_number(value, percentiles): #2
  for i in range(len(percentiles)):
    if percentiles[i]<=value:
      a=i
    return(a)
    
def value_equalization(value,percentiles,add_random=False): #3 4
  idx = get_percentile_number(value, percentiles)
  step = 1/len(percentiles)
  new_value = idx*step
  if add_random==True:
    new_value = random.uniform(idx*step, (idx+1)*step)
  return(new_value)
  
def values_equalization(values, percentiles,add_random=True): #5
  for i in range(len(values)):
    values[i]=value_equalization(values[i],percentiles,add_random=False)
return(values)
