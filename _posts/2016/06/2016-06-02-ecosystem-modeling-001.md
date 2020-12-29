---
layout: post
title: 'Ecosystem modeling: a question of chicken or eggs?'
date: '2016-06-02T07:31:00.001-07:00'
author: Chang Liao
tags:
- CLM
modified_time: '2018-04-03T12:22:49.136-07:00'
thumbnail: https://4.bp.blogspot.com/-R2WBK34TFOA/V1BBCwtldnI/AAAAAAAAOsA/o1Zqg-RR_W0InGHvaIjaefoGlASqO6rggCLcB/s72-c/clm.png
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-8391579013067800750
blogger_orig_url: https://changliao.blogspot.com/2016/06/ecosystem-modeling-001.html
---

Ecosystem modeling generally include three conceptual components: inputs, algorithm and outputs.
For example, we usually need precipitation to estimate surface runoff.
On the other hand, sometimes some outputs are also considered as inputs for other models. For example, vegetation dynamics also change the surface albedo and therefore the incoming radiation.
In another word, the feedback among different processes are often too complex that we generally have to ignore some feedback processes.

The reason is that our computer simulation MUST have a starting point and a sequence of algorithms in order to run the simulation.
For some well-designed models, the differences between different starting points are not significant when using the numerical approach. However, it is a best practice to put all the algorithms in the right orders.

![Figure 1](https://github.com/changliao/changliao.github.io/blob/main/_figure/clm_process.png?raw=true)



For example, in surface hydrology, the generally order of the water flow is like this: precipitation->interception->snow->infiltration->overland runoff->stream flow, etc. In some case, groundwater also plays a role in this process.
If you map these processes to the actual physical world, these processes occur in the following places: atmosphere->canopy->land surface->soil->stream channel. etc.
Therefore, even though most of the processes occur simultaneously, we still need to break them down due to the time discretization scheme. If you have input data at a second resolution, following above order will not produce any different outputs compared with a different order. But if the time resolution is daily, monthly, or annually, the differences will increase significantly.

Even though the algorithms are placed under a logic order such as water flow, how to design them in a computer program remains unclear. First, in most computer program developments, dependency relationship among components do not always reflect these logical orders. For example, a typical vegetation is consist of canopy, stem and root. However, processes occur in these parts are usually at different time scale and environmental conditions, which makes the dependency relationship of these processes are usually much distorted in computation programs.

I will provide a real live example for review here:
The Community Land Model (CLM) is a widely used ecosystem model.
The core part of the processes simulated has a following order in CLM 4.0.


On the left are the names of the processes or modules, on the right are brief description of them. It appears that the general workflow is from top to bottom. But the question remains unresolved, whether this is the appropriate order for all of these processes. For example, what if the albedo is estimated ahead of the soil flux since energy budget will be potentially different if albedo chanages from snow are considered.