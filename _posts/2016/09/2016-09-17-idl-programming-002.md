---
layout: post
title: 'IDL programming: How to design a simple program'
date: '2016-09-17T08:43:00.002-07:00'
author: Chang Liao
tags:
- IDL
modified_time: '2016-09-17T08:43:17.721-07:00'
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-5292399144623383251
blogger_orig_url: https://changliao.blogspot.com/2016/09/idl-programming-002.html
---

For scientists and engineers, our scripts/programs are usually very straightforward and simple. Even some of us are modelers, our models should be complex but the source code are still manageable.
However, the re-usability of these simple programs are still necessary because a lot of our work must be done over and over again. For example, we need to plot/map some data in various scenarios. And we wants the plot/map program can be used for various types of inputs.

Specially, for IDL programming, there are a few common blocks that should be considered in a program.

Compiler option; this step is usually just for compiling setup, you can also specify it the start-up file.
Error control; some of the most important error information;
Global variable; this step should be used to define the global variable, such as the extension of a file.
Keyword check;
Local variable; this step should be project variable, such as data range.
Workspace; workspace usually refer to the directory all operations will be performance on.
Main: do the actual job.
Post; this is used to finish the program; 
Cleanup; mainly for memory cleanup, (optional)
Another important tip is that do NOT try to finish everything within one program, especially for computationally intensive jobs.

I will provide an example soon.
