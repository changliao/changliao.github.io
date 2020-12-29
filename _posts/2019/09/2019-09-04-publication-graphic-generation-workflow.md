---
layout: post
title: Publication graphic generation workflow
date: '2019-09-04T15:46:00.002-07:00'
author: Chang Liao
tags:
- Graphics
- Publication
modified_time: '2019-09-04T15:46:36.774-07:00'
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-4027485007039689489
blogger_orig_url: https://changliao.blogspot.com/2019/09/publication-graphic-generation-workflow.html
---

<div style="background-color: white; box-sizing: inherit; color: #404040; 
font-family: &quot;Libre Baskerville&quot;, Libre, Georgia, Times, serif; 
font-size: 16px; margin-bottom: 1.75em;">Preparing graphics for journal 
publication is an important step before we submit the manuscript. And 
sometimes this process is not as smooth as we expected. There are several 
problems we often encounter:<ul style="background-color: white; box-sizing: 
inherit; color: #404040; font-family: &quot;Libre Baskerville&quot;, Libre, 
Georgia, Times, serif; font-size: 16px; list-style-image: initial; 
list-style-position: initial; margin: 0px 0px 1.75em; padding-left: 
1.75em;"><li style="box-sizing: inherit;">We generally generate more than 
enough figures and in the end, we only need a few;</li><li style="box-sizing: 
inherit;">We also use different format for different purposes. For example, we 
use jpg/png for debugging. And we use svg/postscript for high quality 
production. A conversion is usually required.</li><li style="box-sizing: 
inherit;">Journals usually prefer 600dpi high resolution figures. So 
postscript format might be the best option.</li><li style="box-sizing: 
inherit;">Indexing is important for final upload.</li><li style="box-sizing: 
inherit;">Subplot makes it even complicated.</li><li style="box-sizing: 
inherit;">We use more than one tools as well. I use IDL/Python for plotting, 
but I also use GIMP/Snagit/Inkscape for some processes. Keep the process 
consistent is not easy.</li><div style="background-color: white; box-sizing: 
inherit; color: #404040; font-family: &quot;Libre Baskerville&quot;, Libre, 
Georgia, Times, serif; font-size: 16px; margin-bottom: 1.75em;">So maybe we 
need a clear road map so we won’t get lost easily. Here are my plans:<ul 
style="background-color: white; box-sizing: inherit; color: #404040; 
font-family: &quot;Libre Baskerville&quot;, Libre, Georgia, Times, serif; 
font-size: 16px; list-style-image: initial; list-style-position: initial; 
margin: 0px 0px 1.75em; padding-left: 1.75em;"><li style="box-sizing: 
inherit;">Produce postscript/svg when possible using 
DrawIO/Python/IDL;</li><li style="box-sizing: inherit;">If we need subplot, 
produce them simultaneously;</li><li style="box-sizing: inherit;">Avoid using 
GIMP/Inkscape unless in the final step;</li><li style="box-sizing: 
inherit;">Better file system management.</li><div style="background-color: 
white; box-sizing: inherit; color: #404040; font-family: &quot;Libre 
Baskerville&quot;, Libre, Georgia, Times, serif; font-size: 16px; 
margin-bottom: 1.75em;">I might provide an example later. 