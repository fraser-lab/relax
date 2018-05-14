Relax
=====

Summary:
-----
A small tool for calculating non-linear relaxation fits from arbitrary time-resolved experiments

Authors:
-----
Ben Barad

Available Relaxation Kinetics Functions:
-----
* Single Step Relaxation: y = A*(1-e<sup>-Bx</sup>)+C
* Two Step Relaxation: y = A*(1-e<sup>-Bx</sup>)+C*(1-e<sup>-Dx</sup>)+E
* Three Step Relaxation: y = A*(1-e<sup>-Bx</sup>) + C*(1-e<sup>-Dx</sup>) + E*(1-e<sup>-Fx</sup>) + G

Example Usage:
-----
```python
import numpy as np
from relax import relaxation_fit, single_step_relaxation

x = [1,2,5,10,15,25,35,60,90, 200, 500, 1000, 10000, 1000000, 10000000000]
y = [25*(1-np.exp(-5*i))+2 for i in x]

parameters, covariances, y_calc = relaxation_fit(x, y, relaxation_function = single_step_relaxation, initial_guess=[18, 11, 10])

print(parameters) 
# Ideally this should converge to 25., 5., 2. for this example - more data points will improve convergence.

```

Requirements:
-----
* Python >= 3.6
* Numpy
* Scipy
