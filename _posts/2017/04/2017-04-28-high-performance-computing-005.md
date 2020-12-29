---
layout: post
title: 'High performance computing: data management'
date: '2017-04-28T23:02:00.000-07:00'
author: Chang Liao
tags:
- Data Management
- HPC
- Cluster
modified_time: '2017-04-28T23:06:53.138-07:00'
thumbnail: https://3.bp.blogspot.com/-VxTbGCA6EPM/WQFyP9oanJI/AAAAAAAAWeQ/Msspk3l8GMI8goLddzydB9kP_GfwvoUBQCLcB/s72-c/tree.JPG
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-2826427237579333687
blogger_orig_url: https://changliao.blogspot.com/2017/04/high-performance-computing-005.html
---

When you leave a position, such as graduation from university, you usually 
have to backup lots of data, which is usually considered as one critical step 
in data management. 

In general, data management is an important process in all scientific research 
activities. Without proper data management, research activity efficiency may 
be influenced. In extreme cases, you may lose valuable data due to poor data 
management. In some cases, it could be regarded as research misconduct as 
well. 

Data management itself can be a project from my perspective, especially when 
you have to deal with massive amount of data across different platforms. 

In my case, I need to manage different types of data under different 
environments, I will first introduce the data formats that I am dealing with, 
then I will introduce the file system that will be used to manage the data. 

In Earth system research, data usually can be classified based on various 
dimensions. 
Based on data properties, these dimensions can be raster/vector, 
spatial-temporal resolutions, dateset content, etc. Ideally, you can choose 
any of them as index and store the data in a typical file system. 
However, bearing in mind that complex tree structure will also decrease the 
performance of data I/O. 

I plan not go to much details, and I will directly provide the structure I am 
using currently. 
In my case, I usually prefer to use "auxiliary", "raster" and "vector" at the 
first level. 

Under the second level, there are data from different sources such as MODIS 
and NCDC. 

Under the third level , there are different products from corresponding 
sources. For example, if the source is MODIS, they could be "mcd12q1" and 
"mod17a2". 

Under the fourth level, there are several sub-directory for different 
purposes. 

In the last level, time becomes the index. Simply, sub-directories will be 
named as "2001", "2002" in chronological order. 

The whole structure can be illustrated in one single picture: 
<div class="separator" style="clear: both; text-align: center;">[<img 
border="0" 
src="https://3.bp.blogspot.com/-VxTbGCA6EPM/WQFyP9oanJI/AAAAAAAAWeQ/Msspk3l8GMI8goLddzydB9kP_GfwvoUBQCLcB/s1600/tree.JPG" 
/>](https://3.bp.blogspot.com/-VxTbGCA6EPM/WQFyP9oanJI/AAAAAAAAWeQ/Msspk3l8GMI8goLddzydB9kP_GfwvoUBQCLcB/s1600/tree.JPG)<div 
class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">There are 
several reasons why this structure may improve data management efficiency.<div 
class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both;">First,  for HPC which use 
hierarchical file system as storage system, the more complex the tree 
structure is, the more time it will spend on data I/O. This is also the reason 
why [object storage](https://en.wikipedia.org/wiki/Object_storage) is becoming 
popular in recent years. <div class="separator" style="clear: both;"> 
<div class="separator" style="clear: both;">Therefore, we want to minimize the 
complexity of hierarchical structure while maintain the readability of data 
information.<div class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">For archive 
purpose, Linear Tape File System 
([LTFS](https://en.wikipedia.org/wiki/Linear_Tape_File_System)) based storage 
systems are also used in my research. Even though LTFS is designed for large 
files, we usually do not want to throw everything into one single archive file 
([TAR](https://en.wikipedia.org/wiki/Archive_file)). The good news is that 
LTFS has maintained the hierarchical concept, so we can manage TAR files using 
the same hierarchical structure. It is also very convenient to update or 
modify the archives.<div class="separator" style="clear: both; text-align: 
left;"> 
<div class="separator" style="clear: both; text-align: left;">If you look at 
the filename format from MODIS dataset such as this one:<div class="separator" 
style="clear: both; text-align: left;">"*<span style="color: 
blue;">MCD12Q1.A2001001.h00v08.051.2012157220450.hdf*", you may also notice 
that a better filename design can also help you to manage and distribute data. 
But that is out of the scope for now. Details the example filename can be 
found [here](https://modis-atmos.gsfc.nasa.gov/products_filename.html).<div 
class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">So far I haven't 
tested whether a geospatial database could further improve the data 
management. Since our numerical simulations need to access data, I think the 
complete data I/O flow will be changed and therefore may benefit from the 
changes. If you have any experience in this, feel free to comment.<div 
class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;"> 