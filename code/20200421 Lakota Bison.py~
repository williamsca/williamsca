import numpy as np
from scipy.integrate import odeint
import matplotlib.pyplot as plt

def model(X, t, alpha):
    x = X[0]
    y = X[1]
    z = X[2]

    dxdt = x - x*y
    dydt = x*y - y*(z**alpha)
    dzdt = x - z
    dZdt = [dxdt, dydt, dzdt]
    return dZdt

# initial condition
X0 = [.2, .8, .3]
alpha = 1

# set T
T = 20
n = T*10+1
t = np.linspace(0, T, n)

# store solution; record initial conditions
x = np.empty_like(t)
y = np.empty_like(t)
z = np.empty_like(t)
x[0] = X0[0]
y[0] = X0[1]
z[0] = X0[2]

# solve ODE
for i in range(1, n):
    
    # solve for the next time step
    tspan = [t[i-1], t[i]]
    X = odeint(model, X0, tspan, args = (alpha,))
    
    # store solution for plotting
    x[i] = X[1][0]
    y[i] = X[1][1]
    z[i] = X[1][2]

    # next initial condition
    X0 = X[1]

# plot results
plt.rcParams['font.sans-serif'] = 'Garamond'
plt.rcParams['font.family'] = 'sans-serif'
plt.plot(t, x, color='DarkGoldenRod', label = 'x(t)')
plt.plot(t, y, color='DarkGreen', label = 'y(t)')
plt.plot(t, z, color='Crimson', label = 'z(t)')
plt.ylabel('Population', fontsize = 13)
plt.xlabel('Time', fontsize = 13)
plt.title('Hunters Everywhere, But Few Bison', fontsize = 16)
plt.legend(loc='best')
plt.show()
