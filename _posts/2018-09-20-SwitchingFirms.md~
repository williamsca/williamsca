I consider the simple problem of when a worker should find a new job. It's puzzled me that people will stay at my firm for only two years and then move elsewhere, so this is the start of an explanation.<br />
<br />
The worker (call her Ruby) chooses when to switch between two firms operating in a competitive economy over a unit time period. Ruby's hourly wage at either firm is given by $$w_t = \lambda E_t$$ where $E_t$ is the amount of human capital she supplies in time period $t$, and $\lambda$ is the rental price paid for a single unit of human capital. For simplicity, I assume $\lambda = 1$ so that $w_t = E_t$.<br />
<br />
Ruby accumulates human capital on the job at a diminishing rate (I learned far more in the first week of my new job than in the most recent). For ease of exposition, let it grow according to the square root of time: $E_t = \sqrt{t}$. This human capital is either firm-specific or general. If Ruby chooses to jump ship to another firm at time $k \in [0, 1)$, she is able to bring with her $\alpha \sqrt{k}$ units of capital, where $\alpha \in[0, 1]$ is the fraction of general human capital she possesses. All of the idiosyncratic, firm-specific knowledge Ruby has acquired is lost when she transfers.<br />
<br />
If she does change firms, however, Ruby "jump-starts'' her accumulation of human capital due to the unfamiliar environment. Surrounded by new people and ideas, her own creativity and motivation are dramatically increased, so her stock of capital at time $t &gt; k$ is given by $\alpha \sqrt{k} + \sqrt{t - k}$. Thus, at any point in time we can compute Ruby's human capital:<br />
&nbsp;$$ E_t = \begin{cases} \sqrt{t}, &amp; 0 \leq t &lt; k \\ \alpha \sqrt{k} + \sqrt{t - k}, &amp; k \leq t \leq 1 \end{cases} $$<br />
Ruby wants to maximize her lifetime income $Y$ by choosing a time $k$ to switch firms (Ruby is more interested in her career than in a family right now):
\begin{align*} 
Y &amp;= \int_0^1 w_t \\
&amp;= \int_0^1 E_t \\
&amp; = \int_0^k \sqrt{t}~dt + \int_k^1\alpha \sqrt{k} + \sqrt{t - k}~dt \\
&amp;= \Big(\frac{2}{3} - \alpha\Big)k^{3/2} + \alpha \sqrt{k} + \frac{2}{3}(1-k)^{3/2}
\end{align*}

Taking the derivative and setting equal to zero gives the optimal time to switch as \begin{align}k = \frac{\alpha + 2 - \sqrt{-9\alpha^4 + 12\alpha^3 - 7 \alpha^2 + 4 \alpha + 4}}{9 \alpha^2- 12 \alpha + 8}\end{align}<br />
For $\alpha = 1$, this gives $k = 0.2$. In other words, this form of human capital production tells you to switch jobs no later than 20% of the way through your career. As $\alpha$ decreases, so do the lifetime gains from switching: $\dfrac{\partial Y}{\partial \alpha} = k^{1/2}(1-k) \geq 0$, and so too does the optimal time to switch.<br />
<br />
<b>Comments</b><br />
As a brief sanity check, I examined data on the median employee tenure.&nbsp; The BLS reports the median tenure among workers aged 25 to 34 as <a href="https://www.bls.gov/news.release/pdf/tenure.pdf">2.8 years</a>&nbsp;in 2016. Unsurprisingly, the median tenure of older workers aged 55 to 64 was almost four times larger (10.1 years). Exactly as this (admittedly simplistic) problem predicts, most job switching takes place at the beginning of a career. Of course, this behavior could have nothing to do with human capital and instead be the result of an imperfect matching process. <br />
<br />
In any case, the solution is more easily digested with a picture. If all of the worker's human capital is general ($\alpha = 1$), then she will choose to switch firms at $k = 0.2$. Her lifetime income is given by the area under the two lines below:<br />
<br />
![png](images/2010-09-20-SwitchingFirms-switch.png)
<br />
<br />
As $\alpha$ decreases, the worker will choose to switch firms earlier.

More broadly, I am interested whether a model based on this mechanism could predict where firms decide to locate. My tentative idea is that firms face a trade-off between leveraging monopsony power over the labor market and attracting workers who will eventually want to switch. The former will lead them to locate away from other firms, while the latter (I think) will cause them to clump together. What ultimately happens will depend on the value of $\alpha$ for a particular industry. If $\alpha$ is large, then workers will be drawn to areas where they can easily switch between firms, rewarding dense agglomerations. If it is small, then firms will be able to remain far apart and pay lower wages. The human capital cost of switching firms will prevent workers from demanding higher wages by threatening to move.<br />
