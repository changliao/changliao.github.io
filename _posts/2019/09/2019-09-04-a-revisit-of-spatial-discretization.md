---
layout: post
title: A revisit of spatial discretization
date: '2019-09-04T15:45:00.001-07:00'
author: Chang Liao
tags:
- Spatial Discretization
modified_time: '2019-09-04T15:45:43.363-07:00'
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-584062623971820911
blogger_orig_url: https://changliao.blogspot.com/2019/09/a-revisit-of-spatial-discretization.html
---

<div style="background-color: white; box-sizing: inherit; color: #404040; 
font-family: &quot;Libre Baskerville&quot;, Libre, Georgia, Times, serif; 
font-size: 16px; margin-bottom: 1.75em;">Discretization by definition from 
[Wikipedia](https://en.wikipedia.org/wiki/Discretization): In [applied 
mathematics](https://en.wikipedia.org/wiki/Applied_mathematics), <span 
style="box-sizing: inherit; font-weight: 700;">discretization is the process 
of transferring 
[continuous](https://en.wikipedia.org/wiki/Continuous_function) functions, 
models, variables, and equations into 
[discrete](https://en.wiktionary.org/wiki/discrete) counterparts. This process 
is usually carried out as a first step toward making them suitable for 
numerical evaluation and implementation on digital computers.<div 
style="background-color: white; box-sizing: inherit; color: #404040; 
font-family: &quot;Libre Baskerville&quot;, Libre, Georgia, Times, serif; 
font-size: 16px; margin-bottom: 1.75em;">Now we add “spatial” to the term. The 
first intuitive definition is the <span style="box-sizing: inherit; 
font-weight: 700;">discretization of functions in the spatial domain.<div 
style="background-color: white; box-sizing: inherit; color: #404040; 
font-family: &quot;Libre Baskerville&quot;, Libre, Georgia, Times, serif; 
font-size: 16px; margin-bottom: 1.75em;">There are two elements in this 
description: functions and spatial domain.<div style="background-color: white; 
box-sizing: inherit; color: #404040; font-family: &quot;Libre 
Baskerville&quot;, Libre, Georgia, Times, serif; font-size: 16px; 
margin-bottom: 1.75em;">For functions, we often refer to integral or ODEs/PDEs 
in numerical simulations. If these functions involve with gradient 
information, then they depend on spatial domain, which is how gradient is 
calculated.<div style="background-color: white; box-sizing: inherit; color: 
#404040; font-family: &quot;Libre Baskerville&quot;, Libre, Georgia, Times, 
serif; font-size: 16px; margin-bottom: 1.75em;">For spatial domain, we often 
refer to mesh or grid. And mesh can generally be classified into structured 
and unstructured grid.<div style="background-color: white; box-sizing: 
inherit; color: #404040; font-family: &quot;Libre Baskerville&quot;, Libre, 
Georgia, Times, serif; font-size: 16px; margin-bottom: 1.75em;">In practice, 
we have spent great effects on both aspects of the spatial discretization: 
mesh and corresponding function solvers.<div style="background-color: white; 
box-sizing: inherit; color: #404040; font-family: &quot;Libre 
Baskerville&quot;, Libre, Georgia, Times, serif; font-size: 16px; 
margin-bottom: 1.75em;">In Earth science, lots of functions involve with 
gradient. For example, gas exchange depends on pressure gradient or 
concentration gradient. As a result, Our spatial discretization is always 
associated with mesh grid.<div style="background-color: white; box-sizing: 
inherit; color: #404040; font-family: &quot;Libre Baskerville&quot;, Libre, 
Georgia, Times, serif; font-size: 16px; margin-bottom: 1.75em;">Many studies 
have developed methods to solve equations using the finite difference method 
(FDM), the finite volume method (FVM) and the finite element method (FEM). 
However, many of them have not considered the effects of mesh grid on these 
solvers. For example, most models use array to represent spatial domain. In 
this case, water flow at any location can only flow to 4 directions. However, 
in reality, water can flow to any direction because Earth has no 
discretization. The problem is how can we represent a direction if it is 30 
degree?<div style="background-color: white; box-sizing: inherit; color: 
#404040; font-family: &quot;Libre Baskerville&quot;, Libre, Georgia, Times, 
serif; font-size: 16px; margin-bottom: 1.75em;">We need a better way to 
represent the spatial domain decomposition. We can improve the resolution. We 
can also use unstructured grid such as TIN. Ideally, we need a mesh that 
matches with reality. In my opinion, adaptive hexagon grid mesh is closest.<ul 
style="background-color: white; box-sizing: inherit; color: #404040; 
font-family: &quot;Libre Baskerville&quot;, Libre, Georgia, Times, serif; 
font-size: 16px; list-style-image: initial; list-style-position: initial; 
margin: 0px 0px 1.75em; padding-left: 1.75em;"><li style="box-sizing: 
inherit;">It can cover the sphere.</li><li style="box-sizing: inherit;">It 
proves consistent connectivity.</li><li style="box-sizing: inherit;">It 
provides less assumption.</li><li style="box-sizing: inherit;">It also provide 
6 flow directions.</li><div style="background-color: white; box-sizing: 
inherit; color: #404040; font-family: &quot;Libre Baskerville&quot;, Libre, 
Georgia, Times, serif; font-size: 16px; margin-bottom: 1.75em;">Without a 
solid mesh grid, the simulation which relies on mesh may contain great 
uncertainty. And these uncertainty may be even larger than the uncertainty 
caused by FDM/FVM/FEM and algorithms.<div style="background-color: white; 
box-sizing: inherit; color: #404040; font-family: &quot;Libre 
Baskerville&quot;, Libre, Georgia, Times, serif; font-size: 16px; 
margin-bottom: 
1.75em;">[http://www.thermopedia.com/content/9172/](http://www.thermopedia.com/content/9172/) 