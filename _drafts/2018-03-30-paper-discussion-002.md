---
layout: post
title: Quantifying the role of permafrost distribution in groundwater and surface
  water interactions using a three-dimensional hydrological model
date: '2018-03-30T17:07:00.000-07:00'
author: Chang Liao
tags:
- Groundwater Modeling
- MODFLOW
- Groundwater
modified_time: '2018-08-17T15:27:58.317-07:00'
thumbnail: https://1.bp.blogspot.com/-diau2w8atl8/Wr7J4iBRzsI/AAAAAAAAgL4/SlEVVy853U0dvhayfs__lDcugkseDS0NACLcBGAs/s72-c/figure3b.jpg
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-821426278144995144
blogger_orig_url: https://www.changliao.us/2018/03/paper-discussion-002.html
---

Following my earlier 
[post](http://www.changliao.us/2018/03/paper-discussion-001.html) on promoting 
my research, this is the second study that I conducted in an attempt to 
understand the hydrology processes in high latitudes. 
<div> 
<div>You are encouraged to read the first 
[post](http://www.changliao.us/2018/03/paper-discussion-001.html) for a 
background understanding of this study.<div> 
<div>Let's cut to the chase, the title of this study is "Quantifying the role 
of permafrost distribution in groundwater and surface water interactions using 
a three-dimensional hydrological model", and you can access the paper through 
[here](https://www.tandfonline.com/doi/abs/10.1657/AAAR0016-022) or 
[this](http://www.bioone.org/doi/abs/10.1657/AAAR0016-022).<div> 
<div>In Arctic, snow and glacier are not the only players in the hydrology 
processes. Permafrost, the so called frozen soil is also an important player 
in both hydrology and carbon cycles.<div> 
<div>There are several reasons for that:<div>1. It is frozen, so it could 
potentially release a lot of water in the warming climate; 
1. Permafrost degradation can change the landscape, then both the carbon and 
water cycles will be affected; 
1. Permafrost is like a barrier, it blocks interactions. Therefore, permafrost 
degradation will change the interactions between surface processes and deep 
processes. 
<div>While there are many aspects we can look into, we decided to look into 
the groundwater and surface water (GW-SW) interactions. Part of the reason is 
that we now consider permafrost in a three-dimensional domain and GW-SW 
interaction in directly affected by the spatial distribution of 
permafrost.<div> 
<div>So we started with the standard groundwater flow model, this model is 
again from USGS, and it is called MODFLOW. More details can be found at 
[here](https://www.blogger.com/(https://water.usgs.gov/ogw/modflow/) 
(https://water.usgs.gov/ogw/modflow/).<div> 
<div>I would not get into details of how MODFLOW works. I do want to highlight 
a few important things.<div>1. The spatial domain is now broken into 3D zones, 
just like you cut your cheese cake. It has layers and pieces; 
1. Water flows through the 3D domain and its speed depends on gradient and 
conductivity. 
<div> 
<div>A zoomed view of the 3D setup is illustrated here:<div class="separator" 
style="clear: both; text-align: center;">[<img border="0" 
data-original-height="983" data-original-width="1600" height="392" 
src="https://1.bp.blogspot.com/-diau2w8atl8/Wr7J4iBRzsI/AAAAAAAAgL4/SlEVVy853U0dvhayfs__lDcugkseDS0NACLcBGAs/s640/figure3b.jpg" 
width="640" 
/>](https://1.bp.blogspot.com/-diau2w8atl8/Wr7J4iBRzsI/AAAAAAAAgL4/SlEVVy853U0dvhayfs__lDcugkseDS0NACLcBGAs/s1600/figure3b.jpg)<div 
class="separator" style="clear: both; text-align: center;">Figure 1. The 
spatial discretization of the study domain.<div class="separator" 
style="clear: both; text-align: center;"> 
<div class="separator" style="clear: both; text-align: center;"> 
<div class="separator" style="clear: both; text-align: left;">If you look at 
the above figure, different cell/zone have different shape/size and hydrologic 
properties.<div class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">We have to know 
where permafrost is located and how deep they are. This is defined using the 
permafrost map:<div class="separator" style="clear: both; text-align: 
center;">[<img border="0" data-original-height="1133" 
data-original-width="1600" height="452" 
src="https://1.bp.blogspot.com/-aCt7MKKy5mY/Wr7L0d0DDLI/AAAAAAAAgMA/iNwSf2z3pfYZe5kzP8JLfhBxHegkQva-ACLcBGAs/s640/figure6.jpg" 
width="640" 
/>](https://1.bp.blogspot.com/-aCt7MKKy5mY/Wr7L0d0DDLI/AAAAAAAAgMA/iNwSf2z3pfYZe5kzP8JLfhBxHegkQva-ACLcBGAs/s1600/figure6.jpg)<div 
class="separator" style="clear: both; text-align: center;">Figure 2. The 
spatial distribution of permafrost and thickness.<div class="separator" 
style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">Note that we 
also defined the stream network similar to my earlier study. In fact, it is a 
much complicated process than it appears to be.<div class="separator" 
style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">We have to 
consider how groundwater interacts with stream in permafrost regions.<div 
class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">We first need to 
ask, is there permafrost under stream bed?<div class="separator" style="clear: 
both; text-align: left;">And we also have to ask whether there are permafrost 
next to stream.<div class="separator" style="clear: both; text-align: 
left;">In the end, we have to design the model structure to be very realistic 
and computationally friendly. For example, should the stream in the first 
layer or the second layer where permafrost rests? Can there be two-way 
interactions depending on stream stage?<div class="separator" style="clear: 
both; text-align: left;">Overall, the design is illustrated in Figure 3. <div 
class="separator" style="clear: both; text-align: center;">[<img border="0" 
data-original-height="1200" data-original-width="1600" height="480" 
src="https://2.bp.blogspot.com/-JidZs2Vn2wY/Wr7MkEjChrI/AAAAAAAAgMI/5m-znXO9dsIUmiNFlHYpokhu7kXRr7BkACLcBGAs/s640/figure5.jpg" 
width="640" 
/>](https://2.bp.blogspot.com/-JidZs2Vn2wY/Wr7MkEjChrI/AAAAAAAAgMI/5m-znXO9dsIUmiNFlHYpokhu7kXRr7BkACLcBGAs/s1600/figure5.jpg)<div 
class="separator" style="clear: both; text-align: center;">Figure 3. The 
interactions between groundwater and stream water in permafrost regions.<div 
class="separator" style="clear: both; text-align: center;"> 
<div class="separator" style="clear: both; text-align: center;"> 
<div class="separator" style="clear: both; text-align: left;">We ran the 
simulation for 36 years driven by the surface infiltration and stream 
discharge. Some results are listed here:<div class="separator" style="clear: 
both; text-align: center;">[<img border="0" data-original-height="1393" 
data-original-width="1600" height="556" 
src="https://4.bp.blogspot.com/-CIwX9MYXCHE/Wr7OtxjOpxI/AAAAAAAAgMU/3bq4yFCCm7w8a0Prf-S5uQlWV5mBZEvXwCLcBGAs/s640/figure10.jpg" 
width="640" 
/>](https://4.bp.blogspot.com/-CIwX9MYXCHE/Wr7OtxjOpxI/AAAAAAAAgMU/3bq4yFCCm7w8a0Prf-S5uQlWV5mBZEvXwCLcBGAs/s1600/figure10.jpg)<div 
class="separator" style="clear: both; text-align: center;">Figure 4. The 
vertical groundwater flow between layer 1 and 2.<div class="separator" 
style="clear: both; text-align: center;"> 
 This result demonstrates that most vertical flow occurs in permafrost-free 
zones, which is not surprising. It also implies that in the warming climate 
where there is less permafrost, the spatial distribution will definitely 
change. 
<div class="separator" style="clear: both; text-align: center;">[<img 
border="0" data-original-height="648" data-original-width="1600" height="258" 
src="https://2.bp.blogspot.com/-ZTHxKPd6Tuk/Wr7OvHp8l-I/AAAAAAAAgMY/IbLS1C9EGV02WTFuHUQ_zL2rxiU0NfsfQCLcBGAs/s640/figure12.jpg" 
width="640" 
/>](https://2.bp.blogspot.com/-ZTHxKPd6Tuk/Wr7OvHp8l-I/AAAAAAAAgMY/IbLS1C9EGV02WTFuHUQ_zL2rxiU0NfsfQCLcBGAs/s1600/figure12.jpg)<div 
class="separator" style="clear: both; text-align: center;">Figure 5. Time 
series of groundwater and stream water interactions.<div class="separator" 
style="clear: both; text-align: center;"> 
<div class="separator" style="clear: both; text-align: left;">This result 
first confirms the base flow throughout the year fed by groundwater. It also 
shows the interactions in different time/season vary with stream 
conditions.<div class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">This study has 
demonstrated the permafrost plays an important role in GW-SW interactions. It 
also implies this relationship will change in the warming climate.<div 
class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">During this 
study, a IDL-based MODFLOW system was developed. Later on, this system is 
converted to Python-based, so you may try out MODFLOW simulation in any region 
without too much effort.<div class="separator" style="clear: both; text-align: 
left;"> 
<div class="separator" style="clear: both; text-align: left;"> 
<div> 
<div> 
<div> 