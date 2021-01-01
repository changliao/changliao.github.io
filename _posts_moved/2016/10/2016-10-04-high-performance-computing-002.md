---
 
title: 'High Performance Computing: OpenMP and Anusplin'
date: '2016-10-04T11:53:00.000-07:00'
author: Chang Liao
tags:
- Anusplin
- HPC
- OpenMP
- GCC
modified_time: '2017-02-16T14:53:53.633-08:00'
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-8204758025720372101
blogger_orig_url: https://changliao.blogspot.com/2016/10/high-performance-computing-002.html
---

This is a live example from the project I am working right now. Good luck if you are following!
In order to speed my Anusplin program, I decided to use OpenMP. Anusplin is a package for climate data preparation. 

My program was written in C++ as usual. C++ itself is fast, but Anusplin program takes a long time to run for approximately 50K+ simulations. Previously I set up some system pause (0.1second) between each run. Let's see what OpenMP can do.

There are many guide of OpenMP online.
First you need to know what's the GCC version you get, such as
///===========================================
gcc -v
Using built-in specs.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/apps/rhel6/gcc/5.2.0/libexec/gcc/x86_64-unknown-linux-gnu/5.2.0/lto-wrapper
Target: x86_64-unknown-linux-gnu
Configured with: /tmp/aai/gcc-5.2.0/configure --prefix=/apps/rhel6/gcc/5.2.0 --enable-languages=c,c++,fortran --enable-shared --enable-threads=posix --disable-checking --disable-multilib --with-system-zlib --enable-__cxa_atexit --disable-libunwind-exceptions --enable-java-awt=gtk --with-gmp=/apps/rhel6/gcc/5.2.0/gmp-6.1.0 --with-mpfr=/apps/rhel6/gcc/5.2.0/mpfr-3.1.3 --with-mpc=/apps/rhel6/gcc/5.2.0/mpc-1.0.3
Thread model: posix
gcc version 5.2.0 (GCC) 
///===========================================
Usually the higher, the better, but you may need to double check.
Then here is the OpenMP version support in different versions of GCC.
https://gcc.gnu.org/wiki/openmp

Next, I will follow this guide if possible:
First, I need to enable OpenMP compiler flag in my makefile as: (remember to backup the makefile if you want)
g++ tmp.cpp -fopenmp
Then I added the simplest control to my for loop:
#pragma omp parallel for

Save the source code and re-compile.
My first error:
invalid exit from OpenMP structured block.
My second error:
undefined reference to `GOMP_parallel_start
(You need to link with -fopenmp. Your makefile doesn't provide that flag on the linker step. Just add -fopenmp to your LDFLAGS)
After fixing these two errors within one minute, the re-compile was successful.

However, there is an error thrown out as:
*** glibc detected *** ./anusplin_openmp: double free or corruption (fasttop): 0x00002b8144000af0 ***

So after some research, I have set a few variables as private in the OpenMP and everything works now.

By the way, if you have troubles with memory issues brought out by OpenMP, you can try Valgrind.



