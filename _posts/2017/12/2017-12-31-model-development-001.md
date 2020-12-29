---
layout: post
title: How to write a computational climate model with confidence
date: '2017-12-31T19:54:00.000-08:00'
author: Chang Liao
tags:
modified_time: '2018-04-03T12:12:34.371-07:00'
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-3768606601826938284
blogger_orig_url: https://changliao.blogspot.com/2017/12/model-development-001.html
---

I have covered many aspects of climate model related topics so far and I have also discussed quite a few examples in model development. I think it is time to warp up a post to serve as a guidance for whose who may be interested in this field.

In one sentence, if either of the following scenarios fits you, you may find this post useful:
You want to develop a new model, and you don't know where to start with;
You want to modify an existing model and you also have no idea how.
This post will be mainly organized in chronological order with moderate details. For each step, you may have to spend great amount of time but the effort will worth it eventually.
You need to know what question you want to answer and is there promising solution available. This step is generally considered as literature review. But during this process, you have to estimate whether you are capable to address the question under limited resources (time, intelligence, funding, etc.). 
You will also need to send many emails, go to many forums and ask many questions for more comments and suggestions. This will generally help you get a better idea of the challenge of the question you may encounter later and will save you tons of time if you take the right path.
By now, you have an idea of what approach/model you may use. And more than often, you will need to understand the theory and the implementation through source code. Using a model without understanding its principle is dangerous. However, you are not required to read the code line by line. Instead, you should be able to understand the structure and work flow of the model.
If you are developing new models, you have to choose a language. Depending on the question, it may require significant computation demand in climate model simulation, which usually left you with limited options, Fortran or C/C++.
If you are modifying existing model, no choice needed. You learn what is provided.
You will need to learn "makefile". I have seldom seen any large projects without seeing makefile. Makefile makes compiling much easier. And it help you to understand the structure of the model as well.
Whether you are writing from scratch or existing code. You have to do basic code edit, mostly across platforms. Therefore, you will be using different text editor or IDE. On Linux, most likely you will learn Emacs or Vim. On Windows, you can choose Notepad++ or Visual Studio (Code). On macOS, you can use all of them. I use Visual Studio 2017, Visual Studio Code and Emacs for different purposes. 
If you are developing new models, design you model structure carefully so both you and others can understand it easily. Use dependency map (makefile) or Doxygen to provide better illustration. Draw it out on a blackboard is always a good idea.
Write down your design using document such as Word or Latex. When you know it is a pain to look at others' code, you should try not be the "others".
When you start to write, always write comments when necessary.
Find a solution to archive and backup whatever code or data you will produce. Because you will have trouble remembering where you were after the holiday and even Linux servers fail just like PC.
Start with little, compile it, test it before you go big. Use test code to verify your assumption before you actually put them in your code.
Sometimes you have to use multiple computers simultaneously because you had no choice. For example, I have to use ArcGIS (only on Windows) to some spatial dataset analysis. Sometimes you have to use different types of network (VPN) as well. So be prepared.
Develop good programming habits, so you will have less bugs to catch.
You should learn how to debug using GDB, Totalview or even just "print". Knowing some tricks can save you lots of time even you are using HPC. For example, you may use x-win and interactive job to diagnose tough bugs. Debugging a large project on a HPC is a very time consuming job, and you don't want to run a program for 24 hours again and again and still have no clue where is the problem. Use GDB/DDD to analyze the core dump file can save your time.
Write your code with consideration of cross-platform, so you can test code on most platforms.
Ask questions in person or online (Stack overflow, etc), appreciate others when you are helped.
Learn (spatial) data operations. A lots of data in climate change community are spatial dataset such as Geotiff, Netcdf. You should learn the basic structure of them. More importantly, you should learn how to read, write and other operations. For this subject, I recommend ENVI/IDL or ArcGIS. You can also try other open source alternatives. You should learn to operate these data using programming because you will have to deal with massive dataset. You should also choose a file format for data exchange with other systems.
When you are writing the model, be flexible. So other developers or yourself can keep improving it.
Use strategies to catch errors. Keep log file for references.
Take break time to review your model because there is always more than one way to solve a problem.
When you model is almost finished. Share it with others for testing and comments. You can open source it if possible.
Run your model and compare it with other information, or even your own expectation. If something is not right, check the model using debug approach.
Now you see how much efforts/troubles you might get into, but as you go through these processes, you gain more and more experiences and confidences.

Thank you and Happy New Year!