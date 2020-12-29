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
blogger_orig_url: https://changliao.blogspot.com/2016/09/spatial-datasets-operations-002.html
---
MODIS products are widely used in Earth Science, here I present some typical demos and tryouts to deal with MODIS datasets.

All the MODIS products datasets are distributed in HDF format.
To get familiar with HDF, you can go to:
https://en.wikipedia.org/wiki/Hierarchical_Data_Format
or 
https://www.hdfgroup.org/HDF5/


MODIS land surface products usually have a different map projection than most of our projects.
Here are some information of this projection:
http://modis-land.gsfc.nasa.gov/MODLAND_grid.html
Therefore, a re-project is needed to convert HDF datasets to our projects.


There are quite a few tools available to operate on HDF files, but most of them are not efficient enough. You have to repeat the same set of operations. Therefore, using IDL or ArcObject based script/program is desirable.

The first step is to extract the datasets from HDF, and we also need to define the projection as exactly the same with HDF. Below is a very simple way to do so. You can use ArcMap to open one single HDF file and output the datasets as TIFF or other raster datasets formats.

![Figure 1](https://github.com/changliao/changliao.github.io/blob/main/_figure/modis01.png?raw=true)


Fig 1. Convert result from HDF to GeoTIFF in ArcMap 10.1.

Unfortunately, ENVI doesn't support all the MODIS product quite well so far. And the map projection cannot be read after the conversion using ArcMap, see below.

![Figure 2](https://github.com/changliao/changliao.github.io/blob/main/_figure/modis02.png?raw=true)

Fig 2. File viewing in ENVI 5.1 of the same file.


Even though ENVI can directly open this file, this does not mean we can open the file using ENVI/IDL
;;===================================================
  IF FILE_TEST(filename_in) EQ 1 THEN BEGIN
        PRINT, filename_in    
        ENVI_OPEN_FILE, filename_in, r_fid = r_fid
        IF r_fid NE -1 THEN BEGIN
          ENVI_FILE_QUERY, r_fid, dims = dims, nb = nb
          pos = LINDGEN(nb)
          filename_out = year_out + !slash + prefix_out + year_str + day_str + extension_envi
          ENVI_CONVERT_FILE_MAP_PROJECTION, background = missing_value,  dims=dims, 
            fid = r_fid,  grid=[10,10], 
            o_pixel_size = o_pixel_size, o_proj = map_info, out_name = filename_out,  pos=pos, 
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
You can pass either the geotag using a filename or a struct in the ENVI/IDL script.
After this, you will get a binary dat file with a header file which contains the map projection information.

The bottom line is that you can prepare individual files (for parameters) using ArcMap and run ENVI/IDL scripts on HPC. In this case, you gain both flexibility and efficiency.