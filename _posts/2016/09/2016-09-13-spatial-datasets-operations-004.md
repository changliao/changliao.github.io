---
 
title: 'Spatial datasets operations: When the sky is failing'
date: '2016-09-13T13:53:00.001-07:00'
author: Chang Liao
tags:
- ENVI
- IDL
- ArcObject
- ArcMap
modified_time: '2016-09-13T19:28:31.635-07:00'
thumbnail: https://3.bp.blogspot.com/-baguRWw81hE/V9hhPJTQN7I/AAAAAAAARTQ/GkBL_-UCxCQzgx7WXoIfSeUL89bzzLDaACLcB/s72-c/01.png
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-1651320841679241667
blogger_orig_url: https://changliao.blogspot.com/2016/09/spatial-datasets-operations-004.html
---

Not all raster can be re-projected to another projection, at least some tools don't allow us to.

For example, the AMSR-E/Aqua L3 Global Snow Water Equivalent EASE-Grids cannot be directly re-projected to UTM-6N within ENVI 5.1.
https://nsidc.org/data/docs/daac/ae_swe_ease-grids.gd.html
Please refer this website for projection information.

![Figure 1](https://github.com/changliao/changliao.github.io/blob/main/_figure/spatial_extraction01.png?raw=true)

Fortunately, ArcMap can do a better job in this scenario.
You can use the project tool just like any other operations.



![Figure 2](https://github.com/changliao/changliao.github.io/blob/main/_figure/spatial_extraction02.png?raw=true)

In order to re-project lot of data using ArcObject, I have updated a ArcTool, which is basically a batch mode data operation toolkit. For this task, the screenshot is as follow:



![Figure 3](https://github.com/changliao/changliao.github.io/blob/main/_figure/spatial_extraction03.png?raw=true)


Below is the result:



![Figure 4](https://github.com/changliao/changliao.github.io/blob/main/_figure/spatial_extraction04.png?raw=true)





Beneath the hook is the GP tool, some sample scripts are as follow:
///================================================
public static object ProjectRaster(string sFileIn, string sFileOut, string sNewProject, double dCellSize)
        {
            ESRI.ArcGIS.Geoprocessor.Geoprocessor gp = new ESRI.ArcGIS.Geoprocessor.Geoprocessor();
            ///========================================
            ///disable the pyramid 
            ///========================================
            gp.ResetEnvironments();      
            gp.SetEnvironmentValue("Pyramid", "NONE");          
            gp.OverwriteOutput = true;
            ///=================================
            ProjectRaster pProjectRaster = new ProjectRaster(sFileIn, sFileOut, sNewProject);
            pProjectRaster.cell_size = dCellSize;
            ///pProjectRaster.resampling_type = "BILINEAR";
            pProjectRaster.resampling_type = "NEAREST";
            return gp.Execute(pProjectRaster, null);
        }
///=================================================

Remember that sometimes the environment setting can be messy, so you can always setup them explicitly following (even though the ESRI document itself is a mess):

http://help.arcgis.com/en/arcgisdesktop/10.0/help/index.html?TopicName=Pyramid#/Pyramid/001w0000001w000000/


One may ask, why would you re-project such a raster to the other projection which is not supported in ENVI?
There are other methods, maybe better ones to achieve this task. And this is just a demonstration of how to make use of the GP tool in ArcObject when ENVI/IDL fails.