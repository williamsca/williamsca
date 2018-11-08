---
layout: post
title: Data on Washington, DC Property Values
categories: Datasets
---

I put together a dataset of housing prices in DC. The data include geographic information (address, neighborhood, and sub-neighborhood), [use code](https://otr.cfo.dc.gov/sites/default/files/dc/sites/otr/publication/attachments/Use%20codes.pdf), sale price, recordation date, and the assessed value of the property.

The data come from scraping the [DC Office of Tax and Revenue website](https://www.taxpayerservicecenter.com/RP_Search.jsp?search_type=Assessment). The data span from 1999 through 2017.

You can download the data [here](https://raw.githubusercontent.com/williamsca/williamsca.github.io/master/data/DCPropertyAssessments.zip).

A caveat to these data is that the sales are not necessarily arm's length. Thus, a number of the observations have suspiciously low sale prices and do not reflect market transactions.
