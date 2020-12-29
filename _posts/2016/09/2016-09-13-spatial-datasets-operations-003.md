---
layout: post
title: 'Spatial datasets operations: From MODIS to model ready binary workflow'
date: '2016-09-13T07:44:00.000-07:00'
author: Chang Liao
tags:
- ENVI
- IDL
- ArcMap
modified_time: '2017-01-16T17:38:06.578-08:00'
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-8761224869485976326
blogger_orig_url: https://changliao.blogspot.com/2016/09/spatial-datasets-operations-003.html
---


I have written a couple of articles regarding the potential issues during raster operations. Here I have put down some typical workflow for these operations.
For study area smaller than one MODIS granule, following these steps:

The common method that will work for you:
Convert one HDF file to GeoTIFF using ArcMap, save this file as A.tif.
Convert all HDF files to GeoTIFF using IDL and A.tif, call routine "hdf2tiff". In this step, you should set all unwanted pixel to missing value, such as -9999.
Project one GeoTIFF A.tif to B.dat using ArcMap;
Project all GeoTIFF to ENVI files using B.dat, call routine "project48";
Define the missing value for all the ENVI files from step 4, call routine "define_envi_missing_value";
Prepare the shapefile mask for the study area, C.shp using Arcmap, C should has the same projection as the target projection;
Extract all ENVI files using the C.shp shapefile , call routine "extract50".
(Updated January 15 2017). 
Since in some cases it is impossible to re-project a raster from one projection to another using common projection method, which mean the above step 4 is going to fail unless you use rigorous projection method. At the same time, rigorous method takes a long time to run. Therefore, we recommend an extraction before projection (more details). And the new steps are:
Convert one HDF file to GeoTIFF using ArcMap, save this file as A.tif.
Convert all HDF files to GeoTIFF using IDL and A.tif, call routine "hdf2tiff". In this step, you should set all unwanted pixel to missing value, such as -9999.
Prepare a rectangle shapefile B.shp which covers your study domain using ArcMap. B.shp has the same spatial reference with A.tif;
Extract all the GeoTIFF files using the rectangle shapefile B.shp.
Define the missing value for all the ENVI files from step 4;
Extract the A.tif using B.shp and save it as C.dat;
Project C.dat to D.dat with the target spatial reference using ArcMap;
Project all ENVI files from step 4 using D.dat, call routine "project48";
Prepare the shapefile mask for the study area, E.shp, E should has the same projection as the target projection;
Extract all ENVI files from step 8 using the E.shp shapefile.
Good luck.