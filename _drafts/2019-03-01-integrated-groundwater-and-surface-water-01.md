---
layout: post
title: SWAT-MODFLOW stream flow routing problem
date: '2019-03-01T16:03:00.001-08:00'
author: Chang Liao
tags:
- MODFLOW
- ArcSWAT
- PRMS
- SWAT
modified_time: '2019-03-12T17:04:43.422-07:00'
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-942483677787690714
blogger_orig_url: https://www.changliao.us/2019/03/integrated-groundwater-and-surface-water-01.html
---

<div>Surface water hydrology and groundwater hydrology are coupled together in 
natural ecosystem. While it is easy to say so, it is not easy to model both of 
them simultaneously.<div> 
<div>In my earlier posts I have covered a lot on related topics including 
MODFLOW, PRMS and GSFLOW.<div> 
<div>For example: 
<div>[https://www.changliao.us/2018/03/paper-discussion-002.html](https://www.changliao.us/2018/03/paper-discussion-002.html)<div>[https://www.changliao.us/2018/03/paper-discussion-001.html](https://www.changliao.us/2018/03/paper-discussion-001.html)<div>[https://www.changliao.us/2015/09/integrated-groundwater-and-surface-water-01.html](https://www.changliao.us/2015/09/integrated-groundwater-and-surface-water-01.html)<div>[https://www.changliao.us/2016/04/surface-water-hydrology-modeling-002.html](https://www.changliao.us/2016/04/surface-water-hydrology-modeling-002.html)<div> 
<div>Today I will discuss some other issues related to SWAT-MODFLOW. SWAT is 
another widely used surface hydrology model and there are ongoing efforts 
trying the couple MODFLOW with 
SWAT.<div>https://swat.tamu.edu/software/swat-modflow/<div> 
<div>Unlike PRMS, SWAT in general does NOT use grid based approach to run 
simulation. Instead, SWAT uses subbasin and HRU to represent the watershed. 
And this difference may cause a list of challenge for us. I will discuss a few 
of them in details below.<div> 
<div>Because SWAT and MODFLOW are not fully coupled from the mathematic 
perspective, some balance may not be achieved. Let's temporally ignore the 
issue brought out by HRU and MODFLOW grid overlap. Both model simulate the 
river routing, but only the SWAT routing result is used as "true" output. 
<div> 
<div>Conceptually, these two model behave different as well. For SWAT, the 
routing is defined by the fig file and the stream segment numbering is not 
important. <strike>However, in MODFLOW, the order matters, even if you are 
using RIV package.</strike><div> 
"Note 5: Reach information is read in sequential order from upstream to 
downstream, first by segments, and then sequentially by reaches. **<span 
style="color: red;">If segments are not numbered sequentially in downstream 
order, then the inflow to a segment during the current MODFLOW iteration will 
be the outflow from an upstream segment calculated during the previous 
iteration. Lagging the inflow by one iteration does not change the solution 
for flows into and out of a segment after MODFLOW converges; however, this 
approach may require an additional iteration for the model to converge. 
**Reaches must be listed and read sequentially because the order determines 
the connections of inflows and outflows within a stream segment." (SFR2 user 
manual) 
<div> 
<div>Even though after the model converges, the difference will be not 
significant, it will still bring uncertainty in the following simulation.<div> 
<div>Therefore, it is obvious that these two model use different index system 
to identify stream networks. It is inevitably we can not use SWAT numbering as 
the input for MODFLOW and addition efforts will be required to link them 
together.<div> 
<div>However, there are some solutions to this issue:<div>1. We can just go 
ahead and prepare SWAT and MODFLOW model as usual. After that, we can manually 
link them using the indices. This method requires less modifications on the 
original model but we need to generate new stream ID for MODFLOW. 
1. We can change the ArcSWAT results so that the SWAT stream ID are 
sequentially numbered. The SWAT stream ID can then be used directly by 
MODFLOW. This method requires good understanding of the ArcSWAT mechanism. 
Given that ArcSWAT is not open source, we need to check SWAT input/output 
carefully to see whether the modification is successful or not. 
1. We can also change the SWAT fig and related files and then generate new 
Stream ID for MODFLOW. In this case, we do not have to modify ArcSWAT. But we 
have to check through SWAT input to make sure all related files are updated. 
Because SWAT is open source, this is straightforward. 
<div>Method 2 and 3 require more efforts. In short term, method 1 should be 
used. 

## <span style="color: red;">Updates: in the RIV package, the order does not 
matter because the MODFLOW does not calculate the river routing at all! 
<b><span style="color: red;"> 
</b><div> 
<div> 
<div> 
<div> 