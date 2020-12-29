---
 
title: Another thought on Earth System Model challenge
date: '2018-02-22T17:10:00.000-08:00'
permalink: /posts/2018/02/22/another-thought-on-earth-system-modeling-challenge/
author: Chang Liao
tags:
- System Architecture
modified_time: '2018-04-27T15:50:37.178-07:00'
---

I recent had several discussions with several friends on various topics. Such as whether improving one component with an Earth System Model (ESM) necessarily improve the overall performance.

In the end, I realized that the problem we were discussing is actually very interesting and yet challenge.

To put the question into another perspective, consider the following scenario: if you want to buy a computer, here are three options provided to you:
Some low frequency CPU + 32GB RAM + unknown motherboard;
Some high frequency CPU, i.e. i7 + 1GB RAM + unknown motherboard;
Some average frequency CPU, i.e. i5 + 16 GB RAM + unknown motherboard.
Which one will you pick for daily use? 
Another aspect I also want to point out is that the "unknown motherboard", what if the motherboard does not even support the CPU or RAM frequency?

Let's switch gear back to ESM. Does ESM also have similar issue?
To run a ESM simulation, you have multiple choice of land model, ocean model and atmosphere model. Then you have choice of spatial and temporal resolution. The list goes on.

For each individual model, there are usually hundreds of components. If you take a look at the Community Land Model for example, a list of processes are simulated at depth. 

If you zoom out, you will see that some process is at millisecond level while the ESM is at hourly or monthly temporal resolution. Some process is very local process such as soil biogeochemistry while our simulation spatial resolution is 1.0 degree by 1.0 degree.

Isn't that similar to our struggle with the computer shopping?

Great efforts have been done trying to close this gap but there is still a long way to go. For example, we setup benchmark to study how different models perform under different scenarios. 

While the challenge is that we don't know the role of structure in model performance. A lot of time, we are trying to upgrade i7 to i8 but ignore that we only have 1GB RAM, needless to say that we seldom consider whether the motherboard is the issue. 

This concept is also well-known in management: A bucket can only fill with the volume of water the shortest plank allows. While our computer program can tell us which process consumes most of the computing time, it won't tell us which process is the one affecting the model performance.

With the whole community going forward nearly in parallel, ESM modeler should be aware of this challenge and should not blindly throw whatever progress into the system. Because in the end, it is the shortest one that slows us down.

