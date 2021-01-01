---
title: 'Watershed delineation on a hexagonal mesh grid: part A'
date: 2017-03-19
permalink: /posts/2020/03/19/watershed-delineation-on-a-hexagonal-mesh-grid-part-a/
tags:
  - Watershed
  - HexWatershed
---
One of our recent publications is "Watershed Delineation On A Hexagonal Mesh Grid" published on Environmental Modeling and Software (link).
Here I want to provide some behind the scene details of this study.

(The figures are high resolution, you might need to zoom in to view.)

First, I'd like to introduce the motivation of this work.
Many of us including me have done lots of watershed/catchment hydrology modeling. For example, one of my recent publications is a three-dimensional carbon-water cycle modeling work (link), which uses lots of watershed hydrology algorithms.

In principle, watershed hydrology should be applied to large spatial domain, even global scale. But why no one is doing it? 
I will use the popular USDA SWAT model as an example. Why no one is setting up a SWAT model globally? 

There are several reasons we cannot use SWAT at global scale:

* We cannot produce a global DEM with a desired map projection. SWAT model relies on stream network, which depends on DEM. It is impossible to use a 2D map projection to represent a 3D sphere (Earth is not flat).
* Computationally, it is difficult to delineate watershed at global scale. First, the dataset set is large, and second the continentals are not connected.

However, so how do many global hydrology models (GHMs) somehow avoid these issues?

* Global hydrology models use latitude/longitude, instead of map projection. 
* GHMs use relatively coarse resolution to avoid the computational issue.

The problem with latitude/longitude is that the grid area changes with latitude:
![Figure 1](https://github.com/changliao/changliao.github.io/blob/main/_figure/spatial_distortion.png?raw=true)

Can we guarantee that the flow direction based on this distorted grid resolution is accurate enough? If not, then all the GHM simulations have greater uncertainty in high latitudes.

What if we can use a different type of grid to cover the globe? This falls into the category of Discrete Global Grid Systems (DGGS). There are a number of DGGS listed here: https://en.wikipedia.org/wiki/Discrete_global_grid

One of these DGGS is very promising for us if we want to guarantee reasonable flow direction. That is the ISEA grid:

![Figure 2](https://github.com/changliao/changliao.github.io/blob/main/_figure/dggrid.jpg?raw=true)

Traditionally, flow direction is represented by this method:

![Figure 3](https://github.com/changliao/changliao.github.io/blob/main/_figure/d4d8.png?raw=true)

Interestingly, in an ISEA grid, the flow direction can be represented differently:

![Figure 4](https://github.com/changliao/changliao.github.io/blob/main/_figure/d6.png?raw=true)

It actually solves one of the oldest problems in watershed hydrology: the travel length in the diagonal direction is longer than direct direction.

A bonus benefit is that it will also eliminate the island effect:

![Figure 5](https://github.com/changliao/changliao.github.io/blob/main/_figure/island.png?raw=true)

You probably have seen this before when you look at the subbasin boundary results from the watershed delineation.

So we decided to use the ISEA alike grid, a hexagon mesh grid to address these issues.

The second part is Here.

Reference:
Liao, C., Tesfa, T., Duan, Z., & Leung, L. R. (2020). Watershed delineation on a hexagonal mesh grid. Environmental Modelling & Software, 128, 104702. https://doi.org/https://doi.org/10.1016/j.envsoft.2020.104702
