---
layout: post
title: Another thought on Earth System Model challenge
date: '2018-02-22T17:10:00.000-08:00'
author: Chang Liao
tags:
- System Architecture
modified_time: '2018-04-27T15:50:37.178-07:00'
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-7982991409561417787
blogger_orig_url: https://www.changliao.us/2018/02/model-development-002.html
---

I recent had several discussions with several friends on various topics. Such 
as whether improving one component with an Earth System Model (ESM) 
necessarily improve the overall performance. 

In the end, I realized that the problem we were discussing is actually very 
interesting and yet challenge. 

To put the question into another perspective, consider the following scenario: 
if you want to buy a computer, here are three options provided to you: 
1. Some low frequency CPU + 32GB RAM + unknown motherboard; 
1. Some high frequency CPU, i.e. i7 + 1GB RAM + unknown motherboard; 
1. Some average frequency CPU, i.e. i5 + 16 GB RAM + unknown motherboard. 
<div>Which one will you pick for daily use? <div>Another aspect I also want to 
point out is that the "unknown motherboard", what if the motherboard does not 
even support the CPU or RAM frequency?<div> 
<div>Let's switch gear back to ESM. Does ESM also have similar issue?<div>To 
run a ESM simulation, you have multiple choice of land model, ocean model and 
atmosphere model. Then you have choice of spatial and temporal resolution. The 
list goes on.<div> 
<div>For each individual model, there are usually hundreds of components. If 
you take a look at the Community Land Model for example, a list of processes 
are simulated at depth. <div> 
<div>If you zoom out, you will see that some process is at millisecond level 
while the ESM is at hourly or monthly temporal resolution. Some process is 
very local process such as soil biogeochemistry while our simulation spatial 
resolution is 1.0 degree by 1.0 degree.<div> 
<div>Isn't that similar to our struggle with the computer shopping?<div> 
<div>Great efforts have been done trying to close this gap but there is still 
a long way to go. For example, we setup benchmark to study how different 
models perform under different scenarios. <div> 
<div>While the challenge is that we don't know the role of structure in model 
performance. A lot of time, we are trying to upgrade i7 to i8 but ignore that 
we only have 1GB RAM, needless to say that we seldom consider whether the 
motherboard is the issue. <div> 
<div>This concept is also well-known in management: A bucket can only fill 
with the volume of water the shortest plank allows. While our computer program 
can tell us which process consumes most of the computing time, it won't tell 
us which process is the one affecting the model performance.<div> 
<div>With the whole community going forward nearly in parallel, ESM modeler 
should be aware of this challenge and should not blindly throw whatever 
progress into the system. Because in the end, it is the shortest one that 
slows us down.<div> 
<div> 