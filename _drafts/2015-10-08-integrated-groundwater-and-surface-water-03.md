---
layout: post
title: 'Integrated groundwater and surface water modeling: spatial discretization'
date: '2015-10-08T06:37:00.000-07:00'
author: Chang Liao
tags:
- MODFLOW
- Groundwater
modified_time: '2017-02-13T13:56:56.420-08:00'
thumbnail: https://3.bp.blogspot.com/-DA0aEob35CA/VhZw_drqPyI/AAAAAAAALk4/ni9qKZC46Rs/s72-c/spatial_discretization1.png
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-1289202966362808038
blogger_orig_url: https://www.changliao.us/2015/10/integrated-groundwater-and-surface-water-03.html
---

Numerical simulations have to break time and space into increments. For 
example, weather predictions are usually modeled in hours or days and maps are 
produced with resolution. 

 In contrast, our real world is always behaving continuously. For example, 
temperature always evolves with time continuously. 

We are also interested in a three dimensional simulation instead of 1D or 2D. 
The real world itself is 3D though we constantly forget that. It is just 
doesn't benefit much if we had a 3D temperature map. 


For other types of simulation, however, 3D could provides much better 
solutions. 
Groundwater flow, as an example, is best simulated with 3D numerical 
simulation. 

The spatial discretization is always a challenge for groundwater modeling. 
Horizontal and vertical discretization are always coupled together. For 
example, in a flat grassland with homogeneous hydrologic proprieties, the 
horizontal discretization becomes less important. However, if the surface 
elevation changes drastically, the horizontal discretization matters. 

Imagine a cheese cake with multi-layers, if it is placed on the table, no 
matter how you cut it into pieces, the cake will look exactly the same as long 
as you don't part the pieces. 



<div style="text-align: center;">[<img border="0" 
src="https://3.bp.blogspot.com/-DA0aEob35CA/VhZw_drqPyI/AAAAAAAALk4/ni9qKZC46Rs/s400/spatial_discretization1.png" 
/>](http://3.bp.blogspot.com/-DA0aEob35CA/VhZw_drqPyI/AAAAAAAALk4/ni9qKZC46Rs/s1600/spatial_discretization1.png) 

 However, if we lean the table to certain angle and consider the pieces are 
adjusted to sit vertically in their same positions, the system may changes 
dramatically: the top layer on the higher position no longer touch others; the 
cheese in the lower layer may mix the neighbor cake layer! 

<div style="text-align: center;">[<img border="0" 
src="https://2.bp.blogspot.com/-1s4V7XN16RU/VhZw_ZEAlBI/AAAAAAAALk8/bulWlMhVwpY/s400/spatial_discretization2.png" 
/>](http://2.bp.blogspot.com/-1s4V7XN16RU/VhZw_ZEAlBI/AAAAAAAALk8/bulWlMhVwpY/s1600/spatial_discretization2.png) 

 So what might be the solution? We need better space discretization to 
minimize the space distortion. 

Let's still consider the cake example, if there is only one layer, just the 
cake, it might be acceptable as long as we don't flip the table. In other 
words, if we have thick layers, horizontal discretization becomes less 
important. However, when we have thin layers, fine horizontal discretization 
can reduce the distortion. If we cut the cake into many pieces, then top might 
always stick with top. 

<div>Wait, if we cut the cake to fine, what if we can't even eat it? 
Like if we have fine grid, such as 0.1m, that we can't even run the simulation 
since we may have 1Billion grid! 

Therefore, a compromise has to be made in order to make things work.<div> 
Several options are: 
Bring horizontal grid into the similar scale with vertical layer to avoid 
distortion; 
Use unstructured grid instead of uniform grid to reduce computational demand. 


Besides, careful selection or definition of the layered cake and table also 
plays an important role! 