---
layout: post
title: Trends in Roman Epigraphy
categories: Economics
tags: ['Rome', 'Epigraphy']
---

Some observations and a plausible result from the inscription data.

The number of inscriptions produced in the Roman Empire peaks around the 2nd century AD. The increase is not driven by a single type of inscription; instead, all inscription types grow and shrink in absolute terms while maintaining similar proportions.

![png]({{ site.baseurl }}/images/20191211 Roman Epitaphs by Year.png)

The top five types of inscription -- epitaph, votive, honorific, owner/artist, and building/dedicatory -- account for more than 90% of all inscriptions in the sample. Votive inscriptions accumulate share from epitaphs until around 200 AD, at which point they fall back to their initial level of 10%. Otherwise, there is little variation over the centuries. 

An **epitaph** commemorates the dead. Common epitaphs include X and Y.

Votive 

## What Drives Epigraphic Writing?

A differences-in-differences model indicates that local epidemics shift epigraphic writing toward epitaphs. The usual qualifications apply, and moreover
1. I am not a professional econometrician
2. I know very little about how these data are collected and categorized
3. The accuracy of the dates and locations is subject to substantial uncertainty
4. Over fifty-year time intervals, any observed 'effect' will be overdetermined

Regardless, my story is straightforward: a higher mortality rate leads to increased demand for inscriptions that commemorate the dead. I will do my best to convince you.

The city of Rome suffered a series of epidemics in the latter half of the first century. ([^1]) These epidemics were local to the city, and do not appear to have spread to the rest of Italy. ([^2])

I compare the number of epitaphs uncovered in Rome to those from the rest of the Italian peninsula. Importantly, the comparison accounts for secular trends in the popularity of epigraphic writing, so that the difference must be the result of some cause(s) specific to Rome itself.

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
[^1] https://www.kyleharper.net/uncategorized/database-of-pestilence-in-the-roman-empire/
[^1] Ibid. Harper notes that "interregional events -- spreading beyond one province or so -- were rare before the outbreak of the Antonine Plague (165 AD). It seems unlikely that pandemics occurred but went unattested."
