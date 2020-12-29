---
layout: post
title: Develop Python scripts cross platform
date: '2019-10-14T11:41:00.001-07:00'
author: Chang Liao
tags:
- Python
- HPC
modified_time: '2019-10-14T11:57:20.509-07:00'
thumbnail: https://1.bp.blogspot.com/-Nz5KrmvEsJw/XaTDjXg0DeI/AAAAAAAA4kg/UHwhK2xB4H0ln_ShSybujc6BATJPGrcZwCLcBGAsYHQ/s72-c/01.jpg
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-839930796884516868
blogger_orig_url: https://changliao.blogspot.com/2019/10/develop-python-scripts-cross-platform.html
---


This post was an answer to my own question: 
[https://twitter.com/changliao1025/status/1182847707666247680](https://twitter.com/changliao1025/status/1182847707666247680) 

When you write code for many moons, usually you will develop some sort of 
shared library/package for various projects. 
These Python scripts may not be suitable for deployment as a package but you 
still want to use them anywhere. 

Another issue is that I often need to write and run code cross 
platform/cluster. So I want to make sure there is an easy way to configure my 
code so that I don't have to modify things when I update something. 

In my early attempt, I put everything into a package and use the following 
method to use them in any source code: 
<div class="separator" style="clear: both; text-align: center;">[<img 
border="0" data-original-height="757" data-original-width="738" height="640" 
src="https://1.bp.blogspot.com/-Nz5KrmvEsJw/XaTDjXg0DeI/AAAAAAAA4kg/UHwhK2xB4H0ln_ShSybujc6BATJPGrcZwCLcBGAsYHQ/s640/01.jpg" 
width="620" 
/>](https://1.bp.blogspot.com/-Nz5KrmvEsJw/XaTDjXg0DeI/AAAAAAAA4kg/UHwhK2xB4H0ln_ShSybujc6BATJPGrcZwCLcBGAsYHQ/s1600/01.jpg) 
With these global variables, now I can import any function within the package: 
<div class="separator" style="clear: both; text-align: center;">[<img 
border="0" data-original-height="76" data-original-width="615" 
src="https://1.bp.blogspot.com/-Ok_LsJTZ0WA/XaTD3oBA3LI/AAAAAAAA4ko/om6RbiMmqK0_EVrf61LdYbWfv1pLBdBswCLcBGAsYHQ/s1600/02.jpg" 
/>](https://1.bp.blogspot.com/-Ok_LsJTZ0WA/XaTD3oBA3LI/AAAAAAAA4ko/om6RbiMmqK0_EVrf61LdYbWfv1pLBdBswCLcBGAsYHQ/s1600/02.jpg) 
This seems to work well at the beginning, however, I have to copy/paste this 
about 20 lines of code in lots of functions. And if I want to add new 
capability, I have to modify all of them! 

So I am on a new quest to fix it. 

After digging a little bit, I was able to find a better solution. So instead 
of defining these system wide or global variables in production code, I can 
place them into a standalone module. 
After that, I only need to import them using 3 or 4 lines: 
<div class="separator" style="clear: both; text-align: center;">[<img 
border="0" data-original-height="74" data-original-width="441" 
src="https://1.bp.blogspot.com/-5CXfTXVK1Yw/XaTEM_2_rUI/AAAAAAAA4kw/OU7M6JuFn3EDYDo9nYoFv_0BDzDF9Fv5ACLcBGAsYHQ/s1600/03.jpg" 
/>](https://1.bp.blogspot.com/-5CXfTXVK1Yw/XaTEM_2_rUI/AAAAAAAA4kw/OU7M6JuFn3EDYDo9nYoFv_0BDzDF9Fv5ACLcBGAsYHQ/s1600/03.jpg) 
The magic here is that I added one single line in my bash profile. 
With the combination of environment variable "PATH" and Python sys.path, I was 
able to import all the global variables using one single module. 

With that, I can significantly reduce and clean up the code I wrote for 
several projects. Also, if I need to change something, I only need to change 
the library, nothing else. 
Problem solved. 

Cheers! 