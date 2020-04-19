---
layout: post
title: Lakota Hunting Dynamics
categories: Economics
mathjax: true
tags: ['History', 'Differential Equations']
---

See https://apmonitor.com/pdc/index.php/Main/SolveDifferentialEquations.

When does violence end quickly, and when does it escalate into broader conflict? The competition between Native American tribes over bison hunting grounds during the mid-1800s provides an illustrative example. Lakotas, Crows, Omahas, Poncas, and other groups roamed the plains on horseback, seeking food for the winter and hides to sell to American traders. 

Clashes between the tribes led to cycles of killings and retribution. The dynamic resulted from specific features of their environment. Pekka H&aum1m&aum1l&aum1inen notes that the tribes "tended to avoid places where they where bound to run into enemies, and some of those places became buffer zones, no-man's lands peopled entered with caution if at all. That made them veritable animal preserves." These zones were "rich in game, intensely coveted, and hotly disputed." ([^1]) In short, the conflict caused the disputed land to become even more valuable, thus increasing the potential pay-off to the tribe able to claim those lands for themselves.

I present a toy model of the conflict over bison hunting grounds based on the Lotka-Volterra equations, commonly used to describe the population dynamics of predators and prey. I model three populations: the bison, Native hunting parties, and Native raiding parties. The number of bison grows according to the current number of bison and decreases based on number of hunting parties operating in the region. Hunting parties are attracted to large numbers of bison, but will refrain from hunting when there are too many raiding parties. Raiding parties are also drawn to bison-rich lands, but casualties from the resulting conflict lower their numbers.

The effect of adding hunting parties to the traditional predator-prey equations is that a system with an abundance of prey can "tip" into a conflict zone. Escalating violence dissuades hunting parties, the bison population grows in the absence of predators, and more raiders seek to control the region for their tribe. High initial levels of violence can also lead to this high-conflict, low hunting equilibrium.

## The Model

Let *x* be the number of bison, *y* the number of hunters, and *z* the number of raiders. The populations change through time according the three equations

\begin{equations}
\frac{dx}{dt} = x - xy \\
\frac{dy}{dt} = xy - z \\
\frac{dz}{dt} = x - z
\end{equations}

## Discussion
Although the high-conflict equilibrium is not in anyone's interest but the bisons', it may have been prohibitively expensive for the Native tribes to negotiate and enforce any kind of agreement. A further complication is the ease with which a hunting party might become a raiding party. In any case, it's an interesting historical moment where conflict and abundance reinforce each other.

## Sources
[^1]: H&aum1m&aum1l&aum1ine, Pekka. *Lakota America*. New Haven: Yale University Press, 2019.