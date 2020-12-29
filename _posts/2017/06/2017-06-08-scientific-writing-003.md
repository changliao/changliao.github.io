---
layout: post
title: 'Scientific writing: from LaTex to BibTex'
date: '2017-06-08T18:37:00.001-07:00'
author: Chang Liao
tags:
- Mendeley
- Latex
modified_time: '2018-04-03T12:17:42.475-07:00'
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-4578913744633339929
blogger_orig_url: https://changliao.blogspot.com/2017/06/scientific-writing-003.html
---

I am not very familiar with Tex system, but I use it for several purposes.

To produce a high quality manuscript using Latex itself can be a little bit of challenge so I am trying to do it once for all here.

Here are steps I generally follow if everything works fine.

You will need an Overleaf account because I prefer to write in a browser.
Find the template of the document. If Overleaf has one, use it directly, if not, download it and upload it as a project;
Start writing your manuscript just like normal;
For figures, I suggest use an separated folder and indexed names;
Use Mendeley to manage all your references and enable Mendeley Bibtex feature;
Connect your Overleaf with Mendeley,
Add the Bibliography file from Mendeley;
Add all citations into your manuscript;
Download the whole project including all output;
Install Bibtex on a Linux machine;
Upload all the results to Linux machine;
Install the bibexport package;
Remove unwanted citations from the Mendeley local file using bibexport;
Upload the revised bib file back to Overleaf and update the project;
Congratulations.
Some tips are:
Make sure you have cited all reference before you apply bibexport, or else you will have to repeat step 13 and 14 (because journal usually do not need your entire bib file and you must only include references that are actually cited.);
Produce postscript format to prepare high quality figures if possible:
Sometimes you have to disconnect Mendeley and re-connect again.
Good luck!

