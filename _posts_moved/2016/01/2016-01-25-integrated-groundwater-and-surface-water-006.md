---
 
title: 'Integrated groundwater and surface water modeling: the appropriate way to
  prepare the best DEM'
date: '2016-01-25T12:46:00.000-08:00'
permalink: /posts/2016/01/25/dem-for-hydrology/
author: Chang Liao
tags:
- DEM
- Arc Hydro
- ArcMap
- SAGA
modified_time: '2018-04-03T12:14:58.000-07:00'
---

One the most important inputs for groundwater and surface water hydrology modeling is the Digital Elevation Model (DEM).

Though DEM can be obtained through many approaches, the final DEM varies significantly. Therefore, DEM can seldom  be directly used in most modeling work. Instead, we often need to adjust the DEM so that it can meet the requirements of the hydrology modeling.

The adjustment, however, often involves series of operations. These operations can be carried out using different approaches in different orders. The result could be quite different. The important part is that most of them are unusable. So the question is, what is most promising way to prepare the DEM?

Here I have provided an example work flow, which may be suitable for most tasks. Then I will explain in details the purpose of this step and what tools we can make use of. In the end I will discuss why it should be done in this order.
Download the DEM datasets of the same format for the study area;
Mosaic these DEM datasets into one raster file;
Resample the DEM if necessary;
Project the DEM into required projection;
Clip the DEM using  a rectangle, whose spatial extent must cover the whole study area; 
Download the stream datasets of the study area;
Process the stream datasets similar to DEM;
Burn the flow line into the DEM;
Fill the depression within the DEM;
Correct the DEM in flow line.

Explanations:

DEM datasets can be downloaded from USGS NED in various formats and resolutions. Make sure the DEM datasets covers the spatial extent of the study area;
Depending on the spatial extent of the study area, it usually contains more than one DEM data file. Therefore, it is necessary to mosaic them into one file. This is because most GIS operations such as re-sample are sensitive to edge effects. 
The resample operation could bring the DEM into desired spatial resolution. It is common to re-sample from high resolution to low resolution;
The DEM file is probably not in the desired projection under the study area. 
Computational demand is something we try to avoid if possible. Therefore it is best to extract the DEM out from the larger file. However, we must keep the valuable information. So we can clip the DEM using a large rectangle. 
Stream data are necessary to assist the DEM reconditioning;
The stream data also needs to prepared into the same spatial extent and projection;
Adjust the DEM so surface water can always flow into the streams. However, we don't want to change the DEM so much because the groundwater system also interacts with the stream.
Surface depression causes a lot of troubles for surface runoff. For most surface hydrology, they can be removed through the fill operation.
There might be still flaws within the DEM along the flow line, so we need to correct them separately.

Most of the GIS operations can be carried out within ArcGIS. However, other tools such as ArcHydro, SAGA are also very powerful. 

Next, for most cases, these operations must be carried out in the above order. Step 3 and 4 can change order without too many differences. For DEM reconditioning, it is usually good practice to follow steps 8, 9 and 10 exactly. You will find that depressions still exist if you fill them in the first place since burn can change DEM. There is currently no tools can consider stream and depression at the same time. Double check the DEM afterwards is encouraged.









