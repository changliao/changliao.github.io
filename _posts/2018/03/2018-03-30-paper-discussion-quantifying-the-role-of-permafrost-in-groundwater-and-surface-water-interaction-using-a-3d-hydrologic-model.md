---
 
title: Quantifying the role of permafrost distribution in groundwater and surface
  water interactions using a three-dimensional hydrological model
date: '2018-03-30T17:07:00.000-07:00'
permalink: /posts/2018/03/paper-discussion-quantifying-the-role-of-permafrost-in-groundwater-and-surface-water-interaction-using-a-3d-hydrologic-model/
author: Chang Liao
tags:
- Groundwater Modeling
- MODFLOW
- Groundwater
modified_time: '2018-08-17T15:27:58.317-07:00'

---

Following my earlier post on promoting my research, this is the second study that I conducted in an attempt to understand the hydrology processes in high latitudes.

You are encouraged to read the first post for a background understanding of this study.

Let's cut to the chase, the title of this study is "Quantifying the role of permafrost distribution in groundwater and surface water interactions using a three-dimensional hydrological model", and you can access the paper through here or this.

In Arctic, snow and glacier are not the only players in the hydrology processes. Permafrost, the so called frozen soil is also an important player in both hydrology and carbon cycles.

There are several reasons for that:
It is frozen, so it could potentially release a lot of water in the warming climate;
Permafrost degradation can change the landscape, then both the carbon and water cycles will be affected;
Permafrost is like a barrier, it blocks interactions. Therefore, permafrost degradation will change the interactions between surface processes and deep processes.
While there are many aspects we can look into, we decided to look into the groundwater and surface water (GW-SW) interactions. Part of the reason is that we now consider permafrost in a three-dimensional domain and GW-SW interaction in directly affected by the spatial distribution of permafrost.

So we started with the standard groundwater flow model, this model is again from USGS, and it is called MODFLOW. More details can be found at here (https://water.usgs.gov/ogw/modflow/).

I would not get into details of how MODFLOW works. I do want to highlight a few important things.
The spatial domain is now broken into 3D zones, just like you cut your cheese cake. It has layers and pieces;
Water flows through the 3D domain and its speed depends on gradient and conductivity.

A zoomed view of the 3D setup is illustrated here:

Figure 1. The spatial discretization of the study domain.


If you look at the above figure, different cell/zone have different shape/size and hydrologic properties.

We have to know where permafrost is located and how deep they are. This is defined using the permafrost map:

Figure 2. The spatial distribution of permafrost and thickness.

Note that we also defined the stream network similar to my earlier study. In fact, it is a much complicated process than it appears to be.

We have to consider how groundwater interacts with stream in permafrost regions.

We first need to ask, is there permafrost under stream bed?
And we also have to ask whether there are permafrost next to stream.
In the end, we have to design the model structure to be very realistic and computationally friendly. For example, should the stream in the first layer or the second layer where permafrost rests? Can there be two-way interactions depending on stream stage?
Overall, the design is illustrated in Figure 3. 

Figure 3. The interactions between groundwater and stream water in permafrost regions.


We ran the simulation for 36 years driven by the surface infiltration and stream discharge. Some results are listed here:

Figure 4. The vertical groundwater flow between layer 1 and 2.

 This result demonstrates that most vertical flow occurs in permafrost-free zones, which is not surprising. It also implies that in the warming climate where there is less permafrost, the spatial distribution will definitely change.

Figure 5. Time series of groundwater and stream water interactions.

This result first confirms the base flow throughout the year fed by groundwater. It also shows the interactions in different time/season vary with stream conditions.

This study has demonstrated the permafrost plays an important role in GW-SW interactions. It also implies this relationship will change in the warming climate.

During this study, a IDL-based MODFLOW system was developed. Later on, this system is converted to Python-based, so you may try out MODFLOW simulation in any region without too much effort.