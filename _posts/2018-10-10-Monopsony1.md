---
layout: post
title: Spatial Patterns of Firms with Monopsony Power (Part 1)
mathjax: true
categories: Economics
---

The economist Harold Hotelling pointed out that two store owners will naturally locate their stores [right next to each other](https://en.wikipedia.org/wiki/Hotelling%27s_law) so that they will appeal to the largest possible number of buyers. 

If the store owners are competing to hire workers, however, they may want to keep some distance between themselves. In this post, I develop and simulate a simple model with one firm hiring workers who are uniformly distributed across a unit square. Later posts will extend the model to include more firms, who will avoid close proximity, and so I will test various mechanisms that incentivize the firms to clump together.

All the math in this first section can safely be ignored. The story is quite simple and can be comprehended from the pictures and text.

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy.optimize import minimize
```

## The Dawn of Industry
A lone entrepreneur (call her Ruby) arrives in a vast wilderness, uniformly populated by farming homesteads. As the bearer of advanced industrial technology, Ruby promptly sets up a factory and hires some locals. She locates her factory directly in the center of the region.


```python
# Set the initial location for Ruby's factory
def plotFirms(points, labels):
    for point, label in zip(points, labels):
        plt.plot(point, visible=False)
        plt.annotate(label, xy=point)
        
    plt.axis([0, 1, 0, 1])
    
plotFirms([(0.5, 0.5)], ["R"])
```


![png]({{ site.baseurl }}/images/output_2_0.png)


---
Ruby is eager to maximize her profits. She can sell her widgets back East for 1 gold each, and each worker she hires can produce 1 widget. Thus, her profit is given by $\prod = N_w * (1 - w)$, where $N_w$ is the number of workers she can hire at wage $w$. 


```python
# Calculate Ruby's (negative) profit
def profit(w, N_w):
    return -(N_w * (1 - w))  
```

The farmers in the region can always obtain a wage of zero by working in the field. They incur travel costs $\beta$ that are linear in the distance to Ruby's factory, so they will choose to work whenever $$w - \beta \sqrt{(x_n - 0.5)^2 + (y_n - 0.5)^2} \geq 0$$

The factory's "draw area" is the circle $\frac{w^2}{\beta^2} = (x - 0.5)^2 + (y - 0.5)^2$. The area of this circle is $A = \pi * \frac{w^2}{\beta^2}$. Note that $A$ is also the fraction of the unit square contained by $A$.

If $N$ is the total number of workers in the region, then Ruby will hire $N_w = N * A = N * \pi * \dfrac{w^2}{\beta^2}$ workers. Her maximization problem is $$\max_w\{N * \pi * \dfrac{w^2}{\beta^2} * (1 - w)\}$$ 

Some calculus gives that Ruby will maximize profit at $w = \frac{2}{3}$. If $\beta = 2$, then she will hire $100 * \pi * \frac{4/9}{4} \approx 35$ workers.


```python
# Initiate the unit square for plotting and simulating.
step = 0.003
x = np.arange(0, 1, step)
y = np.arange(0, 1, step)
xx, yy = np.meshgrid(x, y, sparse = False)
```


```python
# Draw factory's "draw area"
beta = 2
def shareWorkers(pos, w, plot=0):
    x1, y1 = pos[0]
    d = np.sqrt((xx - x1)**2 + (yy - y1)**2)
    
    if plot:
        plotFirms(pos, ["R"])
        plt.contour(x, y, (w - beta * d), [0])
        
    return np.pi * w**2 / beta**2

A = shareWorkers([(0.5, 0.5)], .6667, plot=1)
print(A)
```

    0.3491007578565704
    


![png]({{ site.baseurl }}/images/output_7_1.png)



```python
# Calculate Ruby's profit
N = 100
N_w = N * A
profit(.6667, N_w)
```




    -11.635528259359493



With 35 employees, Ruby's profit is $35 - (2/3 * 35) \approx 11.64$, as above. (Ignore the minus sign. Scipy.optimize provides an algorithm to minimize a function, so we will later maximize profit by minimizing negative profit.) Next time, I will introduce some competition.
