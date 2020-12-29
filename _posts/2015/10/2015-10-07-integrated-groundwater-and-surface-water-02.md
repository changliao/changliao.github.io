---
 
title: 'Integrated groundwater and surface water modeling: restore the stream index
  relationship'
date: '2015-10-07T09:06:00.001-07:00'
author: Chang Liao
tags:
- Arc Hydro
- IDL
- ArcMap
modified_time: '2015-10-07T09:08:44.453-07:00'

---

Numerical hydrology models usually require the stream index to be built prior to the actual simulation.
It is also good practice to keep them in order so it is much easier to analyse the results.

Here I have provided an examples how it could be done using some scripts and ArcMap.


After the drainage line is defined from watershed delineation process such as using Arc Hydro tool.
The resulting attribute table will be like this:

![Figure 1](https://github.com/changliao/changliao.github.io/blob/main/_figure/drainagelin.png?raw=true)



First, it is good practice to make a copy of the file. Then we need to "Delete" unwanted fields and only keep the HydroID, GridID and NextdownID fields.
Then export the attribute table into a text file and run the IDL routine "restore_drainageline_spatial_relationship", which will produce a new index for each stream segment.
You can copy the created text file content into the Microsoft Excel for next step.
Then edit the drainage shapefile feature and replace the HydroID and NextdownID fields using the just copied indices in the Excel.
After this, the spatial relationship is restored but not sorted in the attribute table. We can use the "Sort" tool is sort them using HydroID field. 



![Figure 2](https://github.com/changliao/changliao.github.io/blob/main/_figure/field_sort.png?raw=true)



The final attribute table will be like this:

![Figure 3](https://github.com/changliao/changliao.github.io/blob/main/_figure/sort_table.png?raw=true)

Well done! This attribute table is ready for other operations.

Please leave a comment if you have questions!
Thank you!
