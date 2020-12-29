---
layout: post
title: Paper discussion special issue the ECO3D model
date: '2019-12-20T20:04:00.003-08:00'
author: Chang Liao
tags:
- DOC
- Carbon
- ECO3D
- Water
- 3D
modified_time: '2020-01-04T13:02:40.038-08:00'
thumbnail: https://1.bp.blogspot.com/-2zX8HAVbhkw/XhD8yU-5EOI/AAAAAAAA64A/0ZGuTWI0mKwCM8ihgmks92Rj7JL8lrlQACLcBGAsYHQ/s72-c/figure3.jpg
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-3555258724070939948
blogger_orig_url: https://changliao.blogspot.com/2019/12/paper-discussion-specific-issue-eco3d.html
---


Recently we have published a paper on Journal of Advanced Modeling of Earth 
System. 

[https://agupubs.onlinelibrary.wiley.com/doi/abs/10.1029/2019MS001792](https://agupubs.onlinelibrary.wiley.com/doi/abs/10.1029/2019MS001792) 

This is also a personal milestone because it is the last chapter of my PhD 
thesis. Below I will provide some details of this work. 
<div> 
<div>In many of my earlier posts, I have discussed that our Earth system is 
always evolving in a three dimensional domain. The water flows, the atmosphere 
flows as well.<div> 
<div>However, in our numerical simulations, we do not always use 3D method. 
Sometimes we just don’t felt it necessary. For example, we always assume rain 
drops on land surface in vertical direction even though rain can attack our 
windows with an angel.<div> 
<div>In some other scenarios, we don’t use 3D because of computational 
resources. We can build a fully 3D model. But it is not useable if we don’t 
have the computer power to run it.<div> 
<div>Land surface model is an important component in ESM. But current 
generation of LSM is 1D instead of 3D. There are many reasons for this design, 
which I plan not to cover here. Instead, I will focus on why 3D makes sense 
and what is the challenge.<div> 
<div>From 1D to 3D means that each grid is aware of its neighborhood. More 
importantly, it talks to its neighborhood and exchanges maybe gifts.<div> 
<div>To put it in the model language, traditionally, each grid is isolated 
from others, so water and carbon budget are calculated in each grid 
independently. In 3D, a grid can send or receive some water and carbon from 
neighborhood. It’s like a grid at mountain valley can receive water from 
mountain ridge. Isn’t that making much more sense? 
On land, each grid cell can connect to its 4/6/8 neighbors: 
<div class="separator" style="clear: both; text-align: center;">[<img 
border="0" data-original-height="1237" data-original-width="1600" height="491" 
src="https://1.bp.blogspot.com/-2zX8HAVbhkw/XhD8yU-5EOI/AAAAAAAA64A/0ZGuTWI0mKwCM8ihgmks92Rj7JL8lrlQACLcBGAsYHQ/s640/figure3.jpg" 
width="640" 
/>](https://1.bp.blogspot.com/-2zX8HAVbhkw/XhD8yU-5EOI/AAAAAAAA64A/0ZGuTWI0mKwCM8ihgmks92Rj7JL8lrlQACLcBGAsYHQ/s1600/figure3.jpg)They 
can also connect with river: 
<div class="separator" style="clear: both; text-align: center;">[<img 
border="0" data-original-height="1582" data-original-width="1600" height="395" 
src="https://1.bp.blogspot.com/-W1qs4-0qAkg/XhD9IyJiIWI/AAAAAAAA64I/_2vnEFPTinwBcZ0HcIL-ic2oBzk0c-V1gCLcBGAsYHQ/s400/figure4.jpg" 
width="400" 
/>](https://1.bp.blogspot.com/-W1qs4-0qAkg/XhD9IyJiIWI/AAAAAAAA64I/_2vnEFPTinwBcZ0HcIL-ic2oBzk0c-V1gCLcBGAsYHQ/s1600/figure4.jpg) 
<div> 
<div>Water can carry lots of stuff, including carbon in the dissolved mode. 
Water can also carry other stuff such as sediment and debris. <div> 
<div>So without 3D, we cannot actually calculate how much stuff are carried by 
water from one grid to another.<div> 
<div>How to implement a 3D approach is another story, in ECO3D, we used a 
method widely used in the hydrology community, an explicit forward Euler 
method. There are several advantages of this method. I personally think that 
it’s suitable for parallel computing and does not require expensive matrix 
solvers.<div> 
<div>We also introduced a brand new DOC model, DOC is one of the carbon that 
flows with water, apparently. This is currently the only litter DOC model that 
considers lateral flow. 
Currently we haven’t consider the DOC in the groundwater system. 
<div class="separator" style="clear: both; text-align: center;">[<img 
border="0" data-original-height="1405" data-original-width="1600" height="351" 
src="https://1.bp.blogspot.com/-FHj2WvZB2TI/XhD9Q4OilrI/AAAAAAAA64M/zzC-STwnOkw3Kmx8paiSOCig0E3pPmG6QCLcBGAsYHQ/s400/figure5.jpg" 
width="400" 
/>](https://1.bp.blogspot.com/-FHj2WvZB2TI/XhD9Q4OilrI/AAAAAAAA64M/zzC-STwnOkw3Kmx8paiSOCig0E3pPmG6QCLcBGAsYHQ/s1600/figure5.jpg) 
<div> 
<div>Other solutes including particles can also be added and modeled by ECO3D 
in the near future.<div> 
<div>As we have more solutes in the water flow, it’s natural to have 
biogeochemistry and reactive transport as well.<div> 
<div>There are many scientific questions we can answer with this model. But my 
time is limited so I will slowly try them out in the near future. 