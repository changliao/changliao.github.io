---
 
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

Over the time, I need to manipulate a lot of data on a Linux cluster. Some of these manipulations actually read/write data, whereas some are essentially file system operations, such as downloading the files.
Here I present a list of similar operations suitable for HPC using pbs job approach whenever possible.
I do not attempt to include all possible methods but only the ones that I find useful and easy to prepare in seconds.
Download
The most efficient way to download MODIS alike data using HPC.
wget -r --no-parent -R "index.html*" --retr-symlinks -A "*.nc" ftp-url
wget -r --no-parent -R "index.html*" -A "MOD17A2.A2000*.hdf" -A "MOD17A2.A2000*.xml" http-url
wget -r --no-parent -R "index.html*" -A "MOD17*.hdf" -A "MOD17*.xml" http-url
You can basically setup filter for file type, year and granule id.
A live example:
///==========================================================
#!/bin/bash                       
#PBS -l nodes=1:ppn=1                     
#PBS -l naccesspolicy=singleuser       
#PBS -l walltime=40:00:00                   
#PBS -M your email address
#PBS -m ae             
#PBS -N download                         
#PBS -q standby                           
cd $PBS_O_WORKDIR
wget -r --no-parent  -R "index.html*"   --retr-symlinks  -A "*.tar" ftp://somwhere
///==========================================================

Compress and extract 
Examples:
///==========================================================
#!/bin/bash                            
#use this script to extract tar files under the sub directory     
for dir in `find -mindepth 1 -maxdepth 1 -type d`
do
    cd $dir
    echo $dir
    tar xf *.tar ./
    cd ..
done
///==========================================================
#!/bin/bash
# Pass the name of the file to unpack on the command line $1
for file in *.gz
do
    gunzip -d "$file"
done
///==========================================================

Search
grep -rnw '/path/to/somewhere/' -e "pattern"
find . -maxdepth 1 -name "*string*" -print
Comiple
make &> results.txt

Count 
find . -name '*.cpp' | xargs wc -l

Debug
qsub -I -lnodes=1:ppn=20 -lwalltime=04:00:00 -q boss  -X


Simply organize these above bash script and replace with commands, most file system related tasks can be resolved. I will add more related scripts later.









