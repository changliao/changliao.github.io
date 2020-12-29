---
layout: post
title: 'Integrated groundwater and surface water modeling: the finite element'
date: '2015-09-30T17:58:00.000-07:00'
author: Chang Liao
tags:
- MODFLOW
- PRMS
- SWAT
modified_time: '2018-04-03T12:13:55.089-07:00'
thumbnail: https://1.bp.blogspot.com/-OG1THPjVUx8/Vg1Fx0mMSeI/AAAAAAAALcE/ShlpSnmcW5Q/s72-c/D8.png
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-7788391884478680973
blogger_orig_url: https://changliao.blogspot.com/2015/09/integrated-groundwater-and-surface-water-01.html
---

Numerical simulations of groundwater and surface water movements are 
essentially dealing with the finite element in the spatial domain. 
<div>This finite element could be in a variety of forms including cubic, node 
and pixel. This depends upon the methods used to conceptualize this physical 
world.<div>The dimension of these finite elements varies as well since they 
are characterized by spatial resolution.<div>For spatial distributed 
hydrologic models, regardless of groundwater or surface water models, these 
finite elements interact with each other governed by derived continuity 
equations such as Richard's equation.<div> 
<div>Consequently, in most groundwater models, the finite element would 
interact with 6 neighbors in a 3D model. However, in a spatial distributed 
surface water model, the finite element may interact with 8 neighbors or 4 
neighbors. Even within one model, different assumptions are possibly made in 
different scenarios. <div>Then the question is are these assumptions 
contradict each other? Or why it should have 8 neighbor instead of 4 and so 
on?<div> 
<div>Let's first take a look at some real life examples using some existing 
models. For groundwater modeling, in MODFLOW, which is one of the most widely 
used groundwater models, each finite element can interact with 4 horizontal 
neighbors and 2 vertical neighbors. So there are 6 neighbors in total. 
Similarly for surface modeling, in SWAT/PRMS, each finite element can interact 
with 4 or 8 neighbors. <div> 
<div>A close look at some watershed delineation process will unveil that even 
though water flow direction is predefined using digital elevation model (DEM) 
aspect, flow itself in fact is distributed in more than one direction using 
fractions. <div> 
<div>An important reference of how this flow direction is produced is 
explained 
here:<div>[http://help.arcgis.com/EN/arcgisdesktop/10.0/help/index.html#//009z00000063000000.htm](http://help.arcgis.com/EN/arcgisdesktop/10.0/help/index.html#//009z00000063000000.htm)<div> 
<div>Now it looks plausible that 8 neighbor would better describe the flow 
path than 4 neighbors. But why?<div>And why this is not implemented in 
groundwater modeling? Also what plays a factor in these assumptions? (spatial 
resolution?) 

The following figure is retrieved from watershed delineation process. So will 
it become an issue that there are a few pixels that belong to 8 neighbor, but 
not 4 neighbor? 
<div class="separator" style="clear: both; text-align: center;">[<img 
border="0" height="521" 
src="https://1.bp.blogspot.com/-OG1THPjVUx8/Vg1Fx0mMSeI/AAAAAAAALcE/ShlpSnmcW5Q/s640/D8.png" 
width="640" 
/>](http://1.bp.blogspot.com/-OG1THPjVUx8/Vg1Fx0mMSeI/AAAAAAAALcE/ShlpSnmcW5Q/s1600/D8.png)Certainly 
in surface water hydrology, water flow can be like this. But for groundwater 
modeling, this is usually not allowed if this type of pixels are on the 
boundary. <div> 
<div>In fact, some watershed utilities indeed use 4 neighbors instead of 8 
neighbors.<div>Complexity doesn't always performance better than simplicity. 
But sometimes complexity is a compromise between simplicity and 
limitation.<div> 
<div>No matter what assumptions or strategies are made, govern equation only 
cares about mass balance and energy balance. As long as these laws are not 
violated, the models are usually reliable. However, this is also a common 
issue in integrated hydrologic model. And as our model continues to increase 
in processes and resolution, the possibility of encountering this type of 
issue increases as well.<div> 