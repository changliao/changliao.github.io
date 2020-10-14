---
layout: post
title: A workflow for distributed parallel data analysis on HPC with checkpoint
date: '2020-01-29T11:52:00.002-08:00'
author: Chang Liao
tags:
- Python
- HPC
- Checkpoint
- Parallel
- MPI
- Slurm
modified_time: '2020-02-05T20:12:01.202-08:00'
thumbnail: https://1.bp.blogspot.com/-DllSPM6g9BQ/XjHhneeFE8I/AAAAAAAA7S0/DuH9pO0lwcs3ztLb64h8tzWTlSVaE7JTgCLcBGAsYHQ/s72-c/auto-mpi.png
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-2931585619224056034
blogger_orig_url: https://www.changliao.us/2020/01/a-workflow-for-distributed-parallel.html
---

A typical task we do nowadays is to submit a job to the cluster to run some 
data analysis. But there are some limitations we can do as I know, to some 
extend. 

1. Lots of tasks take a long time to run, which means the Walltime must be 
large even with multiple cores; 
1. HPC queue is busy and it takes forever to wait in the queue; 
1. If a job failed, we have to start over; 
<div>Therefore, I have designed a protocol with workflow to resolve these 
issues.<div>1. It uses MPI for parallel computing, so we can make use of 
multiple nodes to speed up; 
1. It provides a checkpoint feature, so it can restart if something went 
wrong; 
1. It supports automate resubmit if the Walltime is not enough. 
<div class="separator" style="clear: both; text-align: center;">[<img 
border="0" data-original-height="1502" data-original-width="1464" height="640" 
src="https://1.bp.blogspot.com/-DllSPM6g9BQ/XjHhneeFE8I/AAAAAAAA7S0/DuH9pO0lwcs3ztLb64h8tzWTlSVaE7JTgCLcBGAsYHQ/s640/auto-mpi.png" 
width="620" 
/>](https://1.bp.blogspot.com/-DllSPM6g9BQ/XjHhneeFE8I/AAAAAAAA7S0/DuH9pO0lwcs3ztLb64h8tzWTlSVaE7JTgCLcBGAsYHQ/s1600/auto-mpi.png)<div 
class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">There are 
several implementations depending on the system. For example, on the SLURM 
system, a recurring job method can be used.<div class="separator" 
style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">This design is 
expected to be able handle normal operations. However, there is a catch. It 
makes some assumption about the work load of individual slave node: it assumes 
that within each walltime, all the slave node should be able to finish the 
task. <div class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">Normally, the 
slave node will receive only a small fraction of the whole task and finish it 
on time. However, if the work load is not uniform, i.e., some nodes may 
experience slow down whereas others are fast, this work could fail.<div 
class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">Ideally, the 
workflow should keep track of individual node status so we can restart failed 
ones easily.<div class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">A get around 
method would be Parafly. If we can physically decompose the task into 
individual tasks, it would be much easily to rerun some slaves.<div> 