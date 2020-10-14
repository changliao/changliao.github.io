---
layout: post
title: 'Numerical simulation: unit system'
date: '2016-06-29T19:20:00.000-07:00'
author: Chang Liao
tags:
- NCDC
modified_time: '2018-04-03T12:21:33.257-07:00'
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-7624787636918173850
blogger_orig_url: https://www.changliao.us/2016/06/numerical-simulation-000.html
---

Unit is always one of the most important factors in science. Most of the time, 
a number without unit is useless. 
For numerical simulation, a good design of unit system can be critical. 
Recently, I have written a short script/program to prepare climate data for my 
groundwater/surface water hydrology simulation. I downloaded some data from 
the National Climatic Data Center([NCDC](http://www.ncdc.noaa.gov/)) 
separately, and I did NOT notice the changes in unit system. In the end, I 
have to do everything over again. 

So the question is: what kind of unit system should we use to improve our 
efficiency, and how do we actually implement it? 

First of all, we need to identify the unit system used in the data obtained 
from third party. This is usually done through reading the meta data in the 
documentation. Never directly use the data without reading the documentation! 
A lot of time we don't usually have choices of the unit system provided. In 
this case, the best practice might be stick with the original unit system. 

However,  we should use the SI unit system whenever possible. They are 
apparently a few benefits from it. For example, NCDC climate data online 
usually provide standard unit and metric unit system. In this scenario, I 
would prefer to use metric. And you can always convert them into other units 
without much efforts. 

When we implement related numerical simulation program, using SI unit system 
for data I/O is also very straightforward. For some type of data, a scale 
factor can easily preserve the precision without losing efficiency. In modern 
programming language, the double floating data type can handle almost all type 
of data without memory issues. 

Even when you are dealing with old algorithms which use standard unit system, 
you can always convert the units before actual calculations, and convert them 
back to SI afterwards. 

Below is the unit system used in one of my recent projects: 
<table border="1" bordercolor="black" cellpadding="3" cellspacing="3" 
style="background-color: white; width: 
100%;"><th>Data</th><th>Unit</th><th>Note</th><td>Temperature<td>Fahrenheit<td>It 
could be reproduced in Kelvin<td>Precipitation<td>Millimeter<td><td>Dewpoint 
temperature<td>Fahrenheit<td> 