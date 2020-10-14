---
layout: post
title: Depression filling on a sphere
date: '2020-04-30T15:06:00.000-07:00'
author: Chang Liao
tags:
- DEM
- Hydrology
- HexWatershed
- Global Hydrology
- Watershed Hydrology
- Hexagon
modified_time: '2020-04-30T15:06:58.764-07:00'
thumbnail: https://1.bp.blogspot.com/-UYAbZgBx1VY/XqtKSNE7stI/AAAAAAAA9WE/FWTgkby924I5GwlmQzEAA-DGdVcMfOi5gCLcBGAsYHQ/s72-c/island.jpg
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-1041224258987358516
blogger_orig_url: https://www.changliao.us/2020/04/depression-filling-on-sphere.html
---

One of my interests and projects is about flow routing on a global scale or a 
sphere. 
This work has several major challenges awaiting to be resolved. Here I will 
explain a few of them. 

I want to provide some background, we are not using traditional square mesh to 
cover the sphere. Instead, we will be using DGGS grid, and most grids will be 
hexagons, you can take a look at my previous posts. 


1. On a sphere, land/continents are not continuous, a landmass may be broken 
into several islands.<div class="separator" style="clear: both; text-align: 
center;">[<img border="0" data-original-height="863" 
data-original-width="1600" height="215" 
src="https://1.bp.blogspot.com/-UYAbZgBx1VY/XqtKSNE7stI/AAAAAAAA9WE/FWTgkby924I5GwlmQzEAA-DGdVcMfOi5gCLcBGAsYHQ/s400/island.jpg" 
width="400" 
/>](https://1.bp.blogspot.com/-UYAbZgBx1VY/XqtKSNE7stI/AAAAAAAA9WE/FWTgkby924I5GwlmQzEAA-DGdVcMfOi5gCLcBGAsYHQ/s1600/island.jpg)<div 
class="separator" style="clear: both; text-align: center;"> 
1. <div class="separator" style="clear: both; text-align: left;">Because of 
the unique structure of hexagon mesh, parallel computing becomes difficult. It 
is not straightforward to decompose the global mesh into regular tiles similar 
to square grid mesh. 
1. <div class="separator" style="clear: both; text-align: left;">DEM 
remap/resamaple method needs to be improved. Current DEM dataset is still in 
the square grid format, a rigorous remap method is needed to assign elevation 
to new hexagon grids. 