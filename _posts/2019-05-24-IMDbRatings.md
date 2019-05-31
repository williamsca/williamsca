---
layout: post
title: Unlike Game of Thrones, the Season Finale is Usually the Best Episode
categories: Opinion
---

TV episode ratings remain roughly constant until the last 20% of the season, when they climb upwards.

The graphs below are created with data from IMDb ([^1]). I normalize the duration of each TV season to be 1, so that the 5th episode of a 10 episode season and the 7th episode of a 14 episode season are both assigned to a value of 1/2. I then compute the average rating given to episodes within 10 buckets.

![png]({{ site.baseurl }}/images/IMDb Episode Ratings.png)

The first bucket contains all episodes in the first tenth of their season, the second all episodes in the second tenth, and so on. The red series shows the simple average of all episode ratings in each bucket. The blue series shows the average weighted by the number of votes. Both tick upwards at the end of a season, but the upturn is much more pronounced in the blue series. This suggests that highly-rated episodes tend to get more votes.

I expected this series to look U-shaped. If television producers could allocate quality, then strong episodes at the start of a season might serve to hook audiences, and strong episodes at the end might increase the liklihood that they watch the next season. The middle episodes could just be filler.

Evidently, however, it takes time for a show to hit its stride over the course of a season. If the increase in quality came from the supply side -- actors building chemistry, writers getting to know their characters -- then one would expect the trend to be relatively uniform.

Instead, the rating jumps only in the final fifth of the season. It seems that audiences just like endings.

---

The life of a show is more varied. I follow the same procedure in the graph below, but the dots now represent the average rating of a *season* over the lifetime of the show. 

![png]({{ site.baseurl }}/images/IMDb Season Ratings.png)

The first and last seasons are rated slightly worse than those in the middle. Strangely, while audiences tend to prefer the last episode in a season, they are less happy with the last season of a show. The Game of Thrones writers may have been doomed from the start.

[^1]: Retrieved from https://datasets.imdbws.com/ on 19 May 2019.