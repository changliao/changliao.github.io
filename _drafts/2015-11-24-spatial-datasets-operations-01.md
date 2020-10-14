---
layout: post
title: 'Spatial datasets operations: mask raster using region of interest'
date: '2015-11-24T17:01:00.000-08:00'
author: Chang Liao
tags:
- ENVI
- IDL
- Shapefile
- ArcMap
- ROI
- Extract
modified_time: '2016-01-26T11:27:01.276-08:00'
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-2661957083325641186
blogger_orig_url: https://www.changliao.us/2015/11/spatial-datasets-operations-01.html
---

Climate change related studies usually involve spatial datasets extraction 
from a larger domain. 
In this article, I will briefly discuss some potential issues and solutions. 

In the most common scenario, we need to extract a raster file using a polygon 
based shapefile. And I will focus as an example. 

In a typical desktop application such as [ArcMap 
](https://desktop.arcgis.com/en/desktop/)or 
[ENVI](http://www.exelisvis.com/ProductsServices/ENVIProducts/ENVI.aspx), this 
is usually done with a tool called [clip 
](http://resources.arcgis.com/en/help/main/10.1/index.html#//00170000009n000000)or 
[extract 
](http://resources.arcgis.com/EN/HELP/MAIN/10.1/index.html#//009z0000002n000000)using 
mask or [ROI](https://www.exelisvis.com/docs/regionofinteresttool.html). 

Before any analysis can be done, it is the best practice to project all 
datasets into the same projection. 

If you are lucky enough, you may find that the polygon you will use actually 
matches up with the raster grid perfectly. But it rarely happens unless you 
created the shapefile using 
"[fishnet](http://resources.arcgis.com/EN/HELP/MAIN/10.1/index.html#//00170000002q000000)" 
or other approaches. 

What if luck is not with you? The algorithm within these tool usually will 
make the best estimate of the value based on the location. The nearest 
re-sample, but not limited to, will be used to calculate the value. But what 
about the output location of the new data. Since the output will also be a 
raster with the same resolution, it the best solution that the output raster 
can match up with input raster perfectly. 

Another issue is the efficiency because we usually have more than one raster 
need to be extracted from. Apparently this could be done using programming. 
Since ArcGIS doesn't support quite well on Linux, it is very naturally we use 
IDL/ENVI to achieve the task. In ENVI, the concept of ROI is used to extract 
raster. However there is another issue, ROI and the input raster have a one to 
one relation, which means that you can't use one single ROI to extract all the 
raster. The good news is that we can dynamically create ROI from shapefile 
using APIs. 

There are some articles online stating that you can open a shapefile directly 
and store it as the FID, which can be used as the mask. It is NOT going to 
work. Instead, you need to create a shapefile object and retrieve all the 
boundary locations, then you can get all the values needed.The last step will 
be save the data with spatial reference. 

Some incomplete demo code using IDL is listed here: 

<div style="text-align: left;">1. *<span style="font-size: x-small;">        * 
  ;;Read shapefile 
1.            oshp = OBJ_NEW('IDLffshape', shapefile_in) 
1.            oshp -&gt; GetProperty, n_entities = n_ent, Attribute_info = 
attr_info, $ 
1.                                 n_attributes = n_attr, Entity_type = 
ent_type 
1.            roi_shp = LONARR(n_ent) 
1.            FOR ishp = 0, n_ent - 1 DO BEGIN 
1.               entitie = oshp -&gt; GetEntity(ishp) 
1.               ;;Check polygon 
1.               IF entitie.SHAPE_TYPE EQ 5 THEN BEGIN 
1.                  record = *(entitie.VERTICES) 
1.                  ;;Convert coordinates 
1.                  ENVI_CONVERT_FILE_COORDINATES, fid_in, xmap, ymap, 
record[0, *], record[1, *] 
1.                  ;;Create ROI 
1.                  roi_shp[ishp] = ENVI_CREATE_ROI(ns = ns_in, nl = nl_in) 
1.                  ENVI_DEFINE_ROI, roi_shp[ishp], /polygon, xpts = 
REFORM(xmap), ypts = REFORM(ymap) 
1.                  IF ishp EQ 0 THEN BEGIN 
1.                     ;;nearest sampling is used 
1.                     xmin = ROUND(MIN(xMap)) 
1.                     yMin = ROUND(MIN(yMap)) 
1.                  ENDIF ELSE BEGIN 
1.                     ;;there should be only one polygon in most cases 
1.                     RETURN 
1.                  ENDELSE 
1.               ENDIF 
1.               oshp -&gt; DestroyEntity, entitie 
1.            ENDFOR 
1.            ;;apply the mask 
1.            ENVI_MASK_DOIT, AND_OR = 1, /IN_MEMORY, ROI_IDS = roi_shp, $ 
1.                            ns = ns_in, nl = nl_in, /inside, $ 
1.                            r_fid = fid_mask 
1.            ;;define the output raster array 
1.            dims_mask = [-1, xMin, (xMin + ncol - 1), yMin, (ymin + nrow - 
1)] 
1.            m_pos = [0] 
1.            ;;subset the input raster and save it within the memory 
1.            filename_out = year_out + !slash + prefix_out + year_str + 
day_str + envi_extension 
1.            ENVI_MASK_APPLY_DOIT, FID = fid_in, POS = pos, DIMS = dims_mask, 
$ 
1.                                  M_FID = fid_mask, M_POS = m_pos, VALUE = 
missing_value, /in_memory, $ 
1.                                  R_FID = fid_out 
1.            ENVI_FILE_QUERY, fid_out, ns = ns_out, nl = nl_out, nb = nb_out, 
bname = bname_out, dims = dims_out 
1.            data = ENVI_GET_DATA(fid = fid_out, dims = dims_out, pos = pos) 
1.            ;;output with pre-defined spatial reference 
1.            ENVI_WRITE_ENVI_FILE, FLOAT(data), map_info = map_info, out_name 
= filename_out, $ 
1.                                  nb = nb_out, ns = ncol, nl = nrow, OUT_DT 
= 4 


Feel free to try it out and give me feedback. 