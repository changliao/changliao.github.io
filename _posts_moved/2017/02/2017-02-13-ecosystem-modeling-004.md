---
 
title: 'Ecosystem modeling: challenges in simulating the dissolved organic carbon '
date: '2017-02-13T13:52:00.000-08:00'
permalink: /posts/2017/02/13/doc/
author: Chang Liao
tags:
- DOC
- GIS
modified_time: '2018-04-03T12:18:56.895-07:00'
---

Dissolved Organic Carbon (DOC) is an important carbon budget within ecosystem, especially for aquatic ecosystem including oceanic ecosystem.

Conventional DOC investigations mainly focus on DOC measurements in either soil profile or stream discharge. These measurements generally cannot explain where does DOC come from and how much DOC will be exported into the ocean. However, these studies have provided much insights of what biogeochemical processes are responsible for DOC dynamics.

So the question is can we quantitatively estimate DOC in terrestrial ecosystem based on existing knowledge.

I will provide more information on this topic in the coming months.

There are a few processes need to be simulated following the path of DOC.


![Figure 1](https://github.com/changliao/changliao.github.io/blob/main/_figure/stream_doc_transport.png?raw=true)


DOC production, consumption, and transportation on surface (mainly in litter);
DOC production, consumption and transportation in subsurface (mainly in soil);
DOC consumption and transportation in hydrological network;
In some scenarios, DOC transportation in groundwater movements.

For section 3, there are some widely established approach to simulate solute transportation in stream. For example, the MT3D-USGS provides the one-dimensional advection-dispersion equation to solve the transport in stream network.

Assuming we have a fully distributed watershed hydrology model, each stream segment is represented by a number of stream reaches.


In order to estimate DOC transport in each stream reach, we need an accurate estimate of stream flow and associated DOC concentration. Three or four type of flow play a role in this process.

Over land surface runoff
Soil zone inter flow
Open channel flow
Potential groundwater flow
These flow may have completely different type of proprieties including flow rate and travel time. 

And the spatial resolution also plays an important role since all time related processes must be linked to grid size.