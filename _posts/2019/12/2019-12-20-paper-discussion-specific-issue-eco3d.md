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
---
Recently we have published a paper on Journal of Advanced Modeling of Earth System.
https://agupubs.onlinelibrary.wiley.com/doi/abs/10.1029/2019MS001792

This is also a personal milestone because it is the last chapter of my PhD thesis. Below I will provide some details of this work.

In many of my earlier posts, I have discussed that our Earth system is always evolving in a three dimensional domain. The water flows, the atmosphere flows as well.

However, in our numerical simulations, we do not always use 3D method. Sometimes we just don’t felt it necessary. For example, we always assume rain drops on land surface in vertical direction even though rain can attack our windows with an angel.

In some other scenarios, we don’t use 3D because of computational resources. We can build a fully 3D model. But it is not useable if we don’t have the computer power to run it.

Land surface model is an important component in ESM. But current generation of LSM is 1D instead of 3D. There are many reasons for this design, which I plan not to cover here. Instead, I will focus on why 3D makes sense and what is the challenge.

From 1D to 3D means that each grid is aware of its neighborhood. More importantly, it talks to its neighborhood and exchanges maybe gifts.

To put it in the model language, traditionally, each grid is isolated from others, so water and carbon budget are calculated in each grid independently. In 3D, a grid can send or receive some water and carbon from neighborhood. It’s like a grid at mountain valley can receive water from mountain ridge. Isn’t that making much more sense?
On land, each grid cell can connect to its 4/6/8 neighbors:

![Figure 1](https://github.com/changliao/changliao.github.io/blob/main/_figure/flow_cascade.jpg?raw=true)


They can also connect with river:

![Figure 2](https://github.com/changliao/changliao.github.io/blob/main/_figure/land_river_interaction.jpg?raw=true)


Water can carry lots of stuff, including carbon in the dissolved mode. Water can also carry other stuff such as sediment and debris. 



So without 3D, we cannot actually calculate how much stuff are carried by water from one grid to another.

How to implement a 3D approach is another story, in ECO3D, we used a method widely used in the hydrology community, an explicit forward Euler method. There are several advantages of this method. I personally think that it’s suitable for parallel computing and does not require expensive matrix solvers.

We also introduced a brand new DOC model, DOC is one of the carbon that flows with water, apparently. This is currently the only litter DOC model that considers lateral flow.

![Figure 3](https://github.com/changliao/changliao.github.io/blob/main/_figure/litter_doc.jpg?raw=true)

Currently we haven’t consider the DOC in the groundwater system.



Other solutes including particles can also be added and modeled by ECO3D in the near future.

As we have more solutes in the water flow, it’s natural to have biogeochemistry and reactive transport as well.

There are many scientific questions we can answer with this model. But my time is limited so I will slowly try them out in the near future.




