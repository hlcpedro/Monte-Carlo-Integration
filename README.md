# Monte-Carlo-Integration
#Integral evaluation of any given polynomial using the Monte Carlo method, the program also returns a histogram with the distribution of the calculated values and the #expected value of its distribution

from scipy import random
import seaborn as sns
import numpy as np
import matplotlib.pyplot as plt
%matplotlib inline

a = 0
b = 10
N = 1000

def func(x):
  ppar = [4, 3, -2, 10]
  p = np.poly1d(ppar)
  return p(x)

areas = []
for i in range(int(N)):
  integral = 0.0
  xrand = np.zeros(int(N))
  for i in range(len(xrand)):
       xrand[i]= random.uniform(a,b) 

  for i in range(int(N)):
      integral += func(xrand[i])

  integral = (b-a)/float(N)*integral 
  areas.append(integral)
print(f"expected value: {np.mean(areas)}")
sns.displot(data=areas, kde=True, bins=N)
