---
layout: post
title: 'Spatial datasets operations: a hexagon-based discrete grid systems for global
  simulation'
date: '2017-06-19T08:24:00.001-07:00'
author: Chang Liao
tags:
- CPI
- DGGRID
modified_time: '2018-04-03T12:17:22.750-07:00'
thumbnail: https://4.bp.blogspot.com/-nIM2m-WQHWo/WUfoTfHVS6I/AAAAAAAAX68/1SZtjTEem9MXY1tm_pQ6s4dd3BvkiuQNACLcBGAs/s72-c/polar.jpg
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-1324242836609927983
blogger_orig_url: https://www.changliao.us/2017/06/spatial-datasets-operations-006.html
---

After finished my three-dimensional coupled water and carbon cycle model, I 
have been thinking whether I can apply this approach at large spatial domain 
or even global scale. 
During this process, I realized that most (or all) global scale land surface 
modeling work are based on the square grid system, which is widely used in 
Earth science. This grid is also common recognized as pixel, grid cell. 

Can we still use grid in global scale land surface model simulation? 
Yes and no. If you do not consider lateral flow, then interactions between 
grid cells are omitted. In this scenario, grid cell might be the easiest 
approach to do so. 
However, if horizontal interactions are considered. Then the grid-based 
structure will fail. This is because latitude/longitude based structure will 
create singularity in polar regions like this. 
<div class="separator" style="clear: both; text-align: center;">[<img 
border="0" data-original-height="391" data-original-width="766" height="323" 
src="https://4.bp.blogspot.com/-nIM2m-WQHWo/WUfoTfHVS6I/AAAAAAAAX68/1SZtjTEem9MXY1tm_pQ6s4dd3BvkiuQNACLcBGAs/s640/polar.jpg" 
width="640" 
/>](https://4.bp.blogspot.com/-nIM2m-WQHWo/WUfoTfHVS6I/AAAAAAAAX68/1SZtjTEem9MXY1tm_pQ6s4dd3BvkiuQNACLcBGAs/s1600/polar.jpg) 
And due to the distortion, it is impossible to calculate interactions within 
this area across polar regions. 

Most maps of various variables at global scale express the polar regions as 
lines instead of points due to current limitation in map projections. 

So what is the solution? 
As I mentioned in my previous 
[post](http://www.changliao.us/2017/06/spatial-datasets-operations-005.html), 
a hexagon-based discrete grid system can be used to address this issue. To get 
it start easily, image Earth as a football, specifically, a soccer, then no 
place on this surface will be distorted and they all will have nearly the same 
area. 
Using technics in geometry, we can further divide the "faces" into smaller 
"faces". Without getting into some details we can produce a discrete grid 
system like this: 
<div class="separator" style="clear: both; text-align: center;">[<img 
border="0" data-original-height="941" data-original-width="1600" height="376" 
src="https://3.bp.blogspot.com/-d4hYxgTBly4/WUfpNDSNzwI/AAAAAAAAX7E/wLKSY_IQhcUxTDWh7aGSC87X2AWud5MLwCLcBGAs/s640/dggrid.jpg" 
width="640" 
/>](https://3.bp.blogspot.com/-d4hYxgTBly4/WUfpNDSNzwI/AAAAAAAAX7E/wLKSY_IQhcUxTDWh7aGSC87X2AWud5MLwCLcBGAs/s1600/dggrid.jpg) 
Create a structure like this requires some program like this 

[http://www.discreteglobalgrids.org/software/](http://www.discreteglobalgrids.org/software/) 
There is also an online service similar: 

[https://www.pyxisglobe.com/view/Explore](https://www.pyxisglobe.com/view/Explore) 

After this grid system is built, another problem is how we can index all the 
grids. Traditional cartesian coordinate system will not work well in this 
scenario. 

In DGGRID, a Central Place Index (CPI) system is introduced to address this 
issue, but not implemented at all resolutions, which however provides an 
effective approach. 

Besides, we also need to consider the relationship between grids, 
specifically, we need to know the neighbors of each grid in global simulation. 
So far I haven't got a decent solution for the indexing problem but will 
update when available. 

I want to thank Dr. Kevin for his help in DGGRID program and Perry Peterson on 
Q&amp;A related to Pyxis. 