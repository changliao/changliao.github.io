---
layout: post
title: A visual decomposition of the land grid in the E3SM/CESM model
date: '2018-08-02T14:59:00.003-07:00'
author: Chang Liao
tags:
- ELM
- CIME
- Fortran
- E3SM
- CESM
- CLM
- Grid Decomposition
modified_time: '2018-08-02T23:07:45.471-07:00'
thumbnail: https://lh3.googleusercontent.com/NK5xRYJvo9RsJll8isEANxGUREJvm8rQSW8YuM4LLHByuSW3wIO5bMHW15nzwgP5zqKmXBnKlkv5-O0RQ5iZbcXOI4nszOVLVgzLOaDsibN32vfbo0puI3KqQE9afOQ8LHGEem-4PQG3Ew=s72-c
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-1843711549862235551
blogger_orig_url: https://changliao.blogspot.com/2018/08/model-development-005.html
---

One of my recent development projects needs to exchange several variables 
between different components using the Common Infrastructure for Modeling the 
Earth ([CIME](http://esmci.github.io/cime/)) model. However, different 
components have different grid systems. Therefore, I have to get familiar with 
the grid system of these two component before assigning any variables. 

One of them is the land grid used in Community Land Model 
([CLM](http://www.cesm.ucar.edu/models/clm/))/ELM, which is the land component 
in the Energy Exascale Earth System Model ([E3SM](https://e3sm.org/)) model. 
Because CLM is also part of CESM, this post should also apply to the CESM land 
component. 
<div> 
<div>In short, the land component distributes all the land units across 
multiple nodes/cores and each grid cell is run by clump. 

Here I developed a small Python utility to illustrate the concept. 

First we define a sample problem as follow: 
<div class="separator" style="clear: both; text-align: center;"><div 
class="separator" style="clear: both; text-align: center;"> 
<table id="docs-internal-guid-7bf7207c-fc8e-8b0a-7154-1976a4e94853" 
style="border-collapse: collapse; border: none; text-align: 
center;"><colgroup><col width="159px"></col><col width="66px"></col><col 
width="192px"></col></colgroup><tr style="height: 38px;"><td 
style="border-bottom: solid #9E9E9E 1px; border-left: solid #9E9E9E 1px; 
border-right: solid #9E9E9E 1px; border-top: solid #9E9E9E 1px; 
padding-bottom: 10px; padding-left: 10px; padding-right: 10px; padding-top: 
10px; vertical-align: middle;"><div dir="ltr" style="line-height: 1.2; 
margin-bottom: 0pt; margin-top: 0pt; text-align: center;"><span 
style="font-family: &quot;times new roman&quot;; font-size: 12pt; 
vertical-align: baseline; white-space: pre-wrap;">Variable<td 
style="border-bottom: solid #9E9E9E 1px; border-left: solid #9E9E9E 1px; 
border-right: solid #9E9E9E 1px; border-top: solid #9E9E9E 1px; 
padding-bottom: 10px; padding-left: 10px; padding-right: 10px; padding-top: 
10px; vertical-align: middle;"><div dir="ltr" style="line-height: 1.2; 
margin-bottom: 0pt; margin-top: 0pt; text-align: center;"><span 
style="font-family: &quot;times new roman&quot;; font-size: 12pt; 
vertical-align: baseline; white-space: pre-wrap;">Value<td 
style="border-bottom: solid #9E9E9E 1px; border-left: solid #9E9E9E 1px; 
border-right: solid #9E9E9E 1px; border-top: solid #9E9E9E 1px; 
padding-bottom: 10px; padding-left: 10px; padding-right: 10px; padding-top: 
10px; vertical-align: middle;"><div dir="ltr" style="line-height: 1.2; 
margin-bottom: 0pt; margin-top: 0pt; text-align: center;"><span 
style="font-family: &quot;times new roman&quot;; font-size: 12pt; 
vertical-align: baseline; white-space: pre-wrap;">Description<tr 
style="height: 38px;"><td style="border-bottom: solid #9E9E9E 1px; 
border-left: solid #9E9E9E 1px; border-right: solid #9E9E9E 1px; border-top: 
solid #9E9E9E 1px; padding-bottom: 10px; padding-left: 10px; padding-right: 
10px; padding-top: 10px; vertical-align: middle;"><div dir="ltr" 
style="line-height: 1.2; margin-bottom: 0pt; margin-top: 0pt; text-align: 
center;"><span style="font-family: &quot;times new roman&quot;; font-size: 
12pt; vertical-align: baseline; white-space: pre-wrap;">npes<td 
style="border-bottom: solid #9E9E9E 1px; border-left: solid #9E9E9E 1px; 
border-right: solid #9E9E9E 1px; border-top: solid #9E9E9E 1px; 
padding-bottom: 10px; padding-left: 10px; padding-right: 10px; padding-top: 
10px; vertical-align: middle;"><div dir="ltr" style="line-height: 1.2; 
margin-bottom: 0pt; margin-top: 0pt; text-align: center;"><span 
style="font-family: &quot;times new roman&quot;; font-size: 12pt; 
vertical-align: baseline; white-space: pre-wrap;">4<td style="border-bottom: 
solid #9E9E9E 1px; border-left: solid #9E9E9E 1px; border-right: solid #9E9E9E 
1px; border-top: solid #9E9E9E 1px; padding-bottom: 10px; padding-left: 10px; 
padding-right: 10px; padding-top: 10px; vertical-align: middle;"><div 
dir="ltr" style="line-height: 1.2; margin-bottom: 0pt; margin-top: 0pt; 
text-align: center;"><span style="font-family: &quot;times new roman&quot;; 
font-size: 12pt; vertical-align: baseline; white-space: pre-wrap;">CPU/Node<tr 
style="height: 38px;"><td style="border-bottom: solid #9E9E9E 1px; 
border-left: solid #9E9E9E 1px; border-right: solid #9E9E9E 1px; border-top: 
solid #9E9E9E 1px; padding-bottom: 10px; padding-left: 10px; padding-right: 
10px; padding-top: 10px; vertical-align: middle;"><div dir="ltr" 
style="line-height: 1.2; margin-bottom: 0pt; margin-top: 0pt; text-align: 
center;"><span style="font-family: &quot;times new roman&quot;; font-size: 
12pt; vertical-align: baseline; white-space: pre-wrap;">clump_pproc <td 
style="border-bottom: solid #9E9E9E 1px; border-left: solid #9E9E9E 1px; 
border-right: solid #9E9E9E 1px; border-top: solid #9E9E9E 1px; 
padding-bottom: 10px; padding-left: 10px; padding-right: 10px; padding-top: 
10px; vertical-align: middle;"><div dir="ltr" style="line-height: 1.2; 
margin-bottom: 0pt; margin-top: 0pt; text-align: center;"><span 
style="font-family: &quot;times new roman&quot;; font-size: 12pt; 
vertical-align: baseline; white-space: pre-wrap;">10<td style="border-bottom: 
solid #9E9E9E 1px; border-left: solid #9E9E9E 1px; border-right: solid #9E9E9E 
1px; border-top: solid #9E9E9E 1px; padding-bottom: 10px; padding-left: 10px; 
padding-right: 10px; padding-top: 10px; vertical-align: middle;"><div 
dir="ltr" style="line-height: 1.2; margin-bottom: 0pt; margin-top: 0pt; 
text-align: center;"><span style="font-family: &quot;times new roman&quot;; 
font-size: 12pt; vertical-align: baseline; white-space: pre-wrap;">Core per 
CPU<tr style="height: 38px;"><td style="border-bottom: solid #9E9E9E 1px; 
border-left: solid #9E9E9E 1px; border-right: solid #9E9E9E 1px; border-top: 
solid #9E9E9E 1px; padding-bottom: 10px; padding-left: 10px; padding-right: 
10px; padding-top: 10px; vertical-align: middle;"><div dir="ltr" 
style="line-height: 1.2; margin-bottom: 0pt; margin-top: 0pt; text-align: 
center;"><span style="font-family: &quot;times new roman&quot;; font-size: 
12pt; vertical-align: baseline; white-space: pre-wrap;">nsegspc <td 
style="border-bottom: solid #9E9E9E 1px; border-left: solid #9E9E9E 1px; 
border-right: solid #9E9E9E 1px; border-top: solid #9E9E9E 1px; 
padding-bottom: 10px; padding-left: 10px; padding-right: 10px; padding-top: 
10px; vertical-align: middle;"><div dir="ltr" style="line-height: 1.2; 
margin-bottom: 0pt; margin-top: 0pt; text-align: center;"><span 
style="font-family: &quot;times new roman&quot;; font-size: 12pt; 
vertical-align: baseline; white-space: pre-wrap;">2<td style="border-bottom: 
solid #9E9E9E 1px; border-left: solid #9E9E9E 1px; border-right: solid #9E9E9E 
1px; border-top: solid #9E9E9E 1px; padding-bottom: 10px; padding-left: 10px; 
padding-right: 10px; padding-top: 10px; vertical-align: middle;"><div 
dir="ltr" style="line-height: 1.2; margin-bottom: 0pt; margin-top: 0pt; 
text-align: center;"><span style="font-family: &quot;times new roman&quot;; 
font-size: 12pt; vertical-align: baseline; white-space: pre-wrap;">Segment per 
clump<tr style="height: 38px;"><td style="border-bottom: solid #9E9E9E 1px; 
border-left: solid #9E9E9E 1px; border-right: solid #9E9E9E 1px; border-top: 
solid #9E9E9E 1px; padding-bottom: 10px; padding-left: 10px; padding-right: 
10px; padding-top: 10px; vertical-align: middle;"><div dir="ltr" 
style="line-height: 1.2; margin-bottom: 0pt; margin-top: 0pt; text-align: 
center;"><span style="font-family: &quot;times new roman&quot;; font-size: 
12pt; vertical-align: baseline; white-space: pre-wrap;">nclumps<td 
style="border-bottom: solid #9E9E9E 1px; border-left: solid #9E9E9E 1px; 
border-right: solid #9E9E9E 1px; border-top: solid #9E9E9E 1px; 
padding-bottom: 10px; padding-left: 10px; padding-right: 10px; padding-top: 
10px; vertical-align: middle;"><div dir="ltr" style="line-height: 1.2; 
margin-bottom: 0pt; margin-top: 0pt; text-align: center;"><span 
style="font-family: &quot;times new roman&quot;; font-size: 12pt; 
vertical-align: baseline; white-space: pre-wrap;">40<td style="border-bottom: 
solid #9E9E9E 1px; border-left: solid #9E9E9E 1px; border-right: solid #9E9E9E 
1px; border-top: solid #9E9E9E 1px; padding-bottom: 10px; padding-left: 10px; 
padding-right: 10px; padding-top: 10px; vertical-align: middle;"><div 
dir="ltr" style="line-height: 1.2; margin-bottom: 0pt; margin-top: 0pt; 
text-align: center;"><span style="font-family: &quot;times new roman&quot;; 
font-size: 12pt; vertical-align: baseline; white-space: pre-wrap;">Core 
count<tr style="height: 38px;"><td style="border-bottom: solid #9E9E9E 1px; 
border-left: solid #9E9E9E 1px; border-right: solid #9E9E9E 1px; border-top: 
solid #9E9E9E 1px; padding-bottom: 10px; padding-left: 10px; padding-right: 
10px; padding-top: 10px; vertical-align: middle;"><div dir="ltr" 
style="line-height: 1.2; margin-bottom: 0pt; margin-top: 0pt; text-align: 
center;"><span style="font-family: &quot;times new roman&quot;; font-size: 
12pt; vertical-align: baseline; white-space: pre-wrap;">lni<td 
style="border-bottom: solid #9E9E9E 1px; border-left: solid #9E9E9E 1px; 
border-right: solid #9E9E9E 1px; border-top: solid #9E9E9E 1px; 
padding-bottom: 10px; padding-left: 10px; padding-right: 10px; padding-top: 
10px; vertical-align: middle;"><div dir="ltr" style="line-height: 1.2; 
margin-bottom: 0pt; margin-top: 0pt; text-align: center;"><span 
style="font-family: &quot;times new roman&quot;; font-size: 12pt; 
vertical-align: baseline; white-space: pre-wrap;">20<td style="border-bottom: 
solid #9E9E9E 1px; border-left: solid #9E9E9E 1px; border-right: solid #9E9E9E 
1px; border-top: solid #9E9E9E 1px; padding-bottom: 10px; padding-left: 10px; 
padding-right: 10px; padding-top: 10px; vertical-align: middle;"><div 
dir="ltr" style="line-height: 1.2; margin-bottom: 0pt; margin-top: 0pt; 
text-align: center;"><span style="font-family: &quot;times new roman&quot;; 
font-size: 12pt; vertical-align: baseline; white-space: pre-wrap;">Longitude 
count<tr style="height: 38px;"><td style="border-bottom: solid #9E9E9E 1px; 
border-left: solid #9E9E9E 1px; border-right: solid #9E9E9E 1px; border-top: 
solid #9E9E9E 1px; padding-bottom: 10px; padding-left: 10px; padding-right: 
10px; padding-top: 10px; vertical-align: middle;"><div dir="ltr" 
style="line-height: 1.2; margin-bottom: 0pt; margin-top: 0pt; text-align: 
center;"><span style="font-family: &quot;times new roman&quot;; font-size: 
12pt; vertical-align: baseline; white-space: pre-wrap;">lnj<td 
style="border-bottom: solid #9E9E9E 1px; border-left: solid #9E9E9E 1px; 
border-right: solid #9E9E9E 1px; border-top: solid #9E9E9E 1px; 
padding-bottom: 10px; padding-left: 10px; padding-right: 10px; padding-top: 
10px; vertical-align: middle;"><div dir="ltr" style="line-height: 1.2; 
margin-bottom: 0pt; margin-top: 0pt; text-align: center;"><span 
style="font-family: &quot;times new roman&quot;; font-size: 12pt; 
vertical-align: baseline; white-space: pre-wrap;">10<td style="border-bottom: 
solid #9E9E9E 1px; border-left: solid #9E9E9E 1px; border-right: solid #9E9E9E 
1px; border-top: solid #9E9E9E 1px; padding-bottom: 10px; padding-left: 10px; 
padding-right: 10px; padding-top: 10px; vertical-align: middle;"><div 
dir="ltr" style="line-height: 1.2; margin-bottom: 0pt; margin-top: 0pt; 
text-align: center;"><span style="font-family: &quot;times new roman&quot;; 
font-size: 12pt; vertical-align: baseline; white-space: pre-wrap;">Latitude 
count<tr style="height: 38px;"><td style="border-bottom: solid #9E9E9E 1px; 
border-left: solid #9E9E9E 1px; border-right: solid #9E9E9E 1px; border-top: 
solid #9E9E9E 1px; padding-bottom: 10px; padding-left: 10px; padding-right: 
10px; padding-top: 10px; vertical-align: middle;"><div dir="ltr" 
style="line-height: 1.2; margin-bottom: 0pt; margin-top: 0pt; text-align: 
center;"><span style="font-family: &quot;times new roman&quot;; font-size: 
12pt; vertical-align: baseline; white-space: pre-wrap;">numg<td 
style="border-bottom: solid #9E9E9E 1px; border-left: solid #9E9E9E 1px; 
border-right: solid #9E9E9E 1px; border-top: solid #9E9E9E 1px; 
padding-bottom: 10px; padding-left: 10px; padding-right: 10px; padding-top: 
10px; vertical-align: middle;"><div dir="ltr" style="line-height: 1.2; 
margin-bottom: 0pt; margin-top: 0pt; text-align: center;"><span 
style="font-family: &quot;times new roman&quot;; font-size: 12pt; 
vertical-align: baseline; white-space: pre-wrap;">85<td style="border-bottom: 
solid #9E9E9E 1px; border-left: solid #9E9E9E 1px; border-right: solid #9E9E9E 
1px; border-top: solid #9E9E9E 1px; padding-bottom: 10px; padding-left: 10px; 
padding-right: 10px; padding-top: 10px; vertical-align: middle;"><div 
dir="ltr" style="line-height: 1.2; margin-bottom: 0pt; margin-top: 0pt; 
text-align: center;"><span style="font-family: &quot;times new roman&quot;; 
font-size: 12pt; vertical-align: baseline; white-space: pre-wrap;">Land count 
Then we define the global grid and land mask: 

Before you start to read the numbers, you need to understand the index system 
used in E3SM. 
Even though Fortran is a 
[column-major](https://en.wikipedia.org/wiki/Row-_and_column-major_order) 
language, the E3SM (written in Fortran) stores the global grid using a 
row-major approach. As a result, global grid index starts from left to right 
in memory, same as the land mask (Figure 1). 

Note that yellow square represent clump index, blue square represent land 
index, and red square represents global grid index.<img height="352" 
id="docs-internal-guid-cfc78fda-fc8f-4cab-758a-91d4a1dbdd93" 
src="https://lh3.googleusercontent.com/NK5xRYJvo9RsJll8isEANxGUREJvm8rQSW8YuM4LLHByuSW3wIO5bMHW15nzwgP5zqKmXBnKlkv5-O0RQ5iZbcXOI4nszOVLVgzLOaDsibN32vfbo0puI3KqQE9afOQ8LHGEem-4PQG3Ew" 
width="640" /> 
<div style="text-align: center;">Figure 1. The global ID and land ID map. 

Similar to global grid, clump/core index starts from left to right across 
node/processor. For example, clump 1 is located on the first core on processor 
1 and clump 2 is located on the first core on processor 2. 

Last, we distribute the land grid onto the clumps. All the land grids are 
allocated to clump in order. In the end, a clump may simulate multiple land 
grids which are far away in the spatial domain. For example, the clump 1 
simulates land grid 1, 41 and 81 (circled in yellow in Figure 1 and 2). 
<div style="text-align: center;"><img height="598px;" 
id="docs-internal-guid-e1ad27a7-fc90-2a62-a184-32e152985c10" 
src="https://lh5.googleusercontent.com/2GEbYlp4yVj99-6OsZW1B_Dl_NDGlmrCOZRdmtjiE5zAVKo7410r9TLZCVybR-IG6DvtJIobiqj55-iXhr4ZIg58i_TDRNxI5e1vm4W8mNLsw0KUSKl3jkcH1BiE9R9GLD7hkbSfGBNM7g" 
width="361px;" /> 
Figure 2. The processor, clump and land grid decomposition. 

<div style="text-align: left;"> 
The global grid and land grid is connected through the “gdc2glo” variable, 
which stores what is the land grid index for each clump in order. For example, 
gdc2glo[1] = 125 means that the 125th global grid is the “second” (index 
starting from 0) simulated land grid, which is land grid 41.<div> 
<div>Let me know if you have any question. 
<div> 