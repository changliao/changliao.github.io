---
title: 'Why we need a unified mesh for Earth system model'
date: 2020-05-23
permalink: /posts/2020/05/23/unified-mesh-for-earth-system-model/
tags:
  - Hydrology
  - ESM
---

In many of my early posts, I shared some aspects that why I decided to develop the hexagon based watershed model, HexWatershed. 
But the real motivation lies beyond watershed and I'd like to share some personal motivation why I started this project.

For decades, since human invented computers and hydrologists invented hydrologic models, we rely on computational techniques to simulate hydrologic processes. And these techniques mostly use the structured mesh/matrix to describe the real world. Nearly all of us are familiar with the so-called X-Y-Z 3D domain.

We stand on the shoulder of giants but we seldom question them. 
It is true in earlier days that most of our research activities focus on a catchment scale or plot scale. We have to admit this is important because we need to understand the fine-scale process before we can extrapolate to a larger domain.

We never look at hydrology on a global scale using a global method. Most of us are simply trying to copy the watershed scale method to a global scale without careful evaluations.

That is where the problem comes, our Earth is not a typical X-Y-Z domain, instead, it is a sphere.
Also, our hydrologic processes interact with various components (lake, river, ocean, etc.)

Can we really use the existing method directly on a global scale? Yes and No. We have already seen many cases. But they are far from what we need. 

For example, we cannot fix the land and ocean interaction:
![Figure 1](https://github.com/changliao/changliao.github.io/blob/main/_figure/land_ocean.png?raw=true)


Besides, we cannot include Greenland and Antarctic in the global simulation.

Then how can we say we can simulate global hydrology without considering these processes?

Many readers may argue that what we are dealing with is not actually a science question and I heard it many times in my talks.
Let me explain with a naive example: How can we study the Moon? In earlier days, scientists rely on the telescope to observe the surface of Moon; later on, we sent sensors to orbit Moon to have a better observation; last, we can also collect sample directly once we can land on Moon.
With the advance in space technology, what was impossible becomes possible. 

Not only what we are doing now has many flaws, but also it cannot answer many scientific questions.
There is a difference between can and cannot.

As I always said, Steve Jobs might change the way we use technology, but it is Dennis Ritchie who invented C changed the computing world. I personally think Dennis Ritchie made it possible that we can now use computers to answer whatever science questions we have that rely on computing.

Having a unified mesh enables us to solute questions that are impossible to answer. For example, how does the coastal zone respond to climate change and affects population in these areas?

Low hanging fruits are easy to fetch, but it takes way more effort to get the higher ones, which might be much better. As a Chinese proverb says: To do a good job, an artisan needs the best tools.



 
