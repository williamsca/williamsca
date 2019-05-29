---
layout: post
title: Unlike Game of Thrones, Most TV Shows Get Better Over Time
categories: Opinion
---

TV episode ratings remain roughly constant until the last 20% of the season, when they climb upwards.

The graphs below are created with data from IMDb ([^1]). I normalize the duration of each TV season to be 1, so that the 5th episode of a 10 episode season and the 7th episode of a 14 episode season are both assigned to a value of 1/2. I then compute the average rating given to episodes within 10 buckets.

![png]({{ site.baseurl }}/images/IMDb Episode Ratings.png)

The first bucket contains all episodes in the first tenth of their season, the second all episodes in the second tenth, and so on. The red series shows the simple average of all episode ratings in each bucket. The blue series shows the average weighted by the number of votes. Both tick upwards at the end of a season, but the upturn is much more pronounced in the blue series. This suggests that highly-rated episodes tend to get more votes.

The life of a show is more varied.

![png]({{ site.baseurl }}/images/IMDb Season Ratings.png)



[^1]: Retrieved from https://datasets.imdbws.com/ on 19 May 2019.