---
layout: post
title: 'Spatial datasets operations: From MODIS HDF to Binary file'
date: '2016-09-12T14:49:00.001-07:00'
author: Chang Liao
tags:
- ENVI
- IDL
- ArcMap
- MODIS
modified_time: '2016-09-13T20:48:10.160-07:00'
thumbnail: https://1.bp.blogspot.com/-XC5pvCY_NOA/V9cXwM1OdWI/AAAAAAAARQ4/_4AYn6ZvygoXlMcAXU-7HoMeKmBRj6PLwCLcB/s72-c/sce_arcmap.png
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-3996357905520631366
blogger_orig_url: https://www.changliao.us/2016/09/spatial-datasets-operations-002.html
---

<div class="separator" style="clear: both; text-align: left;">MODIS products 
are widely used in Earth Science, here I present some typical demos and 
tryouts to deal with MODIS datasets.<div class="separator" style="clear: both; 
text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">All the MODIS 
products datasets are distributed in HDF format.<div class="separator" 
style="clear: both; text-align: left;">To get familiar with HDF, you can go 
to:<div class="separator" style="clear: both; text-align: 
left;">[https://en.wikipedia.org/wiki/Hierarchical_Data_Format](https://en.wikipedia.org/wiki/Hierarchical_Data_Format)<div 
class="separator" style="clear: both; text-align: left;">or <div 
class="separator" style="clear: both; text-align: 
left;">[https://www.hdfgroup.org/HDF5/](https://www.hdfgroup.org/HDF5/)<div 
class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">MODIS land 
surface products usually have a different map projection than most of our 
projects.<div class="separator" style="clear: both; text-align: left;">Here 
are some information of this projection:<div class="separator" style="clear: 
both; text-align: 
left;">[http://modis-land.gsfc.nasa.gov/MODLAND_grid.html](http://modis-land.gsfc.nasa.gov/MODLAND_grid.html)<div 
class="separator" style="clear: both; text-align: left;">Therefore, a 
re-project is needed to convert HDF datasets to our projects.<div 
class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">There are quite 
a few tools available to operate on HDF files, but most of them are not 
efficient enough. You have to repeat the same set of operations. Therefore, 
using IDL or ArcObject based script/program is desirable.<div 
class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">The first step 
is to extract the datasets from HDF, and we also need to define the projection 
as exactly the same with HDF. Below is a very simple way to do so. You can use 
ArcMap to open one single HDF file and output the datasets as TIFF or other 
raster datasets formats.<div class="separator" style="clear: both; text-align: 
center;"> 
<div class="separator" style="clear: both; text-align: center;">[<img 
border="0" height="347" 
src="https://1.bp.blogspot.com/-XC5pvCY_NOA/V9cXwM1OdWI/AAAAAAAARQ4/_4AYn6ZvygoXlMcAXU-7HoMeKmBRj6PLwCLcB/s640/sce_arcmap.png" 
width="640" 
/>](https://1.bp.blogspot.com/-XC5pvCY_NOA/V9cXwM1OdWI/AAAAAAAARQ4/_4AYn6ZvygoXlMcAXU-7HoMeKmBRj6PLwCLcB/s1600/sce_arcmap.png)<div 
class="separator" style="clear: both; text-align: center;">Fig 1. Convert 
result from HDF to GeoTIFF in ArcMap 10.1.<div class="separator" style="clear: 
both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">Unfortunately, 
ENVI doesn't support all the MODIS product quite well so far. And the map 
projection cannot be read after the conversion using ArcMap, see below.<div 
class="separator" style="clear: both; text-align: left;"> 

<div class="separator" style="clear: both; text-align: center;">[<img 
border="0" height="396" 
src="https://2.bp.blogspot.com/-tn1n38KBrcM/V9cYfHa6ttI/AAAAAAAARRA/Hgs17QqFqzIW8nfSkYGid4PkP_thPC-MwCLcB/s640/sce_envi.png" 
width="640" 
/>](https://2.bp.blogspot.com/-tn1n38KBrcM/V9cYfHa6ttI/AAAAAAAARRA/Hgs17QqFqzIW8nfSkYGid4PkP_thPC-MwCLcB/s1600/sce_envi.png)<div 
class="separator" style="clear: both; text-align: center;">Fig 2. File viewing 
in ENVI 5.1 of the same file. 

Even though ENVI can directly open this file, this does not mean we can open 
the file using ENVI/IDL 
;;=================================================== 
  IF FILE_TEST(filename_in) EQ 1 THEN BEGIN 
        PRINT, filename_in 
        ENVI_OPEN_FILE, filename_in, r_fid = r_fid 
        IF r_fid NE -1 THEN BEGIN 
          ENVI_FILE_QUERY, r_fid, dims = dims, nb = nb 
          pos = LINDGEN(nb) 
          filename_out = year_out + !slash + prefix_out + year_str + day_str + 
extension_envi 
          ENVI_CONVERT_FILE_MAP_PROJECTION, background = missing_value, $ 
            dims = dims, $ 
            fid = r_fid, $ 
            grid = [10, 10], $ 
            o_pixel_size = o_pixel_size, o_proj = map_info, out_name = 
filename_out, $ 
            pos = pos, $ 
            resampling = 0, $ 
            warp_method = 0 
          ENVI_FILE_MNG, id = r_fid, /remove 
        ENDIF ELSE BEGIN 
          PRINT, 'Cannot open the file!' 
        ENDELSE 
      ENDIF 
;;================================================== 

For the same file, above script will print "Cannot open the file!" 

A workaround method is using the GeoTIFF instead of native ENVI dat file. 
You can pass either the geotag using a filename or a struct in the ENVI/IDL 
script. 
After this, you will get a binary dat file with a header file which contains 
the map projection information. 

The bottom line is that you can prepare individual files (for parameters) 
using ArcMap and run ENVI/IDL scripts on HPC. In this case, you gain both 
flexibility and efficiency. 