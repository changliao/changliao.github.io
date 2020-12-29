---
title: 'Watershed delineation on a hexagonal mesh grid: part A'
date: 2017-09-01
permalink: /posts/2020/03/watershed-delineation-on-a-hexagonal-mesh-grid-part-a/
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

But because the grid is different, we made several improvements.
First,  we need a new index system, and we need to rebuild the neighbor information.



We also need to do the depression filling, here we used the priority flooding method. This method is pretty impressive in this application. Without getting into details, this is how it works:



After this, we are able to calculate the flow direction, for example:


As well as flow accumulation:

Last, I'd like to illustrate how this method fixs some headache for many of us:



If you are interested in using or applying this method in your study area or hydrologic model, stay tuned.

Reference:
Liao, C., Tesfa, T., Duan, Z., & Leung, L. R. (2020). Watershed delineation on a hexagonal mesh grid. Environmental Modelling & Software, 128, 104702. https://doi.org/https://doi.org/10.1016/j.envsoft.2020.104702
