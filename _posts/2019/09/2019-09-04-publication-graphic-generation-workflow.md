---
 
title: Publication graphic generation workflow
date: 2019-09-04
permalink: /posts/2019/09/publication-graphic-generation-workflow/
author: Chang Liao
tags:
- Graphics
- Publication
modified_time: '2019-09-04T15:46:36.774-07:00'
---

Preparing graphics for journal publication is an important step before we submit the manuscript. And sometimes this process is not as smooth as we expected. There are several problems we often encounter:

* We generally generate more than enough figures and in the end, we only need a few;
* We also use different format for different purposes. For example, we use jpg/png for debugging. And we use svg/postscript for high quality production. A conversion is usually required.
* Journals usually prefer 600dpi high resolution figures. So postscript format might be the best option.
* Indexing is important for final upload.
* Subplot makes it even complicated.
* We use more than one tools as well. I use IDL/Python for plotting, but I also use GIMP/Snagit/Inkscape for some processes. Keep the process consistent is not easy.

So maybe we need a clear road map so we won’t get lost easily. Here are my plans:

* Produce postscript/svg when possible using DrawIO/Python/IDL;
* If we need subplot, produce them simultaneously;
Avoid using GIMP/Inkscape unless in the final step;
* Better file system management.

I might provide an example later.