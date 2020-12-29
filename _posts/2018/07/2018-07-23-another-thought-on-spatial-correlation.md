---
 
title: Another thought on spatial correlation between two spatial datasets
date: '2018-07-23T18:46:00.000-07:00'
permalink: /posts/2018/07/23/thoughts-on-spatial-correlation/
author: Chang Liao
tags:
modified_time: '2018-07-23T18:46:52.114-07:00'
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-6487559763227996117
blogger_orig_url: https://changliao.blogspot.com/2018/07/another-thought-on-spatial-correlation.html
---

This has been a question which I didn't find a perfect answer for years: 
How to express that two maps are correlated in a mathematic way? 

I also noticed that someone has asked this question in the ResearchGate 
community: 
https://www.researchgate.net/post/How_to_statistically_compare_two_maps 

I came into this question when my mentor asked me to provide some correlation 
coefficient for the statement in my paper. Then I have to think how I can 
actually calculate the coefficient. 

For year, whenever someone talk about correlation efficient, it usually refers 
to the the Pearson correlation coefficient: 
https://en.wikipedia.org/wiki/Pearson_correlation_coefficient 
The Pearson correlation coefficient, however, does not care or specify what 
kind of data you are dealing with. 
There are many other different ways to calculate and express correlation, but 
they are more or less similar. 

In Earth science, most data we are dealing with are time series data and 
spatial data. In GIS, theoretically a data is meaningless if it does not have 
the location. 

To simplify our problem, especially for researcher not familiar with GIS, the 
location information is often ignored. And in some cases, time is not 
important as well. 

For example, we can calculate the correlation between the weight and height of 
people without time and location. 

In some cases, time is an invisible hand in fact. For example, we are supposed 
to measure the weight and height simultaneously or close enough. So even time 
is not a factor in the equation, it is an important factor in the experiment. 

But what happens when we add location information, such as a map? 
What if a map is a vector, such as the state map? Let's define it as Type A. 
What if a map is a raster, such as temperature/elevation? Let's define it as 
Type B. 
Some map is raster, but it has been artificially defined, such as soil type 
and vegetation type. Let's define it as Type C. 