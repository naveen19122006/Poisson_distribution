# Exp No: 2-Fitting Poisson  distribution
# Date :05-10-2024
# Aim : 

To fit poisson distribution for the arrival of objects per minute from the feeder

# Software required :  

Python and Visual component tool

# Theory:

The Poisson distribution is the discrete probability distribution of the number of events occurring in a given time period, given the average number of times the event occurs over that time period.

![image](https://user-images.githubusercontent.com/104613195/166248326-fd042076-8b0b-40c4-8b11-1d8e8fcb74db.png)

 Conditions for Poisson Distribution:

1. An event can occur any number of times during a time period.
2. Events occur independently. I
3. The rate of occurrence is constant.
4. The probability of an event occurring is proportional to the length of the time period. 
 
# Procedure :

![image](https://user-images.githubusercontent.com/104613195/166251988-d0c53205-6080-4f7b-ae4c-398178586637.png)

# Experiment :

![image](https://user-images.githubusercontent.com/103921593/230282876-f4a5afbf-cac1-4648-a1b0-c78840638a8e.png)

# Program :

~~~
import numpy as np
from scipy.stats import chi2
from math import exp, factorial
L = [int(i) for i in input().split()]
N, M = len(L), max(L)
f = [L.count(i) for i in range(M+1)]
sf = sum(f)
mean = np.inner(range(M+1), [i/sf for i in f])
p, E, xi = [], [], []
print("X P(X=x) Obs.Fr Exp.Fr xi\n" + "-"*26)
for x in range(M+1):
    px = exp(-mean) * mean**x / factorial(x)
    exp_freq = px * sf
    chi_val = (f[x] - exp_freq)**2 / exp_freq
    p.append(px), E.append(exp_freq), xi.append(chi_val)
    print(f"{x:2} {px:.3f} {f[x]:5.2f} {exp_freq:6.2f} {chi_val:6.2f}")
cal_chi2 = sum(xi)
table_chi2 = chi2.ppf(0.99, df=M)
print("-"*26)
print(f"Calculated Chi-Square: {cal_chi2:.2f}")
print(f"Table Chi-Square at 1%: {table_chi2:.2f}")
print("Data can be fitted in Poisson Distribution at 1% LOS" if cal_chi2 < table_chi2 else "Data cannot be fitted in Poisson Distribution at 1% LOS")
~~~
 

# Output : 
![image](https://github.com/user-attachments/assets/e35706a7-d3af-431c-aed6-4b21a2e2ff3d)



# Results

The Poisson distribution is fitted for the objects arrived from feeder per minute and the data is tested using Chi-square test. 
 
