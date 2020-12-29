---
layout: post
title: From watershed to global
date: '2018-07-31T10:59:00.001-07:00'
author: Chang Liao
tags:
- ECOGlobe
- GPU
- OpenMP
- NetCDF
- Hadoop
- MPI
- HDF
- GDAL
modified_time: '2018-07-31T11:01:42.713-07:00'
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-8350976234777351765
blogger_orig_url: https://changliao.blogspot.com/2018/07/ecosystem-modeling-010.html
---

Ever since I finished my 3D ecosystem simulation using the ECO3D model, I started to think about applying this model to a larger spatial domain such as global.

While there are several technical difficulties in doing so, there are also different combinations of solutions to resolve these issues. In this post I will list out major issues we will address:

First, on a global scale, we need much more massive input data preparation. What's more, some traditional algorithm/method may not even work. For example, the watershed lineation process on global scale will not be used anymore. Instead, another river routing algorithm or dataset should be used.
File I/O will becomes an issue. Global scale simulation will use parallel computing, which mean the file I/O must support parallel reading/writing. Whether file system will be ideal or other options remains unclear. For example, can we use database or Hadoop?
Parallel computing with/without MPI/OpenMP. I am not sure of other options but running billion of instances on HPC requires parallel computing for sure. Maybe Hadoop or GPU could help.
Global grid system must be updated. Can we have a uniform grid scheme for simulation? With spatial relationship established, interactions among grids can be easier considered.
File storage. If data are not stored in database alike data server. A better storage approach will be used.

Because the ECO3D is finally released, my next research focus will be applying it to a large spatial domain. The following steps should be taken in sequence:
Add MPI capability to the ECO3D model. Currently it only uses OpenMP for a watershed scale. On a global scale, MPI is an inevitable path;
Develop the DGGS for the spatial discretization scheme;
Design a better storage system for file I/O.
Develop a GDAL-based raster/vector dataset tool, this tool will be used to speed up all geospatial dataset operations.
I am also looking forward to working with collaborators.