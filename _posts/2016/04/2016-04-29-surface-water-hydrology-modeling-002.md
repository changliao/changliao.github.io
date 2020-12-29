---
layout: post
title: 'Surface water hydrology modeling: scaling issue in Precipitation Runoff Modeling
  System(PRMS)'
date: '2016-04-29T21:28:00.000-07:00'
author: Chang Liao
tags:
- CRT
- PRMS
modified_time: '2018-04-03T12:15:56.911-07:00'
thumbnail: https://4.bp.blogspot.com/-4-HesCLrZ2I/VD88vBJ2alI/AAAAAAAAZOg/-qprjUn4ttk/s72-c/crv.png
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-2008361363063983910
blogger_orig_url: https://changliao.blogspot.com/2016/04/surface-water-hydrology-modeling-002.html
---

Grid-based HRU network for stream routing in PRMS could be convenient for several reasons.
Apparently the ideal data structure as matrix could be one of them.But it is not always the case if the scaling issue is not well handled.
Below is an example how the scale issue could be a potential problem for the simulation framework.
First, I would like to introduce the CRT. Cascade Routing Tool (CRT) is a computer application for watershed models that include the coupled Groundwater and Surface-water FLOW model GSFLOW and the Precipitation-Runoff Modeling System (PRMS). More information could be found at (http://water.usgs.gov/ogw/CRT/)
The example run result is listed as:

![Figure 1](https://github.com/changliao/changliao.github.io/blob/main/_figure/crt_cascade.png?raw=true)




Read the instruction of CRT and you will easily understand the legend/label of the above result.The stream line datasets used here is vector and the grid resolutions in horizontal are both 100 meters.
The next step, the subbasin was delineated using stream line and DEM datasets. Note that in these operations, the resolution of DEM is 10 meters instead of 100 meters. The result is as follow:



![Figure 2](https://github.com/changliao/changliao.github.io/blob/main/_figure/subbasin.png?raw=true)

We are already able to see the potential problem in the above result. The stream line may lies in one grid but the majority of that grid contribute to another subbasin. Could that be a problem? Then, in order to determine which HRU or grid contribute to which stream segment, the rasterization operation is conducted on the subbasin feature, which is the result from watershed delineation.
We have:


![Figure 3](https://github.com/changliao/changliao.github.io/blob/main/_figure/subbasin2.png?raw=true)


The algorithm of rasterization most likely classify grids based on area. And therefore the stream line would cut into neighbors in some cases.
As a result, one HRU must be 8-neighbor connected instead of 4 if the subbasin is inter connected, which is not true for CRT algorithm.
So what is the most practical and robust method to address this problem?