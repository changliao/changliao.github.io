---
layout: post
title: 'Integrated groundwater and surface water modeling: topography effects'
date: '2015-10-09T08:16:00.000-07:00'
author: Chang Liao
tags:
- MODFLOW
modified_time: '2018-04-03T12:14:25.408-07:00'
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-3709873869874227851
blogger_orig_url: https://changliao.blogspot.com/2015/10/integrated-groundwater-and-surface-water-04.html
---

This is a talk highly related to my last post on spatial discretization of 
numerical simulation. 

In groundwater modeling such as MODFLOW, topography effects are very common 
and yet less discussed. 

There are a few distinguishable differences between low land groundwater and 
high land groundwater system. First, heads at high elevation are usually 
higher, this is observed since water table usually follow topography even not 
strictly. Second, variances in heads in high elevation may be insensitive to 
changes in forcing, For example, the low land always receive the most water 
(even flood) and droughts. Third, generally, water movements in high elevation 
are much slower due to low K values. 

With consideration of these differences, it is easier to understand a few 
critical phenomena in groundwater modeling. 

First, groundwater system is seldom in steady state. The best estimation, 
however, could be within winter time when stream base flow is minimal. At this 
stage, only limited groundwater flow and infiltration from snow melt under 
pressure at high elevation are driving the whole groundwater and surface water 
flow system. The K values are so small that the feed could last for several 
months even into the summer time. 

Even with the steady state, it is still a challenge to produce the best 
initial heads after SS simulation. This is because of the sensitivity of high 
land groundwater system. Nearly all terms (K and infiltration rate, etc.) are 
small in magnitude, which means the system is highly sensitive to driving data 
(Thinking of climate change!!!). In order to maintain the constant storage, 
both in flow and out flow must be offset exactly! This is not just required 
for one pixel, but for all. Therefore the spatial resolution is critical here. 
If differences in adjacent heads exceed a certain range, it would drive the 
flow. For example, at high elevation region, adjacent cells have an elevation 
difference of 100m, which in reality surface is continuous but we have no 
choice to discretize it. In this case, in order to maintain the storage, the 
groundwater simulation may get differences in heads around 10m, which means 
one of them must level up or level down. So as a result, at least one of the 
simulated head is far below the surface elevation, which mismatch the 
observation. 

You would think if the resolution is 1m, if might be able to resolve this 
issue. However, computational demand will increase exponentially as resolution 
increases since this is 3D simulation. Also, data availability for other 
inputs must also be considered. Therefore, a compromise of resolution is 
needed. There are a few studies which use 100m (or even less) in small 
catchments. It could potentially improve the simulation accuracy but care must 
be taken to avoid unrealistic assumptions. 

Some also think, why don't we assign the initial head for all pixels? But how 
and what to assign? 

A lot of simulations use the well measurements as initial heads, which might 
be a good solution. But again, these type of data are always absent in high 
elevation regions due to inaccessibility. 

If streams are forms (even in winter), then surface runoff needs to be 
considered. But how? With surface water modeling. However, a typical surface 
water simulation starts around October, 1st,which is not exactly winter time 
in most regions. 

So here comes the scenario, if we start simulation from October, we may be 
able to simulate the infiltration rate dynamics and snow accumulation storage 
for winter time.Without a steady simulation, it is usually encountered with 
the problem with initial heads as well. Since TR simulation is highly 
dependent upon initial heads, the initial condition could affect the low land 
heads.As heads at high elevations remain high throughout the year, they will 
constantly flow following the gradient. Even though the low K values means the 
recharge to low land is small, it may shape the spatial pattern through flow 
system. 

After all, a promising way seems to be shaped: 

Pay attention to the resolution, the higher you can afford, the better, when 
you have the topography effects. 

A reasonable TR simulation starting with assumption on initial heads. The TR 
should run for a few water years until the surface process is close to 
observations (snow cover, discharge and infiltration, etc.). Then use these 
data to drive the groundwater model or coupled surface water-groundwater 
model. It is then possible to recreate the real SS simulation and others 
parameters. 

Welcome your comments, as always! 