---
 
title: 'Surface water hydrology modeling: deal with different types of precipitation'
date: '2016-04-29T16:54:00.000-07:00'
author: Chang Liao
tags:
- Precipitation
- Snow
- PRMS
- SWAT
modified_time: '2019-09-18T10:49:40.068-07:00'
---

In surface water hydrology, precipitation is one of the most important components.
However, within most hydrology models, it is unclear of how precipitation is actually represented.
For example, in a typical water cycle illustration from Wiki, precipitation is described as

![Figure 1](https://github.com/changliao/changliao.github.io/blob/main/_figure/water_cycle.png?raw=true)

Here is the question, what form does precipitation actually take when it falls to land surface?
Water can be in either liquid (water, rain), solid (ice, snow) or gas (water vapor) forms. How about precipitation? Surely most of time precipitation is either rain of snow. In some cases, it takes form in hail, etc.

Since the physical proprieties of water and snow are significantly different, it is necessary to distinguish them within surface water hydrology models.
In some scenarios, rain and snow may co-exist in a mixed precipitation event. In this case, surface water hydrology models need to deal with both of them. The difficulty is how to manage the two-phase mass and energy balance.
A complete comparison of how different models deal with this scenario will be presented later.

Updates: 21, January 2017
After reviewing some typical surface hydrology model, I decided to use the following scheme in my ecosystem model.
This approach uses the maximum and minimum temperature and two parameters to decide the precipitation type.
When it is a mixture event, a linear method is used estimate the portion of rain or snow in precipitation.

![Figure 2](https://github.com/changliao/changliao.github.io/blob/main/_figure/snow_or_rain.png?raw=true)

Copy right of  Purdue University. Please contact me if you want to use this figure. Thanks.