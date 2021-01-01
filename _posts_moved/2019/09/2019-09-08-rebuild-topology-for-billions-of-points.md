---
 
title: Rebuild the topology for billions of points on a sphere
date: 2019-09-08
permalink: /posts/2019/09/08/rebuild-topology-of-billion-point-on-sphere/
author: Chang Liao
tags:
modified_time: '2019-09-08T12:16:34.842-07:00'
---

One of my projects requires an index system for a DGGS alike system with topology information.
Unlike a 2D plane coordinate system which can be easily managed by a 2D matrix, plane coordinate system does work well on a sphere. One biggest issue is that we cannot locate the neighbors of each point.

Of course there are a few existing methods available to handle this type of challenge. For example, if the points were generated using some defined method, the topology relation should be contained from within.

But in the post I want to present a solution from a general perspective: for any given number of points on a sphere, how can we rebuild the topology purely from their coordinates?

I also asked some similar question here:
https://gis.stackexchange.com/questions/334214/finding-neighbors-of-latitude-longitude-pair-location

As I explained, this question is common in GIS: finding the nearest neighbor of a point. But there are also differences:

The data points are in GCS coordinate system, which means locations are stored using latitude and longitude. A simple function can be used to calculated distance;
The amount of data is massive, possibly billions.
Existing tools may be designed to work in this case. So we need to develop a new method with computational efficiency in mind.

To find the nearest neighbor, we can calculate the distance one by one, and choose the ones close to certain threshold. It is straightforward but computational expensive.


https://en.wikipedia.org/wiki/Spherical_coordinate_system