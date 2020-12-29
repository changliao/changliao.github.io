---
 
title: 'Surface water hydrology: a reach based approach'
date: '2017-03-12T20:44:00.001-07:00'
author: Chang Liao
tags:
- Stream Discharge
modified_time: '2018-04-03T12:20:13.221-07:00'
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-432624172299537449
blogger_orig_url: https://changliao.blogspot.com/2017/03/surface-water-hydrology-005.html
---

In surface watershed hydrology, stream network is usually represented by a 
number of connected stream segments. Outflow from a upstream is then routed to 
its downstream as inflow at certain time step. 

One of the important parameters to determine how long the outflow will arrive 
the next segment is defined using the travel time. The manning equation is 
usually used to calculate the open channel flow velocity and rate. 

In a typical surface hydrology model such as SWAT or PRMS, these parameters 
are either prepared or calculated for the model. However, there may be great 
uncertainty for high-spatial resolution simulations. 

For example, a segment travel time may be far less than one hour and a daily 
time step simulation cannot accurately capture the peak flow at all. 

In some scenarios, we are interested in the spatial distribution of flow rate, 
flow velocity, and other dissolved components (DOC/DIC) in the stream, 
therefore, a segment based approach is inappropriate. 

An alternative way to simulate this process is using a reach-based approach 
instead of segment-based. 
In this scenario, each segment is further broken into a number of stream 
reaches. 

Similar to segment, we can define the travel time for each reach. However, in 
this case, the travel time is much shorter. For example, for a reach length of 
100m simulation, the travel time is approximately within 5 minutes (Imagine 
you are sitting in a kayak down the stream without paddling). 

Therefore, we need a much high temporal resolution to simulate the flow 
dynamics for each stream reach. Depending on the local elevation variations, 
the travel time varies significantly, which requires further consideration of 
different paces in stream routing. 