---
 
title: 'Groundwater hydrology modeling: the relation among stream, groundwater and
  surface runoff'
date: '2016-08-30T13:17:00.003-07:00'
author: Chang Liao
tags:
- Stream Discharge
- Surface Runoff
- MODFLOW
modified_time: '2018-04-03T12:16:23.238-07:00'
thumbnail: https://1.bp.blogspot.com/-8JQRW2uMPMs/V8XgyuBNRrI/AAAAAAAAQ-g/YKG3XxhsxFcGBbYPKUwRofAnwHzvZhCmACPcB/s72-c/verification_scatter.png
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-628920856447294217
blogger_orig_url: https://changliao.blogspot.com/2016/08/groundwater-hydrology-modeling-003.html
---

Stream discharge is an important component in hydrology. Yet stream discharge is commonly studied in surface hydrology. In recent decades, it has been recognized that groundwater also interact with stream water throughout the year.

In groundwater modeling, stream routing is explicitly modeled as a groundwater boundary condition.
In general, several data are required for a successful simulation. Here I will only discuss a little bit related to water itself, to say, what kind of sink or source of the water in stream routing should be considered.

First, a stream segment/reach may received upstream discharge.

Second, a stream can also receive direct precipitation from the sky. But this term is usually omitted some the total amount may not be significant.

Third, a stream may also lose water from evaporation. Similar to direct precipitation, this term is usually omitted as well.

Forth, stream also receive later flow, it can be surface runoff and subsurface runoff (soil zone inter-flow). Many studies have shown that subsurface runoff account for more than 50% of the horizontal water flow. This term should be carefully estimated. However, surface runoff is also important during precipitation or snowmelt events.

Fifth, groundwater upwelling or stream leakage. This is the process stream water gain or lose water.

Below is an example of simulation stream discharge rates VS observed ones.

![Figure 1](https://github.com/changliao/changliao.github.io/blob/main/_figure/verification_scatter.png?raw=true)



So there are still some questions. 
First, in winter time, what should be well constrained since simulated discharge rates are much higher than observed rates?