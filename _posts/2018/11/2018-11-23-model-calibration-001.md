---
layout: post
title: A modern way of automate calibration of a hydrologic model
date: '2018-11-23T00:06:00.000-08:00'
author: Chang Liao
tags:
- Model Calibration
- Python
- PEST
- SWAT
modified_time: '2019-01-17T17:22:52.356-08:00'
thumbnail: https://1.bp.blogspot.com/-uZpEf9f3jrU/XEEmg5bm2kI/AAAAAAAAwYo/_Xc3ZY6PmNc5Nm6FUVq2oAvT4j_AzlFAACLcBGAs/s72-c/interface.png
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-3571558200441514084
blogger_orig_url: https://changliao.blogspot.com/2018/11/model-calibration-001.html
---

Calibration of hydrologic model can be tedious, that is why we spent great 
efforts to automate this process. And sometimes we need some tool that is 
universal, reusable, so that we don't have to re-invent the wheel again and 
again. 

Today I want to introduce a very effective framework to conduct a hydrologic 
model calibration. I call it framework because you can apply this method to 
any model and use any of your preferred language in some steps. 

Here is the framework: 
<div class="separator" style="clear: both; text-align: center;"><div 
class="separator" style="clear: both; text-align: left;">Let me explain what 
is going on:<div class="separator" style="clear: both; text-align: 
center;">[<img border="0" data-original-height="434" data-original-width="551" 
src="https://1.bp.blogspot.com/-uZpEf9f3jrU/XEEmg5bm2kI/AAAAAAAAwYo/_Xc3ZY6PmNc5Nm6FUVq2oAvT4j_AzlFAACLcBGAs/s1600/interface.png" 
/>](https://1.bp.blogspot.com/-uZpEf9f3jrU/XEEmg5bm2kI/AAAAAAAAwYo/_Xc3ZY6PmNc5Nm6FUVq2oAvT4j_AzlFAACLcBGAs/s1600/interface.png)<div 
class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">1. PEST generate 
new parameter file based on a simple template; 
1. PEST call Python interface to start model simulation; 
1. Python interface translates parameter file to model input files; 
1. Python interface launches SWAT simulation; 
1. Python interface extracts results; and 
1. PEST analyzes result and updates parameters. 

<div>A few highlights here: 
1. This is an example for a SWAT model, and you can change it to any model you 
are calibrating; 
1. I used Python, but you can also use any other language such as C/C++ or 
even bash; 
1. I used PEST, this is the only requirement you cannot find many good 
alternatives. 
1. You can launch as many SWAT simulations as you want in parallel manner. 
<div>Here are some more details:<div>PEST is a model-independent parameter 
estimation package. You are welcome to check its user manual to obtain its 
mathematical background. One of the highlights is that it supports both local 
and global optimization.<div> 
<div>PEST is very flexible when it interacts with model I/O, however, it is 
still not convenient enough. For example, if the model produces binary result 
instead of text-based, it won't work well. 

If you only use PEST without the interface, you will have something like this: 
<div class="separator" style="clear: both; text-align: center;">[<img 
border="0" data-original-height="434" data-original-width="551" 
src="https://3.bp.blogspot.com/-flrnODAkcQM/XEEnBDRIr7I/AAAAAAAAwY4/TVD3Dtd-JnEhcuQU5uH3LGwYQ_oY37JgACLcBGAs/s1600/interface_old.png" 
/>](https://3.bp.blogspot.com/-flrnODAkcQM/XEEnBDRIr7I/AAAAAAAAwY4/TVD3Dtd-JnEhcuQU5uH3LGwYQ_oY37JgACLcBGAs/s1600/interface_old.png)<div 
class="separator" style="clear: both; text-align: left;"> 
The differences and difficulties are: 
1. You will have to prepare 10-100 times more template files depending on the 
model complexity; 
1. You will have to read the results directly using PEST in a much more 
complicated way; 
1. You may have trouble with slave directory forwarding because no all model 
I/O are friendly designed. 
<div> 
<div>That is why I introduced Python as an interface between model simulation 
and PEST. Python can be considered as an agent to prepare simulation and 
extract final results for PEST simulation. It can also speed up your final 
analysis if the optimization is finished!<div> 
<div>If you have noticed, this method is also cross platform ready and it 
support parallel computing/calibration.<div> 
<div>Let me know if you have any question. 