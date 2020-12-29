---
layout: post
title: Develop Python scripts cross platform
date: '2019-10-14'
permalink: /posts/2019/10/develop-python-script-cross-platform/
author: Chang Liao
tags:
- Python
- HPC
modified_time: '2019-10-14T11:57:20.509-07:00'

---



This post was an answer to my own question: https://twitter.com/changliao1025/status/1182847707666247680

When you write code for many moons, usually you will develop some sort of shared library/package for various projects.
These Python scripts may not be suitable for deployment as a package but you still want to use them anywhere.

Another issue is that I often need to write and run code cross platform/cluster. So I want to make sure there is an easy way to configure my code so that I don't have to modify things when I update something.

In my early attempt, I put everything into a package and use the following method to use them in any source code:

![Figure 1](https://github.com/changliao/changliao.github.io/blob/main/_figure/python01.jpg?raw=true)
![Figure 2](https://github.com/changliao/changliao.github.io/blob/main/_figure/python02.jpg?raw=true)
![Figure 3](https://github.com/changliao/changliao.github.io/blob/main/_figure/python03.jpg?raw=true)

With these global variables, now I can import any function within the package:


This seems to work well at the beginning, however, I have to copy/paste this about 20 lines of code in lots of functions. And if I want to add new capability, I have to modify all of them!

So I am on a new quest to fix it.

After digging a little bit, I was able to find a better solution. So instead of defining these system wide or global variables in production code, I can place them into a standalone module.
After that, I only need to import them using 3 or 4 lines:


The magic here is that I added one single line in my bash profile.
With the combination of environment variable "PATH" and Python sys.path, I was able to import all the global variables using one single module.

With that, I can significantly reduce and clean up the code I wrote for several projects. Also, if I need to change something, I only need to change the library, nothing else.
Problem solved.

Cheers!