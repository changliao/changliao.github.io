---
layout: post
title: 'Scientific writing: high quality scalable vector graphics'
date: '2017-01-17T19:20:00.000-08:00'
author: Chang Liao
tags:
- SVG
- Google
- Postscript
modified_time: '2018-04-03T12:27:39.848-07:00'
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-1276774263960812940
blogger_orig_url: https://changliao.blogspot.com/2017/01/scientific-writing-002.html
---

I recently found a new way to prepare publication-ready high quality vector 
graphic using Google Drive. 
Here is the result: 

<iframe frameborder="0" height="410" scrolling="no" seamless="" 
src="https://docs.google.com/spreadsheets/d/16NjXTNqRbB2yb0M1Z69c2TlSDEzFEr4e9OILvXNIlnk/pubchart?oid=1955051236&amp;format=interactive" 
width="662"></iframe> 

Here are steps you can follow: 

1. Prepare a Google sheets within Google Drive; 
1. Insert chart from the menu; 
1. Define whatever color or label you like; 
1. Use development tool within Google Chrome to find the SVG tag in the html 
script; 
1. Open your text editor and paste the SVG html tag into it; 
1. Make up the SVG header, remember to define the SVG version. 
1. Save the text file as a SVG file. 
1. You may want to convert the SVG file to a 
[Postscript](https://en.wikipedia.org/wiki/PostScript) (PS) file so you can 
convert it to any 600dpi raster figure. 
<div>The essential idea behind this is that [Google Chart 
API](https://developers.google.com/chart/) uses 
[SVG](https://en.wikipedia.org/wiki/Scalable_Vector_Graphics) and we are 
basically calling Google Chart API to produce chart without actually writing 
any script!<div>The above figure is Copy right protected 