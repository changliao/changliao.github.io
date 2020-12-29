---
layout: post
title: 'Integrated groundwater and surface water modeling: the appropriate way to
  prepare the best DEM'
date: '2016-01-25T12:46:00.000-08:00'
author: Chang Liao
tags:
- DEM
- Arc Hydro
- ArcMap
- SAGA
modified_time: '2018-04-03T12:14:58.000-07:00'
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-1452078905121214691
blogger_orig_url: https://changliao.blogspot.com/2016/01/integrated-groundwater-and-surface-water-006.html
---

One the most important inputs for groundwater and surface water hydrology 
modeling is the [Digital Elevation 
Model](https://en.wikipedia.org/wiki/Digital_elevation_model) (DEM). 

Though DEM can be obtained through many approaches, the final DEM varies 
significantly. Therefore, DEM can seldom  be directly used in most modeling 
work. Instead, we often need to adjust the DEM so that it can meet the 
requirements of the hydrology modeling. 

The adjustment, however, often involves series of operations. These operations 
can be carried out using different approaches in different orders. The result 
could be quite different. The important part is that most of them are 
unusable. So the question is, what is most promising way to prepare the DEM? 

Here I have provided an example work flow, which may be suitable for most 
tasks. Then I will explain in details the purpose of this step and what tools 
we can make use of. In the end I will discuss why it should be done in this 
order. 
1. Download the DEM datasets of the same format for the study area; 
1. [Mosaic 
](http://help.arcgis.com/en/arcgisdesktop/10.0/help/index.html#//001700000097000000)these 
DEM datasets into one raster file; 
1. [Resample 
](http://help.arcgis.com/en/arcgisdesktop/10.0/help/index.html#//00170000009t000000)the 
DEM if necessary; 
1. [Project 
](http://help.arcgis.com/en/arcgisdesktop/10.0/help/index.html#//00170000007m000000)the 
DEM into required projection; 
1. [Clip 
](http://help.arcgis.com/en/arcgisdesktop/10.0/help/index.html#//00170000009n000000)the 
DEM using  a rectangle, whose spatial extent must cover the whole study area; 
1. Download the stream datasets of the study area; 
1. Process the stream datasets similar to DEM; 
1. Burn the flow line into the DEM; 
1. [Fill 
](http://help.arcgis.com/en/arcgisdesktop/10.0/help/index.html#//009z00000050000000.htm)the 
depression within the DEM; 
1. Correct the DEM in flow line. 
<div> 
<div>Explanations: 

1. DEM datasets can be downloaded from [USGS 
NED](http://nationalmap.gov/elevation.html) in various formats and 
resolutions. Make sure the DEM datasets covers the spatial extent of the study 
area; 
1. Depending on the spatial extent of the study area, it usually contains more 
than one DEM data file. Therefore, it is necessary to mosaic them into one 
file. This is because most GIS operations such as re-sample are sensitive to 
edge effects. 
1. The resample operation could bring the DEM into desired spatial resolution. 
It is common to re-sample from high resolution to low resolution; 
1. The DEM file is probably not in the desired projection under the study 
area. 
1. Computational demand is something we try to avoid if possible. Therefore it 
is best to extract the DEM out from the larger file. However, we must keep the 
valuable information. So we can clip the DEM using a large rectangle. 
1. Stream data are necessary to assist the [DEM 
reconditioning](http://www.ce.utexas.edu/prof/maidment/gishydro/ferdi/research/agree/agree.html); 
1. The stream data also needs to prepared into the same spatial extent and 
projection; 
1. Adjust the DEM so surface water can always flow into the streams. However, 
we don't want to change the DEM so much because the groundwater system also 
interacts with the stream. 
1. Surface depression causes a lot of troubles for surface runoff. For most 
surface hydrology, they can be removed through the fill operation. 
1. There might be still flaws within the DEM along the flow line, so we need 
to correct them separately. 
<div> 
<div>Most of the GIS operations can be carried out within ArcGIS. However, 
other tools such as 
[ArcHydro](http://resources.arcgis.com/en/communities/hydro/01vn0000000s000000.htm), 
[SAGA ](http://www.saga-gis.org/)are also very powerful. <div> 
<div>Next, for most cases, these operations must be carried out in the above 
order. Step 3 and 4 can change order without too many differences. For DEM 
reconditioning, it is usually good practice to follow steps 8, 9 and 10 
exactly. You will find that depressions still exist if you fill them in the 
first place since burn can change DEM. There is currently no tools can 
consider stream and depression at the same time. Double check the DEM 
afterwards is encouraged. 


<div> 
<div> 
<div> 


<div> 