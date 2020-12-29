---
layout: post
title: 'High Performance Computing: Download and prepare data in a batch mode'
date: '2017-01-13T13:15:00.001-08:00'
author: Chang Liao
tags:
- Linux
- Wget
- HPC
modified_time: '2019-03-24T21:12:14.135-07:00'
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-7284276323195921217
blogger_orig_url: https://changliao.blogspot.com/2017/01/high-performance-computing-004.html
---

<div class="MsoNormal" style="line-height: normal; margin-bottom: .0001pt; 
margin-bottom: 0in;"><div style="margin-bottom: .0001pt; margin: 0in;"><span 
style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">Over the time, I need to manipulate a lot of data on a Linux cluster. 
Some of these manipulations actually read/write data, whereas some are 
essentially file system operations, such as downloading the files. 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">Here I present a list of similar operations suitable for HPC using pbs 
job approach whenever possible. 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">I do not attempt to include all possible methods but only the ones 
that I find useful and easy to prepare in seconds. 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">**Download** 
<span style="font-family: Times, Times New Roman, serif;">The most efficient 
way to download MODIS alike data using HPC. 
<span style="font-family: Times, Times New Roman, serif;">wget -r --no-parent 
-R "index.html*" --retr-symlinks -A "*.nc" ftp-url 
<span style="font-family: Times, Times New Roman, serif;">wget -r --no-parent 
-R "index.html*" -A "MOD17A2.A2000*.hdf" -A "MOD17A2.A2000*.xml" http-url 
<span style="font-family: Times, Times New Roman, serif;">wget -r --no-parent 
-R "index.html*" -A "MOD17*.hdf" -A "MOD17*.xml" http-url 
<span style="font-family: Times, Times New Roman, serif;">You can basically 
setup filter for file type, year and granule id. 
<span style="font-family: Times, Times New Roman, serif;">A live example: 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">///========================================================== 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">#!/bin/bash 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">#PBS -l nodes=1:ppn=1 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">#PBS -l naccesspolicy=singleuser 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">#PBS -l walltime=40:00:00 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">#PBS -M your email address 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">#PBS -m ae 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">#PBS -N download 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">#PBS -q standby 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">cd $PBS_O_WORKDIR 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">wget -r --no-parent  -R "index.html*"   --retr-symlinks  -A "*.tar" 
ftp://somwhere 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">///========================================================== 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;"><span style="font-family: &quot;arial&quot; , sans-serif;"> 
<span style="font-family: &quot;arial&quot; , sans-serif;">**Compress and 
extract ** 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">Examples: 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">///========================================================== 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">#!/bin/bash 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">#use this script to extract tar files under the sub directory 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">for dir in `find -mindepth 1 -maxdepth 1 -type d` 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">do 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">    cd $dir 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">    echo $dir 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">    tar xf *.tar ./ 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">    cd .. 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">done 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">///========================================================== 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">#!/bin/bash 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;"># Pass the name of the file to unpack on the command line $1 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">for file in *.gz 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">do 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">    gunzip -d "$file" 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">done 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">///========================================================== 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;"><span style="font-family: &quot;arial&quot; , sans-serif;"> 
<span style="font-family: &quot;arial&quot; , sans-serif;">**Search** 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">grep -rnw '/path/to/somewhere/' -e "pattern" 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">find . -maxdepth 1 -name "*string*" -print<span style="font-family: 
&quot;times&quot; , &quot;times new roman&quot; , serif;"><span 
style="font-family: &quot;arial&quot; , sans-serif;"> 
<span style="font-family: &quot;arial&quot; , sans-serif;">**Comiple** 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">make &amp;&gt; results.txt 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;"><span style="font-family: &quot;arial&quot; , sans-serif;"> 
<span style="font-family: &quot;arial&quot; , sans-serif;">**Count** 
<span style="font-family: &quot;arial&quot; , sans-serif;"><span 
style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">find . -name '*.cpp' | xargs wc -l 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;"><span style="font-family: &quot;arial&quot; , sans-serif;"><span 
style="font-family: &quot;arial&quot; , &quot;helvetica&quot; , sans-serif;"> 
<span style="font-family: &quot;arial&quot; , sans-serif;"><span 
style="font-family: &quot;arial&quot; , &quot;helvetica&quot; , 
sans-serif;">**Debug** 
<span style="font-family: &quot;arial&quot; , sans-serif;"><span 
style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;">qsub -I -lnodes=1:ppn=20 -lwalltime=04:00:00 -q boss  -X 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;"><span style="font-family: &quot;arial&quot; , sans-serif;"> 

<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;"><span style="font-family: &quot;times&quot; , &quot;times new 
roman&quot; , serif;"><span style="font-family: &quot;times&quot; , 
&quot;times new roman&quot; , serif;">Simply organize these above bash script 
and replace with commands, most file system related tasks can<span 
style="font-family: &quot;times&quot; , &quot;times new roman&quot; , serif;"> 
be resolved. I will add more related scripts later. 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;"> 
<span style="font-family: &quot;times&quot; , &quot;times new roman&quot; , 
serif;"> 







<span style="font-family: &quot;arial&quot; , sans-serif;"> 