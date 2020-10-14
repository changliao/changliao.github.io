---
layout: post
title: The problem of geographic coordinate system in global scale simulation
date: '2018-08-11T14:13:00.000-07:00'
author: Chang Liao
tags:
- Google Map
- Numerical Simulation
- ECO3D
- GIS
- GCS
- Heat Equation
- Hexagon
modified_time: '2018-08-11T14:19:32.808-07:00'
thumbnail: https://i.ytimg.com/vi/kIID5FDi2JQ/0.jpg
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-7824883896413545064
blogger_orig_url: https://www.changliao.us/2018/08/model-development-006.html
---

Earlier I have discussed some 
**[idea](https://www.changliao.us/2017/06/spatial-datasets-operations-006.html)** 
about the hexagon-based grid system. Now I have provided some tests and 
materials to support this project. 

90% percent of global maps you can find online are using the geographic 
coordinate system 
([GCS](https://en.wikipedia.org/wiki/Geographic_coordinate_system)). You can 
try to search "global map" in [Google 
image](https://www.google.com/search?hl=en&amp;tbm=isch&amp;source=hp&amp;biw=1277&amp;bih=688&amp;ei=WkhvW8qKJ4TesAW915yAAw&amp;q=global+map&amp;oq=global+&amp;gs_l=img.3.0.35i39k1j0l9.1747.2687.0.4513.9.9.0.0.0.0.127.697.0j6.6.0....0...1ac.1.64.img..3.6.696.0...0.NzMugjEpFdI). 
<div> 
<div>There might be 9% of them are using various map projection.<div>The 
reason why there are so many different ways to represent the Earth is that 
Earth is NOT flat. Google know it so they changed the Google Map 
recently.<div> 
<div>So these are some basic GIS knowledge but you can also learn it from this 
video.<div><div style="text-align: center;"><iframe allowfullscreen="" 
class="YOUTUBE-iframe-video" 
data-thumbnail-src="https://i.ytimg.com/vi/kIID5FDi2JQ/0.jpg" frameborder="0" 
height="266" 
src="https://www.youtube.com/embed/kIID5FDi2JQ?feature=player_embedded" 
width="320"></iframe><div style="text-align: center;"> 
<div>While it is generally OK to view these types of global map for daily 
usage, it can cause problems for large scale to global scale simulations. 

In Earth science, GCS is most commonly used as the grid system for terrestrial 
ecosystem simulations. For example, a 1* 1 degree grid will discrete the 
global into a 360 * 180 matrix. 

However, it will be problematic for several reasons. 
For example, the area at different regions are not the same. For example. a 
0.5* 0.5 grid cell is about 50*50km in Amazon whereas it is about 50*25km in 
Alaska, only half the size of the former one. 

To illustrate the difference, let's use a classical 2D heat equation I found 
from 
[here](https://scipython.com/book/chapter-7-matplotlib/examples/the-two-dimensional-diffusion-equation/): 
First, we run the simulation with the uniformly dx = dy, which present 
longitude and latitude in our case. The results are like this: 
<div class="separator" style="clear: both; text-align: center;">[<img 
border="0" data-original-height="960" data-original-width="1280" height="300" 
src="https://4.bp.blogspot.com/-_6bOKOEnjcQ/W29NwY-G7mI/AAAAAAAAjxQ/CUkkgz-M1F4OdKN7TQj-RWsONM1RXmxHgCLcBGAs/s400/Figure_2.png" 
width="400" 
/>](https://4.bp.blogspot.com/-_6bOKOEnjcQ/W29NwY-G7mI/AAAAAAAAjxQ/CUkkgz-M1F4OdKN7TQj-RWsONM1RXmxHgCLcBGAs/s1600/Figure_2.png)<div 
class="separator" style="clear: both; text-align: left;">Then we changed to dy 
= 2 dx: <div class="separator" style="clear: both; text-align: center;">[<img 
border="0" data-original-height="960" data-original-width="1280" height="300" 
src="https://2.bp.blogspot.com/-MAyI1wdt-70/W29OGUJoMCI/AAAAAAAAjxY/6IOepeBjQp8md8HuJZQHxZusDSCap9mLACLcBGAs/s400/Figure_1.png" 
width="400" 
/>](https://2.bp.blogspot.com/-MAyI1wdt-70/W29OGUJoMCI/AAAAAAAAjxY/6IOepeBjQp8md8HuJZQHxZusDSCap9mLACLcBGAs/s1600/Figure_1.png)<div 
class="separator" style="clear: both; text-align: left;">Last, we changed to 
dx = 2 dy:<div class="separator" style="clear: both; text-align: 
center;">[<img border="0" data-original-height="960" 
data-original-width="1280" height="300" 
src="https://2.bp.blogspot.com/-I8NZsDclj3A/W29OPkYPUII/AAAAAAAAjxc/vb32554OZyUHyJxGuDTaazaFIH6KmIybwCLcBGAs/s400/Figure_3.png" 
width="400" 
/>](https://2.bp.blogspot.com/-I8NZsDclj3A/W29OPkYPUII/AAAAAAAAjxc/vb32554OZyUHyJxGuDTaazaFIH6KmIybwCLcBGAs/s1600/Figure_3.png)<div 
class="separator" style="clear: both; text-align: center;"> 
<div class="separator" style="clear: both; text-align: left;">If you look 
closer, you will see the differences. When the grid geometry is not uniform, 
the simulated heat distribution is also not uniform in spatial.<div 
class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">Now let's get 
back to GCS in global simulation. Because the grid geometry changes from 
tropic to pole regions, the simulations are likely affected as well.<div 
class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">Next, I will 
show you some results of global scale hydrologic simulation.<div 
class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;"> 


<div> 
<div> 