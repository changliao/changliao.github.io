---
layout: post
title: 'Ecosystem modeling: a review on spatial resolution and lateral flow'
date: '2017-03-29T17:01:00.002-07:00'
author: Chang Liao
tags:
modified_time: '2018-04-03T12:19:53.980-07:00'
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-4198598650102904990
blogger_orig_url: https://changliao.blogspot.com/2017/03/ecosystem-modeling-005.html
---

We all agree that lateral flow is important in hydrology, but why most ecosystem models do not consider lateral flow?

The answer is usually related to spatial resolution. In a large scale or global scale GCM model simulation, the spatial resolution is usually $0.5^{\circ} \times 0.5^{\circ}$. At this resolution, lateral flow is usually negligible compared with vertical fluxes.

However, this procedure usually causes problems in mass balance. First, without lateral flow, freshwater into the ocean cannot be estimated accurately. Second, dissolved nutrients into the oceanic systems cannot be estimated.

So the question is at what resolution do we actually MUST consider lateral flow?

The answer depends on the fluxes you are looking into. For example, if you are looking into water flow, it it more than likely you have to always consider it, especially at regional scale. If you are looking into carbon/nitrogen fluxes, the problem will become slightly complicated.

First, we will need to evaluate what lateral fluxes are expressed in equations.
For water flow in a simplified grid cell:

$
\begin{align}\frac{\partial Water}{\partial t} & = Rain + Snowmelt  - Evaportranspiration \\
& + Groundwater_{upwelling} - Groundwater_{recharge} \\
& + Runoff_{in} - Runoff_{out}
\end{align}
$

For carbon fluxes:

$
\begin{align}\frac{\partial C_{pool}}{\partial t} & = Photosynthesis\\
& - Resipiration_{autotrophic}  -  Resipiration_{heterotrophic} \\
& +  Carbon_{in} - Carbon_{out}
\end{align}
$

Due to the fact that terms on the right hand side are often associated with water condition, it is therefore difficult to determine how sensitive these processes are affected by lateral flow. For example, if photosynthesis algorithm is based on soil moisture, it is likely Photosynthesis maybe affected by lateral flow, but the uncertainty range could be within $5\%$ or more. Or dissolved carbon that flows through water flow is about $1\%$ of the other terms.

Therefore, it is our responsibility to check how sensitive our models/algorithms are to the lateral flow. So far, I have not seen much work conducted in this direction. I am planning to conduct some research using my three-dimensional ecosystem modeling.




