---
title: 'Depression filling on a sphere'
date: 2020-08-26
permalink: /posts/2020/05/depression-filling-on-a-sphere/
tags:
  - Hydrology
  - Depression filling
  - Terrain analysis
---

One of my interests and projects is about flow routing on a global scale or a sphere.
This work has several major challenges awaiting to be resolved. Here I will explain a few of them.

I want to provide some background, we are not using traditional square mesh to cover the sphere. Instead, we will be using DGGS grid, and most grids will be hexagons, you can take a look at my previous posts.


On a sphere, land/continents are not continuous, a landmass may be broken into several islands.

![Figure 1](https://github.com/changliao/changliao.github.io/blob/main/_figure/dual_island.jpg?raw=true)

Because of the unique structure of hexagon mesh, parallel computing becomes difficult. It is not straightforward to decompose the global mesh into regular tiles similar to square grid mesh.
DEM remap/resamaple method needs to be improved. Current DEM dataset is still in the square grid format, a rigorous remap method is needed to assign elevation to new hexagon grids.