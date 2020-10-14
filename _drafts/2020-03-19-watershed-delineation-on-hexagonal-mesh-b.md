---
layout: post
title: 'Watershed Delineation On A Hexagonal Mesh Grid: Part B'
date: '2020-03-19T22:00:00.000-07:00'
author: Chang Liao
tags:
- Arc Hydro
- ECO3D
- HexWatershed
- DGGS
- Watershed Hydrology
- ArcSWAT
- GDAL
modified_time: '2020-04-17T07:57:40.557-07:00'
thumbnail: https://1.bp.blogspot.com/-epsIwby4OMM/XnRLSQ-WpnI/AAAAAAAA8Hk/kjfBHG_pqmUd6PeaJe5HSuwXyrK7M6xqwCLcBGAsYHQ/s72-c/workflow.png
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-1830383762675265122
blogger_orig_url: https://www.changliao.us/2020/03/watershed-delineation-on-hexagonal-mesh-b.html
---

This is the second part of a study, the first part can be accessed from [<span 
style="color: 
red;">**Here**](http://www.changliao.us/2020/03/watershed-delineation-on-hexagonal-mesh-a.html). 
So we decided to use the ISEA alike grid, a hexagon mesh grid to address these 
issues. 

<div>(The figures are high resolution, you might need to zoom in to view.) 

<div>What follows is something I should have learned if my major was 
hydrology. Even though we have been using ArcSWAT, ArcHydro many times, we 
seldom really looked into the algorithms because they are mostly straight 
forward. 
<div> 
<div>But when we decided to try this on a different mesh grid, a lot of 
details start to emerge, and through which we also learned a lot.<div> 
<div>The overall workflow is pretty simple:<div class="separator" 
style="clear: both; text-align: center;">[<img border="0" 
data-original-height="1600" data-original-width="1036" height="640" 
src="https://1.bp.blogspot.com/-epsIwby4OMM/XnRLSQ-WpnI/AAAAAAAA8Hk/kjfBHG_pqmUd6PeaJe5HSuwXyrK7M6xqwCLcBGAsYHQ/s640/workflow.png" 
width="412" 
/>](https://1.bp.blogspot.com/-epsIwby4OMM/XnRLSQ-WpnI/AAAAAAAA8Hk/kjfBHG_pqmUd6PeaJe5HSuwXyrK7M6xqwCLcBGAsYHQ/s1600/workflow.png)<div 
class="separator" style="clear: both; text-align: left;">But because the grid 
is different, we made several improvements.<div class="separator" 
style="clear: both; text-align: left;">First,  we need a new index system, and 
we need to rebuild the neighbor information.<div class="separator" 
style="clear: both; text-align: center;">[<img border="0" 
data-original-height="519" data-original-width="1130" height="292" 
src="https://1.bp.blogspot.com/-u9zMqgYMZNg/XnRLq75jTwI/AAAAAAAA8Hs/JQcB7tMCFXk4FNZmvGWRgwu-ZcG0cfhKACLcBGAsYHQ/s640/hexagon_topology.png" 
width="640" 
/>](https://1.bp.blogspot.com/-u9zMqgYMZNg/XnRLq75jTwI/AAAAAAAA8Hs/JQcB7tMCFXk4FNZmvGWRgwu-ZcG0cfhKACLcBGAsYHQ/s1600/hexagon_topology.png)<div 
class="separator" style="clear: both; text-align: left;"> 
<div> 
<div>We also need to do the depression filling, here we used the priority 
flooding method. This method is pretty impressive in this application. Without 
getting into details, this is how it works:<div> 
<div class="separator" style="clear: both; text-align: center;">[<img 
border="0" data-original-height="472" data-original-width="658" height="457" 
src="https://1.bp.blogspot.com/-I88LY57t2_k/XnRMZgt74ZI/AAAAAAAA8H0/UIhjiI7ef1ggd-Imv2pd5LEq-GhPiuv4ACLcBGAsYHQ/s640/hexagon_flood_legend.gif" 
width="640" 
/>](https://1.bp.blogspot.com/-I88LY57t2_k/XnRMZgt74ZI/AAAAAAAA8H0/UIhjiI7ef1ggd-Imv2pd5LEq-GhPiuv4ACLcBGAsYHQ/s1600/hexagon_flood_legend.gif)<div> 
<div>After this, we are able to calculate the flow direction, for example:<div 
class="separator" style="clear: both; text-align: center;">[<img border="0" 
data-original-height="1180" data-original-width="1600" height="472" 
src="https://1.bp.blogspot.com/-bcV-j8gAXs0/XnRMwsOBrkI/AAAAAAAA8H8/c2_smhiqjrsAhYNd-1JIR7Ggw87NZBPawCLcBGAsYHQ/s640/cbf_flow_direction_90_zoom.png" 
width="640" 
/>](https://1.bp.blogspot.com/-bcV-j8gAXs0/XnRMwsOBrkI/AAAAAAAA8H8/c2_smhiqjrsAhYNd-1JIR7Ggw87NZBPawCLcBGAsYHQ/s1600/cbf_flow_direction_90_zoom.png)<div> 
<div>As well as flow accumulation:<div class="separator" style="clear: both; 
text-align: center;">[<img border="0" data-original-height="1418" 
data-original-width="1600" height="566" 
src="https://1.bp.blogspot.com/-W-5ACyN4i4M/XnRM9S80JYI/AAAAAAAA8IA/QUuC_RmuQcw1T_MOx4qtRqf29I_7kf7TwCLcBGAsYHQ/s640/tinpan_flow_accumulation_30_zoom.png" 
width="640" 
/>](https://1.bp.blogspot.com/-W-5ACyN4i4M/XnRM9S80JYI/AAAAAAAA8IA/QUuC_RmuQcw1T_MOx4qtRqf29I_7kf7TwCLcBGAsYHQ/s1600/tinpan_flow_accumulation_30_zoom.png)<div>Last, 
I'd like to illustrate how this method fixs some headache for many of us:<div 
class="separator" style="clear: both; text-align: center;">[<img border="0" 
data-original-height="1036" data-original-width="1600" height="412" 
src="https://1.bp.blogspot.com/-VSpoYG_ycws/XnRNP1sz77I/AAAAAAAA8IQ/UInrEEl5wYEeci1x9vTbcTV3fwl8B92JACLcBGAsYHQ/s640/tinpan30_square.png" 
width="640" 
/>](https://1.bp.blogspot.com/-VSpoYG_ycws/XnRNP1sz77I/AAAAAAAA8IQ/UInrEEl5wYEeci1x9vTbcTV3fwl8B92JACLcBGAsYHQ/s1600/tinpan30_square.png) 
<div class="separator" style="clear: both; text-align: center;">[<img 
border="0" data-original-height="1202" data-original-width="1600" height="480" 
src="https://1.bp.blogspot.com/-aN09UCv8aiA/XnRNP9qvWcI/AAAAAAAA8IM/BR9j41gXXC0wdtSmOWcIboDV81d14zPkwCLcBGAsYHQ/s640/tinpan30_hexagon.png" 
width="640" 
/>](https://1.bp.blogspot.com/-aN09UCv8aiA/XnRNP9qvWcI/AAAAAAAA8IM/BR9j41gXXC0wdtSmOWcIboDV81d14zPkwCLcBGAsYHQ/s1600/tinpan30_hexagon.png)<div 
class="separator" style="clear: both; text-align: left;">If you are interested 
in using or applying this method in your study area or hydrologic model, stay 
tuned.<div class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">Reference:<div 
style="margin-left: 24pt; text-indent: -24.0pt;">Liao, C., Tesfa, T., Duan, 
Z., &amp; Leung, L. R. (2020). Watershed delineation on a hexagonal mesh grid. 
*Environmental Modelling &amp; Software*, *128*, 104702. 
https://doi.org/https://doi.org/10.1016/j.envsoft.2020.104702<div> 