---
layout: post
title: Spatial Patterns of Firms with Monopsony Power (Part 2)
mathjax: true
categories: Economics
---

[Last time](https://williamsca.github.io/Monopsony1/), I introduced a simple spatial model with a single firm hiring workers across space. Now, I add a competitor and prepare to ask more interesting questions about monopsony and the labor market.

Code snippets from last time that are re-used are included at the top.

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy.optimize import minimize
```

```python
# Set the initial location for Ruby's factory
def plotFirms(points, labels):
    for point, label in zip(points, labels):
        plt.plot(point, visible=False)
        plt.annotate(label, xy=point)
        
    plt.axis([0, 1, 0, 1])
```

```python
# Initiate the unit square for plotting and simulating.
step = 0.003
x = np.arange(0, 1, step)
y = np.arange(0, 1, step)
xx, yy = np.meshgrid(x, y, sparse = False)
```

---

## A Competitor Arrives
Observing her enormous success, Ruby's old flatmate Harold decides to open his own factory. He locates his firm at (.75, .75).


```python
plotFirms([(0.5, 0.5), (.75, .75)], ["R", "H"])
```


![png]({{ site.baseurl }}/images/output_10_0.png)


Ruby will lose some of her workers to Harold. How many, though depends on the wages that they both choose to pay. Each worker compares his real wage at both firms, choosing to work at the factory where they earn the most after paying the cost of travel.

A worker chooses Ruby's factory whenever $$w_R - \beta * d_R \geq w_H - \beta * d_H$$ 

This is equivalent to $$w_R - w_H \geq \beta(d_R - d_H)$$


```python
# Numerically solve for the fraction of workers that a firm employs for a given wage.
def shareN(pos, pos_other, w, w_other):
    x1, y1 = pos
    x2, y2 = pos_other
    
    # calculate the distance each worker must travel to both firms
    d = np.sqrt((xx - x1)**2 + (yy - y1)**2)
    d_other = np.sqrt((xx - x2)**2 + (yy - y2)**2)
    d_diff = d - d_other
    
    # plot the dividing line between the firms
    if False:
        plotFirms([pos, pos_other], ["R", "H"])
        plt.contour(x, y, (w - d - (w_other - d_other)), [0])
        plt.draw()
    
    # workers choose the firm that maximizes W - c, where c is a function of distance
    # if her net wage is negative, the worker stays at home
    lambd = np.multiply(w - w_other > beta * d_diff, w - beta * d >= 0)
        
    # return the fraction of workers who choose this firm
    return np.sum(lambd) / (1 / step**2), lambd.flatten()

def plotWorkers(pos, pos_other, lambd, lambd_other):
    plotFirms([pos, pos_other], ["R", "H"])
    colors = ['red' if point == 1 else 
              'gray' if point_other == 1 else 
              'white' for point, point_other in zip(lambd, lambd_other)]
    plt.scatter(xx, yy, color=colors)
    plt.draw()
```

If Ruby and Harold both set $w = 2/3$, they will secure the workers shown below.


```python
shareR, lambdR = shareN((.5, .5), (.75, .75), .667, .667)
shareH, lambdH = shareN((.75, .75), (.5, .5), .667, .667)
plotWorkers((.5, .5), (.75, .75), lambdR, lambdH)
print('Ruby\'s share: ' + str(round(shareR * 100, 2)) + "%")
print('Harold\'s share: ' + str(round(shareH * 100, 2)) + "%")
```

    Ruby's share: 28.67%
    Harold's share: 23.7%
    


![png]({{ site.baseurl }}/images/output_14_1.png)


Ruby loses about 6 workers, and Harold picks up 24. In the next edition, I'll look at how Ruby and Harold compete to set their wages. Then, I'll explore whether Harold could have chosen a better location for his factory.

