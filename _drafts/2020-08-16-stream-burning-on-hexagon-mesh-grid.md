---
layout: post
title: Stream burning on the hexagon mesh grid
date: '2020-08-16T15:30:00.008-07:00'
author: Chang Liao
tags:
- Hydrology
- Hydrological Modeling
- HexWatershed
- Global Hydrology
- Hexagon
modified_time: '2020-08-16T15:30:58.968-07:00'
thumbnail: https://1.bp.blogspot.com/-x5TVCvEPY7U/Xzlkhaz9fgI/AAAAAAAA_Sc/tjbLNsEB4nE3LvaMT3cHhD5jzy45u-VagCLcBGAsYHQ/s72-c/outlet_burning.png
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-490821681261991419
blogger_orig_url: https://www.changliao.us/2020/08/stream-burning-on-hexagon-mesh-grid.html
---

<p></p><div class="separator" style="clear: both; text-align: center;"> 
<div class="separator" style="clear: both; text-align: left;">This is a follow 
up study of HexWatershed. In the latest development, we decided to add the so 
called "stream burning" capability into the HexWatershed model.<div 
class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">A details 
explanation of the motivation will be discussed in our new paper. Here I will 
only focus on some critical issues in the development.<div class="separator" 
style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">The first issue 
is: what happens if the outlet is not at the edge?<div class="separator" 
style="clear: both; text-align: center;">[<img border="0" 
data-original-height="419" data-original-width="424" 
src="https://1.bp.blogspot.com/-x5TVCvEPY7U/Xzlkhaz9fgI/AAAAAAAA_Sc/tjbLNsEB4nE3LvaMT3cHhD5jzy45u-VagCLcBGAsYHQ/s0/outlet_burning.png" 
/>](https://1.bp.blogspot.com/-x5TVCvEPY7U/Xzlkhaz9fgI/AAAAAAAA_Sc/tjbLNsEB4nE3LvaMT3cHhD5jzy45u-VagCLcBGAsYHQ/s424/outlet_burning.png)<div 
class="separator" style="clear: both; text-align: center;"> 
One of the core processes to conduct priority-flood filling or breaching is 
that if a grid cell is processed, it will not be processed again because a 
mask is used to keep track all the history.<p></p><p>When the outlet is not at 
the edge, the priority-flood method may start from a non-stream grid. As the 
algorithm advances, grids near the actual outlet can be possibly marked before 
outlet is processed. Since these grids are marked, they won't be changed even 
though they are next to stream. The direct result is that the outlet grid 
becomes a depression. However, by the definition of watershed, the outlet 
should be lowest elevation and it would be the first to be added into the 
queue. By the time the outlet is added, it would automatically turns one of 
the neighbors into a stream grid.</p><p>This is exactly what is modeled in the 
HexWatershed. Even without an outlet, the model will be able to create a new 
one, which however, may be the same with the NHD dataset. Therefore, it is 
more desirable to set it in the configuration through the mesh ID 
parameter.</p><p> 
</p><p> </p> 