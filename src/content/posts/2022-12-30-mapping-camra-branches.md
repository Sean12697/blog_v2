---
template: blog-post
title: Mapping CAMRA Branches
slug: mapping-camra-branches
date: 2022-12-30 18:56
description: In this blog post, I'll talk about how I map the Campaign for Real
  Ale (CAMRA) branches using Leaflet and data from the Office for National
  Statistics (ONS).
featuredImage: /assets/eiwu-n1xuaausf1.jpg
---
In this blog post, I'll talk about how I map the Campaign for Real Ale ([CAMRA](https://camra.org.uk/)) branches using [Leaflet](https://leafletjs.com/) and data from the Office for National Statistics (ONS). This blog post will receive later updates due to its immaturity and its currently unfit-for-purpose implementation. But I thought I'd write down what I'm doing now and how I want to change it to make it more accurate.

Having used various mapping frameworks, libraries, and postcode data in the past, in the form of [Leafletjs](https://github.com/Sean12697/Web-Mapping-Heatmap), [QGIS](https://twitter.com/Sean12697/status/1009847795115872257), and [Office for National Statistics Postcode Directory (ONSPD)](https://www.ons.gov.uk/methodology/geography/geographicalproducts/postcodeproducts) data, I stepped up to the plate when Graham Donning, a longtime CAMRA officer, emailed us a [Discourse](https://discourse.camra.org.uk/) (CAMRA's forum) post about a CAMRA project to map branch boundaries where Phil Vickers, [Administrative Office of Staffordshire](https://westmidlands.camra.org.uk/contacts), had already used QGIS to map the West Midlands region, comprising of 26 branches.

Based on this, I used a website called [Find that Postcode](https://findthatpostcode.uk/) to gather GeoJSON coordinate data, which uses data from the Office for National Statistics, Ordnance Survey, and Royal Mail, and cross-referenced the Office for National Statistics Postcode Directory to manually correlate wards and local authorities to CAMRA branches, which, with the help of a quick [NodeJS script](https://github.com/Sean12697/CAMRA-Branch-Map/blob/main/index.js) I wrote, enabled me to whip up a [quick example](https://camra-branches.netlify.app/) of the current 9 branches within the Greater Manchester region (with a few caviates and errors).

Before I aknolwedge the current errors in mapping certain branches, one of my plans is to gather what postcodes CAMRA considers under the authority of branches and use GeoJSON coordinate data from Mark Longair, who wrote a blog post on "[Open Data GB Postcode Unit Boundaries](https://longair.net/blog/2021/08/23/open-data-gb-postcode-unit-boundaries/)," which will integrate into my current codebase without too many adaptations.

For the Central Manchester branch, I am using an INACTIVE ward, [E05000697](https://findthatpostcode.uk/areas/E05000697.html), which was active from January 2009 to May 2018. For the Office for National Statistics Postcode Directory data, I could find no instances of data for North East Cheshire (for the High Peak, Tameside, and North East Cheshire branch), South Manchester (for the Stockport and South Manchester branch), or the entirety of the South-East Lancashire branch, the latter of which can be explained by the fact that it only existed as a [parliament constituency between 1868 and 1885](https://en.wikipedia.org/wiki/South_East_Lancashire_(UK_Parliament_constituency)), which fits within when CAMRA was first founded in 1971.

Current W﻿ebsite: <https://camra-branches.netlify.app/>

Current C﻿ode: <https://github.com/Sean12697/CAMRA-Branch-Map>