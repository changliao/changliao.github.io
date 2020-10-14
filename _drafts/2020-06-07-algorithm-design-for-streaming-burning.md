---
layout: post
title: Algorithm design for the streaming burning based on MPAS mesh
date: '2020-06-07T12:33:00.001-07:00'
author: Chang Liao
tags:
- NHD
- Hydrology
- HexWatershed
- MPAS
- Watershed Hydrology
- Hexagon
modified_time: '2020-06-07T12:33:12.408-07:00'
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-8214540034910436658
blogger_orig_url: https://www.changliao.us/2020/06/algorithm-design-for-streaming-burning.html
---

<span id="docs-internal-guid-aea3587d-7fff-d672-f9ee-717f2a054f31"><p 
dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 
0pt;"><span style="font-family: Arial; font-size: 11pt; white-space: 
pre-wrap;">To generate a stream network that is realistic with the NHD flow 
line, we need to recondition the DEM, or the so-called "stream burning" into 
the DEM.</p> 
<p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 
0pt;"><span style="font-family: Arial; font-size: 11pt; 
font-variant-east-asian: normal; font-variant-numeric: normal; vertical-align: 
baseline; white-space: pre-wrap;">In the classical hydrologic model, streaming 
burning and depression filling are separate steps. Sometimes iterative 
operations are also required because either step will modify the DEM.</p> 
<p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 
0pt;"><span style="font-family: Arial; font-size: 11pt; 
font-variant-east-asian: normal; font-variant-numeric: normal; vertical-align: 
baseline; white-space: pre-wrap;">In the MPAS mesh, these two algorithms must 
be rewritten. So the new question is: can we achieve depression filling and 
streaming burning in one single step? What is the implication behind that? Can 
we design a scenario that this will make a difference?</p> 
<p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 
0pt;"><span style="font-family: Arial; font-size: 11pt; 
font-variant-east-asian: normal; font-variant-numeric: normal; vertical-align: 
baseline; white-space: pre-wrap;">If there is a difference, does merging them 
into one single step will resolve this issue?</p> 
<p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 
0pt;"><span style="font-family: Arial; font-size: 11pt; 
font-variant-east-asian: normal; font-variant-numeric: normal; vertical-align: 
baseline; white-space: pre-wrap;">If the above assumptions are true, then we 
need to consider the following challenges.</p> 
<ol style="margin-bottom: 0; margin-top: 0;"><li dir="ltr" style="font-family: 
Arial; font-size: 11pt; font-variant-east-asian: normal; font-variant-numeric: 
normal; list-style-type: decimal; vertical-align: baseline; white-space: 
pre;"><p dir="ltr" role="presentation" style="line-height: 1.38; 
margin-bottom: 0pt; margin-top: 0pt;"><span style="font-size: 11pt; 
font-variant-east-asian: normal; font-variant-numeric: normal; vertical-align: 
baseline; white-space: pre-wrap;">The existing depression filling algorithm 
starts with boundary/edge, so the stream burning must follow the same 
strategy;</p></li><li dir="ltr" style="font-family: Arial; font-size: 11pt; 
font-variant-east-asian: normal; font-variant-numeric: normal; 
list-style-type: decimal; vertical-align: baseline; white-space: pre;"><p 
dir="ltr" role="presentation" style="line-height: 1.38; margin-bottom: 0pt; 
margin-top: 0pt;"><span style="font-size: 11pt; font-variant-east-asian: 
normal; font-variant-numeric: normal; vertical-align: baseline; white-space: 
pre-wrap;">The stream grid flag must be burned into the MPAS mesh in advance, 
fortunately this requirement is met by the Jigsaw algorithm;</p></li><li 
dir="ltr" style="font-family: Arial; font-size: 11pt; font-variant-east-asian: 
normal; font-variant-numeric: normal; list-style-type: decimal; 
vertical-align: baseline; white-space: pre;"><p dir="ltr" role="presentation" 
style="line-height: 1.38; margin-bottom: 0pt; margin-top: 0pt;"><span 
style="font-size: 11pt; font-variant-east-asian: normal; font-variant-numeric: 
normal; vertical-align: baseline; white-space: pre-wrap;">We need to add an 
auxiliary step to obtain the “true” boundary;</p></li><li dir="ltr" 
style="font-family: Arial; font-size: 11pt; font-variant-east-asian: normal; 
font-variant-numeric: normal; list-style-type: decimal; vertical-align: 
baseline; white-space: pre;"><p dir="ltr" role="presentation" 
style="line-height: 1.38; margin-bottom: 0pt; margin-top: 0pt;"><span 
style="font-size: 11pt; font-variant-east-asian: normal; font-variant-numeric: 
normal; vertical-align: baseline; white-space: pre-wrap;">We need to add 
algorithm to find the stream bank and add the “AGREE” algorithm;</p></li><li 
dir="ltr" style="font-family: Arial; font-size: 11pt; font-variant-east-asian: 
normal; font-variant-numeric: normal; list-style-type: decimal; 
vertical-align: baseline; white-space: pre;"><p dir="ltr" role="presentation" 
style="line-height: 1.38; margin-bottom: 0pt; margin-top: 0pt;"><span 
style="font-size: 11pt; font-variant-east-asian: normal; font-variant-numeric: 
normal; vertical-align: baseline; white-space: pre-wrap;">How can we define 
the buffer zone? Can we just use one single grid (less modification to the raw 
DEM)?</p></li> 
<p dir="ltr" style="line-height: 1.38; margin-bottom: 0pt; margin-top: 
0pt;"><span style="font-family: Arial; font-size: 11pt; 
font-variant-east-asian: normal; font-variant-numeric: normal; vertical-align: 
baseline; white-space: pre-wrap;">Once these questions are answered, we can 
then move to the developments.</p> 