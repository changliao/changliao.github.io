---
layout: post
title: The journey of a three-dimensional ecosystem model debugging and calibration
date: '2018-06-05T15:06:00.000-07:00'
author: Chang Liao
tags:
- Model Calibration
- ThinLinc
- Debugging
- ECO3D
- OpenMP
- Totalview
modified_time: '2018-06-05T17:17:46.775-07:00'
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-7219511816372552984
blogger_orig_url: https://www.changliao.us/2018/06/model-development-004.html
---

Currently I am working on the model development, debugging and calibration of 
the [ECO3D](http://www.eco3d.net/) model. 

Due to the model complexity, I have spent great efforts to get things done in 
an appropriate way. Throughout the process, I have also acquired much 
experiences in model developments. Here I want to share some of the most 
useful tips. However, I will not discuss the technical aspects such as program 
language unless inevitable. 
1. You may use OpenMP to speed up the program, but it appears that the 
debugger, such as the one I use, 
[Totalview](https://www.roguewave.com/products-services/totalview), is not 
quite friendly when debugging in multiple-thread. So I suggest you can prepare 
two versions of CMakeList files, so you can switch between for different 
purposes; 
1. Use conditional breakpoint in Totalview can save you some time when you are 
only interested in certain point/condition; 
1. Ecosystem models, or Earth system models, require a 
"[spin-up](http://www.changliao.us/2017/09/numerical-simulation-001.html)" 
simulation, which usually takes a great length of time ranging from hours to 
days. So you don't want to do it every time when you test your model. To save 
time as well as HPC resources, we can save the steady state system state 
variables into files so we can restart from them to avoid repeated running; 
1. If your simulation objects are independent with each other under certain 
assumption, for example, the shortwave radiation of one pixel is independent 
with nearby pixels, you can speed up the debugging by shutting down/mask out 
the other "useless" pixel. In this way, you can focus on the only pixel that 
gives you troubles; 
1. In other scenarios, such as the cascade/lateral flow simulation, there is 
no way to test the model without a complete simulation because pixels are 
communicating with each other. Even though we have to run all the pixels, that 
doesn't mean we have to output them, and we can still output single pixel for 
debug purpose; 
1. Some debugging information is useful for us to diagnose the problem. Often 
we can output (print, cout, etc.) the information directly on the terminal 
because it is the default I/O. We can also output them to a CSV file, so we 
can check the time series trend easily using Microsoft Excel. Having a deep 
understanding of the trend definitely help you understand what is causing the 
changes; 
1. Even on the most powerful HPC which provides a debug queue, the walltime 
(less than an hour?) is not enough for debugging. So we have to use queue with 
long walltime to debug. Also, because GUI debug causes a lot of 
communications, you should use Remote desktop hosted on HPC 
([ThinLinc](https://www.cendio.com/thinlinc/what-is-thinlinc), etc.) instead 
of local X windows. You should run the debug as an interactive job for as long 
as the debugging requires; 
1. Use debug flag control the workflow efficiently, so you don't have to 
recompile your program every time you change something; 
1. Before you draw any conclusion about the algorithm, double check the input 
file with care. Lots of time we made assumptions about input data that are not 
true. Sometimes you can manually modify/create some input for testing purpose; 
1. Be consistent with some logical controls, if you change some important 
control, remember to check all the related ones. If some variables are used 
across modules, you should be even more careful; 
1. Keep more than one copy of the workspace with the same file system 
structure to speed up some checking processes. Both ftp/sftp and GUI tools can 
be used for data transfer. If you have to transfer large amount of data, 
consider [Globus](https://www.globus.org/). 
<div>Let me know if you have any questions. 