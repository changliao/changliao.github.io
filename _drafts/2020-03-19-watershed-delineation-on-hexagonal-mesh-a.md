---
layout: post
title: 'Watershed Delineation On A Hexagonal Mesh Grid: Part A'
date: '2020-03-19T11:35:00.000-07:00'
author: Chang Liao
tags:
- ECOGlobe
- HexContinent
- DGGRID
- ECO3D
- DGGS
- Watershed Hydrology
- Hexagon
- ISEA
modified_time: '2020-04-17T07:57:56.661-07:00'
thumbnail: https://1.bp.blogspot.com/-dyArKafygvQ/XnOzr9Kut7I/AAAAAAAA8Gw/JCR70uMyL9oKF368HrO5NRirBwOfpNQ2wCLcBGAsYHQ/s72-c/spatial_distortion.png
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-5155046341595809518
blogger_orig_url: https://www.changliao.us/2020/03/watershed-delineation-on-hexagonal-mesh-a.html
---

One of our recent publications is "Watershed Delineation On A Hexagonal Mesh 
Grid" published on Environmental Modeling and Software 
(**[link](https://doi.org/10.1016/j.envsoft.2020.104702)**). 
<div>Here I want to provide some behind the scene details of this study. 

(The figures are high resolution, you might need to zoom in to view.) 
<div> 
<div>First, I'd like to introduce the motivation of this work.<div>Many of us 
including me have done lots of watershed/catchment hydrology modeling. For 
example, one of my recent publications is a three-dimensional carbon-water 
cycle modeling work 
([link](https://agupubs.onlinelibrary.wiley.com/doi/full/10.1029/2019MS001792)), 
which uses lots of watershed hydrology algorithms.<div> 
<div>In principle, watershed hydrology should be applied to large spatial 
domain, even global scale. But why no one is doing it? <div>I will use the 
popular USDA SWAT model as an example. Why no one is setting up a SWAT model 
globally? <div> 
<div>There are several reasons we cannot use SWAT at global scale:<div>1. We 
cannot produce a global DEM with a desired map projection. SWAT model relies 
on stream network, which depends on DEM. It is impossible to use a 2D map 
projection to represent a 3D sphere (Earth is not flat). 
1. Computationally, it is difficult to delineate watershed at global scale. 
First, the dataset set is large, and second the continentals are not 
connected. 
<div>However, so how do many global hydrology models (GHMs) somehow avoid 
these issues?<div>1. Global hydrology models use latitude/longitude, instead 
of map projection. 
1. GHMs use relatively coarse resolution to avoid the computational issue. 
<div>The problem with latitude/longitude is that the grid area changes with 
latitude:<div class="separator" style="clear: both; text-align: center;">[<img 
border="0" data-original-height="1600" data-original-width="554" height="640" 
src="https://1.bp.blogspot.com/-dyArKafygvQ/XnOzr9Kut7I/AAAAAAAA8Gw/JCR70uMyL9oKF368HrO5NRirBwOfpNQ2wCLcBGAsYHQ/s640/spatial_distortion.png" 
width="219" 
/>](https://1.bp.blogspot.com/-dyArKafygvQ/XnOzr9Kut7I/AAAAAAAA8Gw/JCR70uMyL9oKF368HrO5NRirBwOfpNQ2wCLcBGAsYHQ/s1600/spatial_distortion.png)<div 
class="separator" style="clear: both; text-align: left;">Can we guarantee that 
the flow direction based on this distorted grid resolution is accurate enough? 
If not, then all the GHM simulations have greater uncertainty in high 
latitudes.<div class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both;">What if we can use a different 
type of grid to cover the globe? This falls into the category of Discrete 
Global Grid Systems (DGGS). There are a number of DGGS listed here: 
[https://en.wikipedia.org/wiki/Discrete_global_grid](https://en.wikipedia.org/wiki/Discrete_global_grid)<div 
class="separator" style="clear: both;"> 
<div class="separator" style="clear: both;">One of these DGGS is very 
promising for us if we want to guarantee reasonable flow direction. That is 
the ISEA grid:<div class="separator" style="clear: both; text-align: 
center;">[<img border="0" data-original-height="543" data-original-width="544" 
height="319" 
src="https://1.bp.blogspot.com/-Fl3Ay1RXFL0/XnO4Pge01FI/AAAAAAAA8G8/4DD4tF86xRM3hWMSMZ1kMuqtFdZVPKHZQCLcBGAsYHQ/s320/dggrid.jpg" 
width="320" 
/>](https://1.bp.blogspot.com/-Fl3Ay1RXFL0/XnO4Pge01FI/AAAAAAAA8G8/4DD4tF86xRM3hWMSMZ1kMuqtFdZVPKHZQCLcBGAsYHQ/s1600/dggrid.jpg)<div 
class="separator" style="clear: both; text-align: center;"> 
<div class="" style="clear: both;">Traditionally, flow direction is 
represented by this method:<div class="separator" style="clear: both; 
text-align: center;">[<img border="0" data-original-height="318" 
data-original-width="339" height="299" 
src="https://1.bp.blogspot.com/-GLCjHhSxeaY/XnO4l8R_2XI/AAAAAAAA8HI/VY57jWBYrro00p0v3BPYTViUSUM2MmwcwCLcBGAsYHQ/s320/d4d8.png" 
width="320" 
/>](https://1.bp.blogspot.com/-GLCjHhSxeaY/XnO4l8R_2XI/AAAAAAAA8HI/VY57jWBYrro00p0v3BPYTViUSUM2MmwcwCLcBGAsYHQ/s1600/d4d8.png)<div 
class="separator" style="clear: both;">Interestingly, in an ISEA grid, the 
flow direction can be represented differently:<div class="separator" 
style="clear: both; text-align: center;">[<img border="0" 
data-original-height="284" data-original-width="281" height="320" 
src="https://1.bp.blogspot.com/-yHJAsVfUEQ8/XnO4l3dNQyI/AAAAAAAA8HM/RygEG-p6upMyaS0bROiP-DD0SmCySvloACEwYBhgL/s320/d6.png" 
width="316" 
/>](https://1.bp.blogspot.com/-yHJAsVfUEQ8/XnO4l3dNQyI/AAAAAAAA8HM/RygEG-p6upMyaS0bROiP-DD0SmCySvloACEwYBhgL/s1600/d6.png)<div 
class="separator" style="clear: both;"> 
<div>It actually solves one of the oldest problems in watershed hydrology: the 
travel length in the diagonal direction is longer than direct direction. 

A bonus benefit is that it will also eliminate the island effect: 
<div class="separator" style="clear: both; text-align: center;">[<img 
border="0" data-original-height="241" data-original-width="258" height="298" 
src="https://1.bp.blogspot.com/-W1xBTlbNrMs/XnO5m3lBloI/AAAAAAAA8HU/0q7Wd9SepnMa1NCibLEbFLoEFVzlUDfaQCLcBGAsYHQ/s320/island.png" 
width="320" 
/>](https://1.bp.blogspot.com/-W1xBTlbNrMs/XnO5m3lBloI/AAAAAAAA8HU/0q7Wd9SepnMa1NCibLEbFLoEFVzlUDfaQCLcBGAsYHQ/s1600/island.png)<div 
class="separator" style="clear: both; text-align: center;"> 
<div class="separator" style="clear: both; text-align: left;">You probably 
have seen this before when you look at the subbasin boundary results from the 
watershed delineation.<div class="separator" style="clear: both; text-align: 
left;"> 
<div class="separator" style="clear: both; text-align: left;">So we decided to 
use the ISEA alike grid, a hexagon mesh grid to address these issues.<div 
class="separator" style="clear: both; text-align: center;"> 
The second part is [**<span style="color: 
red;">Here**](https://www.changliao.us/2020/03/watershed-delineation-on-hexagonal-mesh-b.html). 

<div>Reference: 
<div style="margin-left: 24pt; text-indent: -24.0pt;">Liao, C., Tesfa, T., 
Duan, Z., &amp; Leung, L. R. (2020). Watershed delineation on a hexagonal mesh 
grid. *Environmental Modelling &amp; Software*, *128*, 104702. 
https://doi.org/https://doi.org/10.1016/j.envsoft.2020.104702 