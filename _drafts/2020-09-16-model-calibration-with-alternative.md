---
layout: post
title: Model calibration with alternative options
date: '2020-09-16T15:36:00.007-07:00'
author: Chang Liao
tags:
- Model Calibration
- PyPEST
- Python
modified_time: '2020-09-16T15:37:59.182-07:00'
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-2567172248827693524
blogger_orig_url: https://www.changliao.us/2020/09/model-calibration-with-alternative.html
---

<p> PyPEST is a project that I worked on a little bit last year. I attempted 
to make PEST available to Python developers so model calibration can be easy 
and efficient.</p><p>So far PyPEST supports MACES, SWAT, MODFLOW, PRMS, etc. 
There is still much work needed for testing.</p><p>MACES has a structure much 
like SUMMA 
([https://summa.readthedocs.io/en/latest/configuration/SUMMA_configuration/](https://summa.readthedocs.io/en/latest/configuration/SUMMA_configuration/)).</p><p>During 
run time, the model may use different algorithms for a single process. As a 
results, the model may have many different configurations in 
applications.</p><p>The question is then how we can calibrate a model with 
alternative options. Shall we treat each option as a parameter or not? 
Mathematically, we can certainly do so with some tweak because anything can be 
considered parameter internally. In this way, we may easily pick out the best 
configuration. There are drawbacks as well. For example, when we treat option 
as parameter, the commonly used gradient search and sensitivity analysis will 
be affected. Also, adding them will increase computational demand.</p><p>A 
more realistic strategy is that we can calibrate classified by configuration. 
This will increase the complexity of file system but decrease the complexity 
of parameter control.</p><p>We can then find out the best configuration using 
another global search. This will also enable us to compare the performance 
between configurations.</p> 