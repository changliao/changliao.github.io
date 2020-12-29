---
title: 'Watershed delineation on a hexagonal mesh grid: part B'
date: 2017-03-19
permalink: /posts/2020/03/watershed-delineation-on-a-hexagonal-mesh-grid-part-b/
tags:
  - Watershed
  - HexWatershed
---
This is the second part of a study, the first part can be accessed from Here.
So we decided to use the ISEA alike grid, a hexagon mesh grid to address these issues.

(The figures are high resolution, you might need to zoom in to view.)

What follows is something I should have learned if my major was hydrology. Even though we have been using ArcSWAT, ArcHydro many times, we seldom really looked into the algorithms because they are mostly straight forward.

But when we decided to try this on a different mesh grid, a lot of details start to emerge, and through which we also learned a lot.

The overall workflow is pretty simple:

![Figure 1](https://github.com/changliao/changliao.github.io/blob/main/_figure/hexwatershed_workflow.png?raw=true)

But because the grid is different, we made several improvements.
First,  we need a new index system, and we need to rebuild the neighbor information.

![Figure 2](https://github.com/changliao/changliao.github.io/blob/main/_figure/hexagon_topology.png?raw=true)


We also need to do the depression filling, here we used the priority flooding method. This method is pretty impressive in this application. Without getting into details, this is how it works:
![Figure 3](https://github.com/changliao/changliao.github.io/blob/main/_figure/hexagon_flood_legend.gif?raw=true)


After this, we are able to calculate the flow direction, for example:

![Figure 4](https://github.com/changliao/changliao.github.io/blob/main/_figure/cbf_flow_direction_90_zoom.png?raw=true)

As well as flow accumulation:

![Figure 5](https://github.com/changliao/changliao.github.io/blob/main/_figure/tinpan_flow_accumulation_30_zoom.png?raw=true)

Last, I'd like to illustrate how this method fixes some headache for many of us:

![Figure 6](https://github.com/changliao/changliao.github.io/blob/main/_figure/tinpan30_square.png?raw=true)

![Figure 7](https://github.com/changliao/changliao.github.io/blob/main/_figure/tinpan30_hexagon.png?raw=true)


If you are interested in using or applying this method in your study area or hydrologic model, stay tuned.

Reference:
Liao, C., Tesfa, T., Duan, Z., & Leung, L. R. (2020). Watershed delineation on a hexagonal mesh grid. Environmental Modelling & Software, 128, 104702. https://doi.org/https://doi.org/10.1016/j.envsoft.2020.104702
