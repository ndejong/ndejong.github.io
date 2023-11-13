---
layout: post
title: Philippines Census + Geocoding + Google Maps API Data Mashup
author: Nicholas de Jong
---

Recently I noticed that the Philippine Statistics Authority (PSA) does an okay job of publishing their datasets openly 
and freely online.  This is notable because not all authorities in the Philippines are able to achieve this level of 
straight-forward openness.  You could even say it's quite impressive!

Quick links for the impatient:
 - [Interactive Census 2015 Heatmap](http://nicholasdejong.com/projects/philippines-data/heatmap/).
 - [Data wrangling code and resulting datasets](https://github.com/ndejong/philippines-data).

Among their online publications there are several reasonable articles discussing the data that came out of the 2015
census.  According to their [reports](http://psa.gov.ph/content/philippine-population-density-based-2015-census-population)
there were 225 people per sq/km in 2000 which has risen to a staggering 337 people sq/km in 2015.  Those sums work out
to a (linear) 2.73% population growth year on year, so it's little wonder the economy is growing so quickly here.

The reports also links to a MS Excel spreadsheet [2015 Population Density_web.xlsx](http://psa.gov.ph/sites/default/files/attachments/hsd/pressrelease/2015%20Population%20Density_web.xlsx) 
with population data per City/Municipality.  Unfortunately the spreadsheet is not well arranged to make easy use of the 
data (multiple values in single cells etc).  Because I wanted to augment this data with other data I needed to spend a 
fair bit of time manually massaging their dataset into [single columns](https://github.com/ndejong/philippines-data/blob/master/data/2015%20Population%20Density_web_clean-columns.csv)
and then [wrangling](https://github.com/ndejong/philippines-data/blob/master/tools/csvtojson.py) it into a nice clean 
JSON formatted structure that could more easily be used to combine with other datasets.

Using the [Google Maps Geocoding API](https://developers.google.com/maps/documentation/geocoding/intro) service it is 
possible to easily lookup the lat/long coordinates for each City/Municipality name listed in the census dataset which 
then is easy to fold back into the JSON formatted data.  See [insertgeocode.py](https://github.com/ndejong/philippines-data/blob/master/tools/insertgeocode.py)
for more detail.

The resulting [mashed together data](https://github.com/ndejong/philippines-data/raw/master/data/2015-population-density-w-google-geocode_20171218.json)
of the PSA 2015 Census data and the Google Maps Geocode data is now a lot more useful and allows us to create things 
like an [interactive heatmap](http://nicholasdejong.com/projects/philippines-data/heatmap/).

The code and datasets for this can all be found on my Github, here:
 - [https://github.com/ndejong/philippines-data](https://github.com/ndejong/philippines-data)

Also worth a mention is the Philippine Statistics Authority Openstat facility with plenty of useful stats and data about 
the Philippines:
 - [http://openstat.psa.gov.ph](http://openstat.psa.gov.ph)
