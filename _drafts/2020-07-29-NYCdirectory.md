---
layout: post
title: The Geography of Work in New York City
categories: Economics
tags: ['Cities', 'Mapping', 'R', 'ggplot']
---

![png]({{ site.baseurl }}/images/20200729 City Directories Map (All Workers).png)

## Code

```R
rm(list = ls())
pacman::p_load(data.table, ggplot2, sf, httr, rgdal)

dir = ""

r <- GET('http://data.beta.nyc//dataset/0ff93d2d-90ba-457c-9f7e-39e47bf2ac5f/resource/35dd04fb-81b3-479b-a074-a27a37888ce7/download/d085e2f8d0b54d4590b1e7d1f35594c1pediacitiesnycneighborhoods.geojson')
nyc_neighborhoods <- readOGR(content(r,'text'), 'OGRGeoJSON', verbose = F)

dt <- readRDS(paste(dir, "derived/20200717 City Directories (1849-1880).Rds", sep = ""))
sample <- dt[!is.na(lat) & validUntil == 1880]

for (occ in c("laborer", "clerk", "tailor", "broker", "physician", "segar", "liquor", "carpenter", 
              "smith", "butcher", "grocer", "lawyer", "musician", "porter", "printer", "jeweler")) {
occupations <- c(occ)
occupations <- c(occupations[1], paste(occupations[1], "s", sep = ''))
sample2 <- sample[`$.data.occupation` %in% occupations] 

gg <- ggplot() + 
  geom_polygon(data = nyc_neighborhoods, aes(x=long,  y = lat, group = group), 
               color = "black") + # Draw NYC neighborhoods
  geom_point(data = sample2, aes(x = as.numeric(lon), y = as.numeric(lat), color = "red"), 
             size = .6, alpha = .25) + # Plot points
  coord_sf(xlim = c(-74.03, -73.96), ylim = c(40.69, 40.785)) + # Set map boundary
  labs(title = "New York City Directory", 
       subtitle = paste("1880 - ",  occupations[1], "s", sep = ''),
       caption = "Source: NY Public Library") +
  theme(panel.grid.major = element_blank(), panel.grid.minor = element_blank(),
        panel.background = element_blank(), legend.position = "none", 
        axis.title = element_blank(),
        axis.text = element_blank(), axis.ticks = element_blank(), # Remove legend and axes
        panel.border = element_rect(color = "black", fill = NA,  size = 2), # Add map border
        plot.title = element_text(vjust = -13, hjust = 0.05),
        plot.subtitle = element_text(vjust = -16, hjust = 0.04)) # Adjust title position
plot(gg)

ggsave(paste(dir, "output/maps/City Directories Map (", occupations[1], "s).png", sep=''))

}
```
