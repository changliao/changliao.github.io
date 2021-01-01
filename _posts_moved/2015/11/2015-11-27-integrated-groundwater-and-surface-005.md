---
 
title: 'Integrated groundwater and surface water modeling: how to make use of the
  MODFLOW Listing file'
date: '2015-11-27T19:13:00.001-08:00'
author: Chang Liao
tags:
- MODFLOW
- Groundwater
modified_time: '2015-11-27T19:14:54.927-08:00'
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-7616722114986559361
blogger_orig_url: https://changliao.blogspot.com/2015/11/integrated-groundwater-and-surface-005.html
---

Whatever version of MODFLOW you are using for groundwater modeling, knowing how to make use of the list file can help a lot to understand what you are actually doing.

As the official MODFLOW manual document describes: 
"The Listing File is a key file to which model output is written. As MODFLOW runs, information is written to the Listing File, including much of the input data (as a record of the simulation) and calculated results."
And
"The Listing File includes a summary of the input data read for all packages. In addition, the Listing File optionally contains calculated head and drawdown controlled by layer and time step, and the overall volumetric budget controlled by time step. The Listing File also contains information about solver convergence and error messages. Output to other files can include head, drawdown, and cell-by-cell flow terms for use in calculations external to the model or in user-supplied applications such as plotting programs."

Therefore, the Listing file actually contains a lot of important information.
In my point of view, the Listing file is a critical way to examine some important variables and outputs. I will briefly talk about several usage of the Listing file with a few examples.

First, the Listing file can used to output all types of inputs in a readable way. MODFLOW provides several utilities to read different types of data. One of them would be real array data. However, a lot of time, even you have prepared the right data, it may not be in the right format or right order. The executable program will run anyway, but none of the inputs actually makes any sense. You probably are not aware of these types of situation at all. For example, you were supposed to input the initial head for three layers, and you mistakenly messed up the order of the layers. But the program will not give a red alert at all. However, if you output this inputs into the Listing file, it maybe very easy for you to catch this error. Another good example is that when have used specific storage (Ss) when the the specific yield (Sy) is needed. When you looked the Listing file, you can immediately pinpoint this issue. Again, the program will probably not complain when you gave a unusual value because it is still within the range.

Second, one of the most annoying parts of a successful MODFLOW simulation is the convergence. A lot of time has been wasted trying to converge. In fact, the Listing file contains very useful information for you to debug the problem. By looking at the convergence information, you can easily identify which cell is causing the problem and infer the reasons. You can also look at the volume changes of each terms (e.g. stream leakage) to identify the water balance issue. With appropriate adjustments, you can quickly improve the convergence efficiency using the water balance information.

Comments are welcome! 




