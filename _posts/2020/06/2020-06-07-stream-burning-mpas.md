---
title: 'Streaming burning on MPAS mesh'
date: 2020-08-26
permalink: /posts/2020/06/stream-burning-on-mpas-mesh/
tags:
  - HexWatershed
  - Watershed
  - Hydrology
  - Stream burning
  - MPAS
---


To generate a stream network that is realistic with the NHD flow line, we need to recondition the DEM, or the so-called "stream burning" into the DEM.


In the classical hydrologic model, streaming burning and depression filling are separate steps. Sometimes iterative operations are also required because either step will modify the DEM.


In the MPAS mesh, these two algorithms must be rewritten. So the new question is: can we achieve depression filling and streaming burning in one single step? What is the implication behind that? Can we design a scenario that this will make a difference?


If there is a difference, does merging them into one single step will resolve this issue?


If the above assumptions are true, then we need to consider the following challenges.


* The existing depression filling algorithm starts with boundary/edge, so the stream burning must follow the same strategy;

* The stream grid flag must be burned into the MPAS mesh in advance, fortunately this requirement is met by the Jigsaw algorithm;

* We need to add an auxiliary step to obtain the “true” boundary;

* We need to add algorithm to find the stream bank and add the “AGREE” algorithm;

* How can we define the buffer zone? Can we just use one single grid (less modification to the raw DEM)?


Once these questions are answered, we can then move to the developments.

