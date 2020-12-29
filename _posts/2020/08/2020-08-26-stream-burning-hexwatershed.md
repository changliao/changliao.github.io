---
title: 'Stream burning on hexagonal mesh'
date: 2020-08-26
permalink: /posts/2020/08/stream-burning-on-hexagonal-mesh/
tags:
  - HexWatershed
  - Watershed
  - Hydrology
  - Stream burning
---
This is a follow up study of HexWatershed. In the latest development, we decided to add the so called "stream burning" capability into the HexWatershed model.

A details explanation of the motivation will be discussed in our new paper. Here I will only focus on some critical issues in the development.

The first issue is: what happens if the outlet is not at the edge?
![Figure 1](https://github.com/changliao/changliao.github.io/blob/main/_figure/outlet_burning.png?raw=true)


One of the core processes to conduct priority-flood filling or breaching is that if a grid cell is processed, it will not be processed again because a mask is used to keep track all the history.
When the outlet is not at the edge, the priority-flood method may start from a non-stream grid. As the algorithm advances, grids near the actual outlet can be possibly marked before outlet is processed. Since these grids are marked, they won't be changed even though they are next to stream. The direct result is that the outlet grid becomes a depression. However, by the definition of watershed, the outlet should be lowest elevation and it would be the first to be added into the queue. By the time the outlet is added, it would automatically turns one of the neighbors into a stream grid.

This is exactly what is modeled in the HexWatershed. Even without an outlet, the model will be able to create a new one, which however, may be the same with the NHD dataset. Therefore, it is more desirable to set it in the configuration through the mesh ID parameter.



 