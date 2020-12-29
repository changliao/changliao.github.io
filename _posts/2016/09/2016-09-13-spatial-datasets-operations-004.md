---
layout: post
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

Not all raster can be re-projected to another projection, at least some tools 
don't allow us to. 

For example, the AMSR-E/Aqua L3 Global Snow Water Equivalent EASE-Grids cannot 
be directly re-projected to UTM-6N within ENVI 5.1. 

[https://nsidc.org/data/docs/daac/ae_swe_ease-grids.gd.html](https://nsidc.org/data/docs/daac/ae_swe_ease-grids.gd.html) 
Please refer this website for projection information. 
<div class="separator" style="clear: both; text-align: center;">[<img 
border="0" height="515" 
src="https://3.bp.blogspot.com/-baguRWw81hE/V9hhPJTQN7I/AAAAAAAARTQ/GkBL_-UCxCQzgx7WXoIfSeUL89bzzLDaACLcB/s640/01.png" 
width="640" 
/>](https://3.bp.blogspot.com/-baguRWw81hE/V9hhPJTQN7I/AAAAAAAARTQ/GkBL_-UCxCQzgx7WXoIfSeUL89bzzLDaACLcB/s1600/01.png) 
<div class="separator" style="clear: both; text-align: center;">[<img 
border="0" height="486" 
src="https://2.bp.blogspot.com/-zBL9McPulvc/V9hhO7Y0ToI/AAAAAAAARTM/_D2YKo_3wIgsTkAbVhqYB6aul2Lzzg0yACLcB/s640/02.png" 
width="640" 
/>](https://2.bp.blogspot.com/-zBL9McPulvc/V9hhO7Y0ToI/AAAAAAAARTM/_D2YKo_3wIgsTkAbVhqYB6aul2Lzzg0yACLcB/s1600/02.png) 
Fortunately, ArcMap can do a better job in this scenario. 
You can use the project tool just like any other operations. 

In order to re-project lot of data using ArcObject, I have updated a ArcTool, 
which is basically a batch mode data operation toolkit. For this task, the 
screenshot is as follow: 


<div class="separator" style="clear: both; text-align: center;">[<img 
border="0" height="323" 
src="https://1.bp.blogspot.com/-tKr5LzAoJtA/V9hhO8IDvTI/AAAAAAAARTU/zbmynATvSx4_4rcMjUSBIs2I8aEviw9kwCLcB/s400/03.png" 
width="400" 
/>](https://1.bp.blogspot.com/-tKr5LzAoJtA/V9hhO8IDvTI/AAAAAAAARTU/zbmynATvSx4_4rcMjUSBIs2I8aEviw9kwCLcB/s1600/03.png)<div 
class="separator" style="clear: both; text-align: center;"> 
<div class="separator" style="clear: both; text-align: left;">Below is the 
result:<div class="separator" style="clear: both; text-align: center;"> 
<div class="separator" style="clear: both; text-align: center;">[<img 
border="0" height="344" 
src="https://2.bp.blogspot.com/-6hfRwGYCniI/V9i0J4fQaZI/AAAAAAAARTk/wktVlCu51LcZhh7HK_7sB8iw0_45N0k5QCLcB/s640/04.png" 
width="640" 
/>](https://2.bp.blogspot.com/-6hfRwGYCniI/V9i0J4fQaZI/AAAAAAAARTk/wktVlCu51LcZhh7HK_7sB8iw0_45N0k5QCLcB/s1600/04.png)<div 
class="separator" style="clear: both; text-align: center;"> 
<div class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">Beneath the hook 
is the GP tool, some sample scripts are as follow:<div class="separator" 
style="clear: both; text-align: 
left;">///================================================<div 
class="separator" style="clear: both;">public static object 
ProjectRaster(string sFileIn, string sFileOut, string sNewProject, double 
dCellSize)<div class="separator" style="clear: both;">        {<div 
class="separator" style="clear: both;">            
ESRI.ArcGIS.Geoprocessor.Geoprocessor gp = new 
ESRI.ArcGIS.Geoprocessor.Geoprocessor();<div class="separator" style="clear: 
both;">            ///========================================<div 
class="separator" style="clear: both;">            ///disable the pyramid <div 
class="separator" style="clear: both;">            
///========================================<div class="separator" 
style="clear: both;">            gp.ResetEnvironments();      <div 
class="separator" style="clear: both;">            
gp.SetEnvironmentValue("Pyramid", "NONE");          <div class="separator" 
style="clear: both;">            gp.OverwriteOutput = true;<div 
class="separator" style="clear: both;">            
///=================================<div class="separator" style="clear: 
both;">            ProjectRaster pProjectRaster = new ProjectRaster(sFileIn, 
sFileOut, sNewProject);<div class="separator" style="clear: both;">            
pProjectRaster.cell_size = dCellSize;<div class="separator" style="clear: 
both;">            ///pProjectRaster.resampling_type = "BILINEAR";<div 
class="separator" style="clear: both;">            
pProjectRaster.resampling_type = "NEAREST";<div class="separator" 
style="clear: both;">            return gp.Execute(pProjectRaster, null);<div 
class="separator" style="clear: both;">        }<div class="separator" 
style="clear: both; text-align: 
left;">///=================================================<div 
class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">Remember that 
sometimes the environment setting can be messy, so you can always setup them 
explicitly following (even though the ESRI document itself is a mess):<div 
class="separator" style="clear: both; text-align: center;"> 
<div class="separator" style="clear: both; text-align: 
left;">[http://help.arcgis.com/en/arcgisdesktop/10.0/help/index.html?TopicName=Pyramid#/Pyramid/001w0000001w000000/](http://help.arcgis.com/en/arcgisdesktop/10.0/help/index.html?TopicName=Pyramid#/Pyramid/001w0000001w000000/)<div 
class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">One may ask, why 
would you re-project such a raster to the other projection which is not 
supported in ENVI?<div class="separator" style="clear: both; text-align: 
left;">There are other methods, maybe better ones to achieve this task. And 
this is just a demonstration of how to make use of the GP tool in ArcObject 
when ENVI/IDL fails. 