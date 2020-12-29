---
layout: post
title: Lessons I have learnt during E3SM development
date: '2019-09-17T17:19:00.000-07:00'
author: Chang Liao
tags:
- ELM
- E3SM
- Snow
- Software Engineer
modified_time: '2019-11-15T10:11:54.868-08:00'
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-7044368689739765316
blogger_orig_url: https://changliao.blogspot.com/2019/09/lessons-i-have-learnt-during-e3sm.html
---


<div>I have been involved with the E3SM development since I joined PNNL as a 
postdoc. Over the course of time, I have learnt a lot from the E3SM model. I 
also found many issues within the model, which reflects lots of similar 
struggles in the lifespan of software engineering. 

Here I list a few major ones that we all dislike but they are around in almost 
every project we have worked on. 

<div style="text-align: center;"><div style="text-align: left;"><li 
style="text-align: left;">Excessive usage of existing framework even it is not 
meant to</li><div style="text-align: left;">Working in a large project means 
that you should **NOT** re-invent the wheels if they are already there. But 
more often, developers tend to use existing data types and functions even when 
they were not designed to do so. The reason is simple: it is easier to use 
existing ones than to create new ones. For example, in E3SM, there was not a 
data type to transfer data between river and land. Instead, developers use the 
data type designed for atmosphere and land to do the job. While it is ok to do 
so, it added unnecessary confusion for future development activities. This 
type of issue is actually easy to fix. So I created a new type and followed 
the pattern of other data type. There are lots of details of course but it is 
the right way to do it.<div style="text-align: left;"> 
<div style="text-align: left;"><li style="text-align: left;">Too many 
temporary solutions</li><div><div style="text-align: left;">Developers usually 
do not want to spend too much time on how to do a task in a sustainable way. 
Instead, developers tend to choose the approach that simply works for now. 
Because we all have lots of deadlines.<div><div style="text-align: left;">Some 
would argue that a working solution is a good solution. While yes and no. For 
a complex Earth system model, some temporary solutions can cause lots of 
issues or production delays because they are not sustainable.  You might have 
to spend way much more time to fix the issues than deal with it from the 
beginning. <div> 
<li style="text-align: left;">Functions can be extremely fragmented if not 
well designed</li><div style="text-align: left;">As a complex model, each 
module within the system is supposed to do only one task. However, modelers 
are often not sure how to discretize the processes. For example, snow dynamics 
involve with calculation of energy balance (solar radiation, ET, etc.). But 
should we update the snow status after each process? What happens when there 
is no snow after we calculated shortwave radiation? 
This challenge is difficult to deal with because it is difficult to have a big 
picture when you have hundreds of processes going on and no one is an expert 
on everything. By the model was released, some algorithms were written decades 
ago and no one really have the resources to keep tracks of everything. 


1. Collaboration requires timely updates 
<div>With many developers working on different branches, it becomes a 
challenge to update all the changes with strong dependency. Ideally, 
development in one branch should not change the behavior of another branch. 
However, in reality, because of the fragmentation and dependency, we have to 
spend great effort to make sure they are compatible with each other.<div> 
<div>I will keep update this list.<div> 
<div> 


<div style="text-align: left;"> 