---
layout: post
title: 'Ecosystem modeling: how to deal with the time-variant datasets?'
date: '2016-10-01T11:46:00.000-07:00'
author: Chang Liao
tags:
- DEM
- HPC
modified_time: '2018-04-03T12:16:45.418-07:00'
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-7411748202216670374
blogger_orig_url: https://www.changliao.us/2016/10/ecosystem-modeling-003.html
---

Ecosystem modeling usually requires a variety of data to run a complete 
simulation. These data usually include both time-variant and time-invariant 
datasets. For example, we usually consider Digital Elevation Model (DEM) as 
time-invariant data because surface topography is relatively stable for a 
given period of time unless extreme events such as earthquake occur. 

However, most other driving datasets are actually time-variant. For example, 
climate data (temperature, precipitation.etc.) are constantly changing at any 
given time. 

To date, there is yet no accurate definition whether a data should be defined 
as time-variant or time-invariant. And we always have to make some assumptions 
to simplify our models. 

There are several reasons behind this and how they may be improved in future 
study. 
First, using time-variant data requires more data. For example, for an 
ecosystem model at daily time step, daily climate data are also required. 
While it may be relatively easy to retrieve climate data from meteorology 
sites, it may be much difficult to retrieve other types of data. For example, 
soil data survey usually requires much effort to produce a reliable soil map. 
It is practically impossible to provide soil data at daily time step. 

Second, using time-variant data implies more computational demand and storage 
quota. For large ecosystem models, data preparation and I/O are among the most 
challenging jobs for a successful simulation. 
I will use one of my current projects as an example. For a 40-year simulation, 
I use approximate 6 time-variant datasets include temperature, precipitation 
and vapor pressure. That is 40*365*6=87600 files of matrix. Needless to say 
the additional data produced during the preparation process, that amount of 
data will place certain requirement on the computational power and 
storage.transfer capacity. 

Third, using time-variant data also make the model much more complex and 
complicated. It is obvious the model itself will become much more complex 
since data I/O inside the model will increase significantly. In addition, the 
time-variant data usually imply that some of our components must be flexible 
enough to be compatible with the changes.For example, if the land cover is 
changed due to wild fire within one week, what happens to the soil properties 
during this period? Does the surface albedo change linearly or nonlinear? 

To conclude, there remains many challenges in time-variant datasets related 
subjects. Some of them can be gradually addressed using advanced approaches. 
For example, high performance computer (HPC) are more and more used to address 
the computational demand and storage capacity. Better data structures or 
formats such as HDF/NetCDF are also widely used to improve the data I/O. 

Further, the first step is still to define whether a data is time-variant or 
time-invariant. 
Here I list a brief table to illustrate how I define different data in one of 
my current projects.  <style type="text/css">.tg  
{border-collapse:collapse;border-spacing:0;} .tg td{font-family:Arial, 
sans-serif;font-size:14px;padding:10px 
5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;} 
.tg th{font-family:Arial, 
sans-serif;font-size:14px;font-weight:normal;padding:10px 
5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;} 
.tg .tg-baqh{text-align:center;vertical-align:top} </style> 
<table class="tg">      <th class="tg-baqh">Data</th>    <th 
class="tg-baqh">Time-variant/invariant</th>    <th class="tg-baqh">Note</th>   
   <td class="tg-baqh">Temperature    <td class="tg-baqh">Variant    <td 
class="tg-baqh">Daily      <td class="tg-baqh">Precipitation    <td 
class="tg-baqh">Variant    <td class="tg-baqh">Daily      <td 
class="tg-baqh">Land use and land cover type    <td class="tg-baqh">Variant    
<td class="tg-baqh">Annually, but when extreme event occurs, it can change     
 <td class="tg-baqh">Vegetation type    <td class="tg-baqh">Variant    <td 
class="tg-baqh">Annually, but when extreme event occurs, it can change      
<td class="tg-baqh">Soil type    <td class="tg-baqh">Invariant    <td 
class="tg-baqh">Change only extreme event occurs 