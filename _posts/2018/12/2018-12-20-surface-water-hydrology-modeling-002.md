---
layout: post
title: The hydrology in the real world
date: '2018-12-20T11:35:00.000-08:00'
permalink: /posts/2018/12/hydrology-in-reality/
author: Chang Liao
tags:
- Hydrology
- Stream
- Hydrological Modeling
- ESM
- Lake
modified_time: '2018-12-20T11:35:45.297-08:00'
thumbnail: https://2.bp.blogspot.com/-1LGwiKKcmgM/W-IoPAUByDI/AAAAAAAAvhg/IsE7EUPz5xANlZBw1v0yJvVgcwTckIZ5gCLcBGAs/s72-c/lake_stream.png
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-4034854503329152695
blogger_orig_url: https://changliao.blogspot.com/2018/12/surface-water-hydrology-modeling-002.html
---

Below is a region of interest from Global Lakes and Wetlands Database (link). 


![Figure 1](https://github.com/changliao/changliao.github.io/blob/main/_figure/lake_stream.png?raw=true)

My question is how can we represent them in the Earth System Model?

To understand the challenge, we need to know how hydrology features are represented in current modeling work.

In an ideal scenario when there is no lake, stream network are the dominant hydrology features.
To date, most existing hydrology simulations are conducted at relatively large spatial domain. As a result, the spatial resolution of such simulation is limited to hundred to thousand of meters. Sometimes it is impossible to capture some features under this resolution.

On the other hand, the land is never homogeneous and lots of local depressions are visible. These local depressions are removed in most hydrological model.

When there are lakes, the situation gets complicated. There are several challenges we will face:
A lake may changed its boundary depending on water storage;
A lake may or may not have an outlet;
A lake itself is a local depression, so should we remove it or not?
I will provide more details in the near future how we can consider lake in a Earth System Model.



