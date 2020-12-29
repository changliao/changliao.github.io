---
title: 'Tips for ArcSWAT issue'
date: 2019-02-28
permalink: /posts/2019/02/28/tips-for-arcswat-issue/
tags:
    - ArcGIS
    - ArcSWAT
    - SWAT
---

I have to use ArcSWAT to prepare some SWAT model simulation inputs. And the experience wasn't exactly good (maybe we need a different tool to do this the right way).

Below I listed a few issues I have encountered and potentially fixed:

Failed to create raster dataset. This issue might be related to permission control on Windows.
Based on my experience, it is best to create the project under the root directory using the ArcSWAT interface. Do not create the directory outside using other method (WSL mkdir caused this error multiple times on my Windows 10).

![Figure 1](https://github.com/changliao/changliao.github.io/blob/main/_figure/swat_error01.png?raw=true)

![Figure 2](https://github.com/changliao/changliao.github.io/blob/main/_figure/swat_error02.png?raw=true)

Object reference not set. This issue is often related to the above issue. If the DEM was successfully, you should not receive this error.



SWAT check error: SWAT check version may not be compatiable with the latest SWAT version. For example, check this discussion: https://groups.google.com/forum/#!topic/swatuser/aSsSeJVIrvU

I will keep adding related issues until the project is finished.