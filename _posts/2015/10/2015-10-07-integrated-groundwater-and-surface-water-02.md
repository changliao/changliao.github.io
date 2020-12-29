---
layout: post
title: 'Integrated groundwater and surface water modeling: restore the stream index
  relationship'
date: '2015-10-07T09:06:00.001-07:00'
author: Chang Liao
tags:
- Arc Hydro
- IDL
- ArcMap
modified_time: '2015-10-07T09:08:44.453-07:00'
thumbnail: http://1.bp.blogspot.com/-xhao4COBa38/VhU_42pN_eI/AAAAAAAALkE/SB-9gZaKpr0/s72-c/drainageline.png
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-592986730039710075
blogger_orig_url: https://changliao.blogspot.com/2015/10/integrated-groundwater-and-surface-water-02.html
---

Numerical hydrology models usually require the stream index to be built prior 
to the actual simulation. 
It is also good practice to keep them in order so it is much easier to analyse 
the results. 

Here I have provided an examples how it could be done using some scripts and 
[ArcMap](http://www.esri.com/software/arcgis). 
After the drainage line is defined from watershed delineation process such as 
using [Arc Hydro 
tool](http://resources.arcgis.com/en/communities/hydro/01vn0000000s000000.htm). 
The resulting attribute table will be like this: 
<div class="separator" style="clear: both; text-align: center;">[<img 
border="0" height="400" 
src="http://1.bp.blogspot.com/-xhao4COBa38/VhU_42pN_eI/AAAAAAAALkE/SB-9gZaKpr0/s400/drainageline.png" 
width="392" 
/>](http://1.bp.blogspot.com/-xhao4COBa38/VhU_42pN_eI/AAAAAAAALkE/SB-9gZaKpr0/s1600/drainageline.png)<div 
class="separator" style="clear: both; text-align: center;"> 
<div class="separator" style="clear: both; text-align: left;">First, it is 
good practice to make a copy of the file. Then we need to 
"[Delete](http://help.arcgis.com/EN/arcgisdesktop/10.0/help/index.html#//00170000004n000000)" 
unwanted fields and only keep the HydroID, GridID and NextdownID fields.<div 
class="separator" style="clear: both; text-align: left;">Then export the 
attribute table into a text file and run the IDL routine 
"restore_drainageline_spatial_relationship", which will produce a new index 
for each stream segment.<div class="separator" style="clear: both; text-align: 
left;">You can copy the created text file content into the Microsoft Excel for 
next step.<div class="separator" style="clear: both; text-align: left;">Then 
edit the drainage shapefile feature and replace the HydroID and NextdownID 
fields using the just copied indices in the Excel.<div class="separator" 
style="clear: both; text-align: left;">After this, the spatial relationship is 
restored but not sorted in the attribute table. We can use the 
"[Sort](http://help.arcgis.com/EN/arcgisdesktop/10.0/help/index.html#//001700000057000000)" 
tool is sort them using HydroID field. <div class="separator" style="clear: 
both; text-align: center;">[<img border="0" height="301" 
src="http://3.bp.blogspot.com/-gEO-EuomrTU/VhVB0ylQxrI/AAAAAAAALkU/amLv9R1Maho/s400/field_sort.png" 
width="400" 
/>](http://3.bp.blogspot.com/-gEO-EuomrTU/VhVB0ylQxrI/AAAAAAAALkU/amLv9R1Maho/s1600/field_sort.png)<div 
class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">The final 
attribute table will be like this:<div class="separator" style="clear: both; 
text-align: center;">[<img border="0" height="640" 
src="http://1.bp.blogspot.com/-h2ZUSNe1Hxg/VhVB_y7BB7I/AAAAAAAALkY/XEeEGtY0jmU/s640/sort_table.png" 
width="473" 
/>](http://1.bp.blogspot.com/-h2ZUSNe1Hxg/VhVB_y7BB7I/AAAAAAAALkY/XEeEGtY0jmU/s1600/sort_table.png)<div 
class="separator" style="clear: both; text-align: left;">Well done! This 
attribute table is ready for other operations.<div class="separator" 
style="clear: both; text-align: left;"> 
Please leave a comment if you have questions! 
Thank you! 