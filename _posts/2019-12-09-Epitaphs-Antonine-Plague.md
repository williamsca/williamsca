---
layout: post
title: Trends in Roman Epigraphy
categories: Economics
tags: ['Rome', 'Epigraphy']
---

## What Drives Epigraphic Writing?

The demand for epitaphs will depend on several
conditions: how many Romans died, their wealth, and the
popularity of inscribed epitaphs relative to other forms of
commemoration. It follows that periods of high
mortality will be associated with more epitaphs. When the death rate
is high, there will be relatively more subjects for epitaphs, and -- in a Malthusian
economy -- their surviving relatives will have extra income available
for "luxury" purchases that signal their wealth, like fancy
inscriptions. ([^1])

The city of Rome suffered a series of epidemics in the latter half of
the first century. ([^1]) Tacitus writes of Rome in 65 AD([^2]): 

> a terrible plague was sweeping away all classes of human beings
> without any such derangement of the atmosphere as to be visibly
> apparent. Yet the houses were filled with lifeless forms and the
> streets with funerals. Neither age nor sex was exempt from
> peril. Slaves and the free-born populace alike were suddenly cut
> off, amid the wailings of wives and children, who were often
> consumed on the very funeral pile of their friends by whom they had
> been sitting and shedding tears.

Two further plagues followed in 77 AD and 79/80 AD. These epidemics were local to the city, and
do not appear to have spread to the rest of Italy. ([^2]) Under
reasonable assumptions about the demographic consequences of these
plagues, it is plausible that they had a measurable effect on the
demand for epitaphs (see appendix for more details). Consistent
with this story, the number of epitaphs dating to this period from Rome
jumps sharply relative to those from the rest of the Italian
peninsula:

![png]({{ site.baseurl }}/images/20191216 Roman Epitaphs by Year (Rome
& Italy).png)

The chart shows the total number of inscriptions dating to each half-century
beginning in 50 BC until 450 AD, separately for the city of Rome and the rest of
the Italian provinces. The two series track each other
in every period except for 50 - 100 AD. A heightened mortality rate in
Rome during these years is the best explanation for the
divergence; other explanations come up short.

### What if the mortality rate in Italy fell?
If so, why did it not also fall in Rome itself? A localized increase
in mortality seems more likely that a regional decrease that skipped
over Rome, though the latter is no doubt possible.

### Could the popularity of epitaphs have increased in Rome?
It would be strange if the popularity of epitaphs did not spill
over from Rome to the rest of Italy. It possible that fads originating
in Rome took time to spread throughout the peninsula, though a delay
on the order of 50 years seems implausible. 

A related possibility is that the popularity of epitaphs increased among
a class of the population who were more likely to reside in Rome. For
instance, if a larger share of Rome's population consisted of slaves
relative to Italy as a whole, and if the popularity of epitaphs among
freed slaves increased starting in
50 BC, then epitaphs in Rome would increase.

TODO: check whether the % of epitaphs referring to freedmen increases
in Rome relative to Italy during these years.

### What if the population or wealth of Rome increased?
If this were the case, other types of inscription should also increase
in Rome. However, this does not happen. Honorifics are the second most
common type of inscription in Italy, and there is little difference in
the trends until 200 AD.

![png]({{ site.baseurl }}/images/20191217 Honorifics by Year (Rome
& Italy).png)

Building/dedicatory inscriptions similarly track each other across the
sample period.

### Final Thoughts
I don't want to overstate my case. I know very little about how
these data are collected and categorized. The accuracy of the dates
and locations is subject to substantial uncertainty. And over a
fifty-year time interval, any observed 'effect' will be
overdetermined.

## Appendix

### Demographic Simulations
TODO

### General Trends in Inscriptions

The number of inscriptions produced in the Roman Empire peaks around the 2nd century AD. The increase is not driven by a single type of inscription; instead, all inscription types grow and shrink in absolute terms while maintaining similar proportions.

![png]({{ site.baseurl }}/images/20191211 Roman Epitaphs by Year.png)

The top five types of inscription -- epitaph, votive, honorific,
owner/artist, and building/dedicatory -- account for more than 90% of
all inscriptions in the sample. Votive inscriptions accumulate share
from epitaphs until around 200 AD, at which point they fall back to
their initial level of 10%. Otherwise, there is little variation over
the centuries. 


## Code

```stata
local scatter_options "msize(small) c(1) yaxis(2) lpattern(-) lwidth(thin)" 
twoway (bar tot year_bucket, fcolor(ltbluishgray) fintensity(inten60) lcolor(black) ytitle("") ///
	ylabel(0 12000, nogrid) yscale(off) yaxis(1) barwidth(50)) || ///
		(scatter frac year_bucket if type_of_inscription_code == 9, `scatter_options') || ///
		(scatter frac year_bucket if type_of_inscription_code == 22, `scatter_options') || ///				  (scatter frac year_bucket if type_of_inscription_code == 5, `scatter_options') || ///		   
		(scatter frac year_bucket if type_of_inscription_code == 10, `scatter_options') || ///
		(scatter frac year_bucket if type_of_inscription_code == 17, `scatter_options') || ///
		(scatter lab year_bucket, msym(none) mlab(tot) mlabpos(12) mlabcolor(gs5) mlabsize(small)), ///		 graphregion(color(white)) bgcolor(white) xlabel(-50(50)400) ///
		legend(order(3 "Epitaph" 4 "Votive" 5 "Building" 6 "Honorific" 7 "Owner/Artist") ///
			symxsize(10) cols(5) region(style(none))) ///
		title("Inscriptions peak in 150 AD, but their relative quantities are roughly constant", ///
			size(medium) pos(11) color(black)) ///
		subtitle("Total inscriptions and the shares of the five most common types, by year", ///
			size(small) pos(11) color(gs8)) ///
		xtitle("Year") ytitle("Share of All Inscriptions", axis(2)) ///
		note("{bf:Source:} Epigraphic Database Heidelberg, retrieved from https://edh-www.adw.uni-heidelberg.de/home on 7/17/2019." ///
			 "{bf:Note:} Inscriptions graphed according to an equal probability of dating to any year within their date range.", ///
			 color(gs7) size(vsmall))
```

## Sources
[^1] Similarly, the Black Death "concentrated wealth, often
substantial family fortunes, in fewer and younger hands.... Even with
a reduced population, the gross volume of luxury goods manufactured
and sold rose." See Rout, David. "The Economic Impact of the Black
Death". *EH.net Encyclopedia*, edited by Robert Whaples. July
20, 2008. http://eh.net/encyclopedia/the-economic-impact-of-the-black-death/
[^1] Harper, Kyle. "Database of Pestilence in the Roman
Empire". *KyleHarper.net*, August 24, 2017, https://www.kyleharper.net/uncategorized/database-of-pestilence-in-the-roman-empire/
[^2] Tacitus Ann 16.13. From *Complete Works of Tacitus*. Alfred John Church. William Jackson
Brodribb. Sara Bryant. edited for Perseus. New York: Random House,
Inc. reprinted in 1942.
[^2] Harper, Kyle. "Database of Pestilence in the Roman
Empire". Harper notes that "interregional events -- spreading beyond one province or so -- were rare before the outbreak of the Antonine Plague. It seems unlikely that pandemics occurred but went unattested."
