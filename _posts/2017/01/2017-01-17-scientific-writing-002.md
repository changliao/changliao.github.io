---
 
title: 'Scientific writing: high quality scalable vector graphics'
date: '2017-01-17T19:20:00.000-08:00'
permalink: /posts/2017/01/17/publication-vector-graphics/
author: Chang Liao
tags:
- SVG
- Google
- Postscript
modified_time: '2018-04-03T12:27:39.848-07:00'
---

I recently found a new way to prepare publication-ready high quality vector graphic using Google Drive.
Here is the result:

 

Here are steps you can follow:

Prepare a Google sheets within Google Drive;
Insert chart from the menu;
Define whatever color or label you like;
Use development tool within Google Chrome to find the SVG tag in the html script;
Open your text editor and paste the SVG html tag into it;
Make up the SVG header, remember to define the SVG version.
Save the text file as a SVG file.
You may want to convert the SVG file to a Postscript (PS) file so you can convert it to any 600dpi raster figure.
The essential idea behind this is that Google Chart API uses SVG and we are basically calling Google Chart API to produce chart without actually writing any script!
The above figure is Copy right protected 