---
layout: post
title: 'High Performance Computing: ParaFly'
date: '2016-10-21T11:20:00.000-07:00'
author: Chang Liao
tags:
- ParaFly
- IDL
- HPC
- OpenMP
modified_time: '2017-09-21T09:46:23.543-07:00'
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-3694223892904686490
blogger_orig_url: https://www.changliao.us/2016/10/high-performance-computing-003.html
---

In my recent posts I shared some first hand experience of parallel computing 
using OpenMP. 
While OpenMP is supported by many programming languages, there are still a few 
does not. So here I am sharing another approach to create a parallel computing 
job. 

The utility I will use is called "ParaFly". There are some information you can 
read [here](http://parafly.sourceforge.net/). 
Basically, ParaFly can be used to run a list of command simultaneously. This 
approach will be particularly useful for some types of jobs in which tasks are 
independent with each other (such as for loop) but take a long time to run. 

In my case, I was using the IDL library to process a huge amount to spatial 
datasets. I will use this job as an example to show how it is done. 

Organically, I have to call a routine: 
PRO project48, extension\_file = ef, \$ 
    filename\_mapinfo, \$ 
    missing\_value, \$ 
    o\_pixel\_size, \$ 
    prefix\_in, $ 
    prefix\_out = po, \$ 
    workspace\_in, \$ 
    workspace\_out, \$ 
    year\_end, \$ 
    year\_start 

to re-project a list of raster image files from 1980 to 2015. 
IDL is known for [inefficient 
](http://www.idlcoyote.com/tips/forloops2.html)in for loop just like MATLAB. 

And it is not easy to parallel IDL on a Linux HPC. You can use C/C++ to call 
IDL with OpenMP enabled if possible, but then you have to write some 
additional program to do the work. You can also use GDAL library to write a 
projection function then you can use OpenMP freely, but that certainly 
requires some efforts. 

However, with ParaFly, we can do the work within a few minutes if you are 
lucky. 
First, we need to add an additional routine to call the above routine, but 
this new routine should accept one parameter, which is time(year), because all 
the other will remain the same. 
Such as: 
;- 
PRO project48_tmax, year 
 COMPILE_OPT IDL2 
  year_start = year 
  year_end = year 
  ;;some other lines are remove here 
  project48, extension_file = file_extension, $ 
    filename_mapinfo, $ 
    missing_value, $ 
    o_pixel_size, $ 
    prefix_in, $ 
    workspace_in, $ 
    workspace_out, $ 
    year_end,$ 
    year_start 
  PRINT, 'Finished!' 
END 

Then the routine is wrapped and ready for ParaFly. 

You may want to write another wrapper to generate the ParaFly file, such as: 
PRO prepare_parafly_files 
  COMPILE_OPT IDL2 
  year_start = 1980 
  year_end = 2015 
  ;;some other lines are remove here 
  FOR year = year_start, year_end, 1 DO BEGIN 
     year_str = STRING(year, format = '(i04)') 
     str = 'idl -e '+ '"' +'project48_tmax, ' $ 
           + year_str + '"' 
     PRINTF, lun, str 
  ENDFOR 
  FREE_LUN, lun 
END 

Then work should be done. 
Theoretically, you can request the whole node with all cores in one job, and 
then gain speed the number of core faster. For example, if I request 10 cores, 
then the program will improve to 10 time faster. 