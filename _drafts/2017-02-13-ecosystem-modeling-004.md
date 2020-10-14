---
layout: post
title: 'Ecosystem modeling: challenges in simulating the dissolved organic carbon '
date: '2017-02-13T13:52:00.000-08:00'
author: Chang Liao
tags:
- DOC
- GIS
modified_time: '2018-04-03T12:18:56.895-07:00'
thumbnail: https://4.bp.blogspot.com/-0_rTWSzwNOs/WMLNNFZHE9I/AAAAAAAAVZo/pMCJ7kSbAoQ7R9rhfGBUMuHHxACJxKu0ACLcB/s72-c/stream_transport.jpg
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-6414558098074632225
blogger_orig_url: https://www.changliao.us/2017/02/ecosystem-modeling-004.html
---

Dissolved Organic Carbon (DOC) is an important carbon budget within ecosystem, 
especially for aquatic ecosystem including oceanic ecosystem. 

Conventional DOC investigations mainly focus on DOC measurements in either 
soil profile or stream discharge. These measurements generally cannot explain 
where does DOC come from and how much DOC will be exported into the ocean. 
However, these studies have provided much insights of what biogeochemical 
processes are responsible for DOC dynamics. 

So the question is can we quantitatively estimate DOC in terrestrial ecosystem 
based on existing knowledge. 

I will provide more information on this topic in the coming months. 

There are a few processes need to be simulated following the path of DOC. 

1. DOC production, consumption, and transportation on surface (mainly in 
litter); 
1. DOC production, consumption and transportation in subsurface (mainly in 
soil); 
1. DOC consumption and transportation in hydrological network; 
1. In some scenarios, DOC transportation in groundwater movements. 
<div> 
<div>For section 3, there are some widely established approach to simulate 
solute transportation in stream. For example, the MT3D-USGS provides the 
one-dimensional advection-dispersion equation to solve the transport in stream 
network. 
Assuming we have a fully distributed watershed hydrology model, each stream 
segment is represented by a number of stream reaches. 
<div class="separator" style="clear: both; text-align: center;">[<img 
border="0" height="351" 
src="https://4.bp.blogspot.com/-0_rTWSzwNOs/WMLNNFZHE9I/AAAAAAAAVZo/pMCJ7kSbAoQ7R9rhfGBUMuHHxACJxKu0ACLcB/s400/stream_transport.jpg" 
width="400" 
/>](https://4.bp.blogspot.com/-0_rTWSzwNOs/WMLNNFZHE9I/AAAAAAAAVZo/pMCJ7kSbAoQ7R9rhfGBUMuHHxACJxKu0ACLcB/s1600/stream_transport.jpg) 
In order to estimate DOC transport in each stream reach, we need an accurate 
estimate of stream flow and associated DOC concentration. Three or four type 
of flow play a role in this process. 

1. Over land surface runoff 
1. Soil zone inter flow 
1. Open channel flow 
1. Potential groundwater flow 
<div>These flow may have completely different type of proprieties including 
flow rate and travel time. <div> 
<div>And the spatial resolution also plays an important role since all time 
related processes must be linked to grid size.<div> 
<div> 