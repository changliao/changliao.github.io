---
 
title: A modern way of automate calibration of a hydrologic model
date: '2018-11-23T00:06:00.000-08:00'
permalink: /posts/2018/11/23/modern-way-automate-calibration/
author: Chang Liao
tags:
- Model Calibration
- Python
- PEST
- SWAT
modified_time: '2019-01-17T17:22:52.356-08:00'
---

Calibration of hydrologic model can be tedious, that is why we spent great efforts to automate this process. And sometimes we need some tool that is universal, reusable, so that we don't have to re-invent the wheel again and again.

Today I want to introduce a very effective framework to conduct a hydrologic model calibration. I call it framework because you can apply this method to any model and use any of your preferred language in some steps.

Here is the framework:

![Figure 1](https://github.com/changliao/changliao.github.io/blob/main/_figure/pypest_interface.png?raw=true)

Let me explain what is going on:


PEST generate new parameter file based on a simple template;
PEST call Python interface to start model simulation;
Python interface translates parameter file to model input files;
Python interface launches SWAT simulation;
Python interface extracts results; and
PEST analyzes result and updates parameters.

A few highlights here:
This is an example for a SWAT model, and you can change it to any model you are calibrating;
I used Python, but you can also use any other language such as C/C++ or even bash;
I used PEST, this is the only requirement you cannot find many good alternatives.
You can launch as many SWAT simulations as you want in parallel manner.
Here are some more details:
PEST is a model-independent parameter estimation package. You are welcome to check its user manual to obtain its mathematical background. One of the highlights is that it supports both local and global optimization.

PEST is very flexible when it interacts with model I/O, however, it is still not convenient enough. For example, if the model produces binary result instead of text-based, it won't work well.

If you only use PEST without the interface, you will have something like this:


The differences and difficulties are:
You will have to prepare 10-100 times more template files depending on the model complexity;
You will have to read the results directly using PEST in a much more complicated way;
You may have trouble with slave directory forwarding because no all model I/O are friendly designed.

That is why I introduced Python as an interface between model simulation and PEST. Python can be considered as an agent to prepare simulation and extract final results for PEST simulation. It can also speed up your final analysis if the optimization is finished!

If you have noticed, this method is also cross platform ready and it support parallel computing/calibration.

Let me know if you have any question.

