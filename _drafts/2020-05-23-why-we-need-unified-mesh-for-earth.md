---
layout: post
title: Why we need a unified mesh for Earth system model
date: '2020-05-23T12:01:00.003-07:00'
author: Chang Liao
tags:
- HexWatershed
- MPAS
- 3D
- Hexagon
modified_time: '2020-05-23T12:03:29.433-07:00'
thumbnail: https://1.bp.blogspot.com/-IrQvrB0by78/XslqOndM1UI/AAAAAAAA9tM/DCd1L6IQiREtw78wasssrzbBR9nLnlLugCK4BGAsYHg/s72-w640-c-h352/land_ocean.png
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-4549319579819921803
blogger_orig_url: https://www.changliao.us/2020/05/why-we-need-unified-mesh-for-earth.html
---

In many of my early posts, I shared some aspects that why I decided to develop 
the hexagon based watershed model, HexWatershed. <div>But the real motivation 
lies beyond watershed and I'd like to share some personal motivation why I 
started this project.<div> 
<div>For decades, since human invented computers and hydrologists invented 
hydrologic models, we rely on computational techniques to simulate hydrologic 
processes. And these techniques mostly use the structured mesh/matrix to 
describe the real world. Nearly all of us are familiar with the so-called 
X-Y-Z 3D domain.<div> 
<div>We stand on the shoulder of giants but we seldom question them. <div>It 
is true in earlier days that most of our research activities focus on a 
catchment scale or plot scale. We have to admit this is important because we 
need to understand the fine-scale process before we can extrapolate to a 
larger domain.<div> 
<div>We never look at hydrology on a global scale using a global method. Most 
of us are simply trying to copy the watershed scale method to a global scale 
without careful evaluations.<div> 
<div>That is where the problem comes, our Earth is not a typical X-Y-Z domain, 
instead, it is a sphere.<div>Also, our hydrologic processes interact with 
various components (lake, river, ocean, etc.)<div> 
<div>Can we really use the existing method directly on a global scale? Yes and 
No. We have already seen many cases. But they are far from what we need. <div> 
<div>For example, we cannot fix the land and ocean interaction:<div 
class="separator" style="clear: both; text-align: center;">[<img border="0" 
data-original-height="449" data-original-width="815" height="352" 
src="https://1.bp.blogspot.com/-IrQvrB0by78/XslqOndM1UI/AAAAAAAA9tM/DCd1L6IQiREtw78wasssrzbBR9nLnlLugCK4BGAsYHg/w640-h352/land_ocean.png" 
width="640" 
/>](https://1.bp.blogspot.com/-IrQvrB0by78/XslqOndM1UI/AAAAAAAA9tM/DCd1L6IQiREtw78wasssrzbBR9nLnlLugCK4BGAsYHg/land_ocean.png)<div 
class="separator" style="clear: both; text-align: left;">Besides, we cannot 
include Greenland and Antarctic in the global simulation.<div 
class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">Then how can we 
say we can simulate global hydrology without considering these processes?<div 
class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">Many readers may 
argue that what we are dealing with is not actually a science question and I 
heard it many times in my talks.<div class="separator" style="clear: both; 
text-align: left;">Let me explain with a naive example: How can we study the 
Moon? In earlier days, scientists rely on the telescope to observe the surface 
of Moon; later on, we sent sensors to orbit Moon to have a better observation; 
last, we can also collect sample directly once we can land on Moon.<div 
class="separator" style="clear: both; text-align: left;">With the advance in 
space technology, what was impossible becomes possible. <div class="separator" 
style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">Not only what we 
are doing now has many flaws, but also it cannot answer many scientific 
questions.<div class="separator" style="clear: both; text-align: left;">There 
is a difference between can and cannot.<div class="separator" style="clear: 
both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">As I always 
said, Steve Jobs might change the way we use technology, but it is Dennis 
Ritchie who invented C changed the computing world. I personally think Dennis 
Ritchie made it possible that we can now use computers to answer whatever 
science questions we have that rely on computing.<div class="separator" 
style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">Having a unified 
mesh enables us to solute questions that are impossible to answer. For 
example, how does the coastal zone respond to climate change and affects 
population in these areas?<div class="separator" style="clear: both; 
text-align: left;"> 
<div class="separator" style="clear: both;">Low hanging fruits are easy to 
fetch, but it takes way more effort to get the higher ones, which might be 
much better. As a Chinese proverb says: To do a good job, an artisan needs the 
best tools. (工欲善其事，必先利其器.)<div class="separator" style="clear: both; 
text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;"> <div> 