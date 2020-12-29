---
layout: post
title: 'Surface water hydrology modeling: deal with different types of precipitation'
date: '2016-04-29T16:54:00.000-07:00'
author: Chang Liao
tags:
- Precipitation
- Snow
- PRMS
- SWAT
modified_time: '2019-09-18T10:49:40.068-07:00'
thumbnail: https://4.bp.blogspot.com/-Q12F-KpAIQ8/WIPWzRA4L-I/AAAAAAAAUgs/QQh9sJu8_j0N1KTNe29yZ8RAc33QvCijwCLcB/s72-c/snow_or_rain.jpg
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-7514953489820814314
blogger_orig_url: https://changliao.blogspot.com/2016/04/surface-water-hydrology-modeling-001.html
---

<span style="font-family: inherit;">In surface water hydrology, precipitation 
is one of the most important components. 
<span style="font-family: inherit;">However, within most hydrology models, it 
is unclear of how precipitation is actually represented. 
For example, in a typical water cycle illustration from 
[Wiki](https://en.wikipedia.org/wiki/Precipitation), precipitation is 
described as 
<div style="text-align: center;"><div style="text-align: center;"><img 
height="273" 
src="https://upload.wikimedia.org/wikipedia/commons/9/94/Water_cycle.png" 
width="400" /><div style="text-align: left;">Here is the question, what form 
does precipitation actually take when it falls to land surface?<div 
style="text-align: left;">Water can be in either liquid (water, rain), solid 
(ice, snow) or gas (water vapor) forms. How about precipitation? Surely most 
of time precipitation is either rain of snow. In some cases, it takes form in 
hail, etc.<div style="text-align: left;"> 
<div style="text-align: left;">Since the physical proprieties of water and 
snow are significantly different, it is necessary to distinguish them within 
surface water hydrology models.<div style="text-align: left;">In some 
scenarios, rain and snow may co-exist in a [mixed 
precipitation](https://en.wikipedia.org/wiki/Rain_and_snow_mixed) event. In 
this case, surface water hydrology models need to deal with both of them. The 
difficulty is how to manage the two-phase mass and energy balance.<div 
style="text-align: left;">A complete comparison of how different models deal 
with this scenario will be presented later. 

<span style="color: red;">**Updates: 21, January 2017** 
<span style="color: red;">**After reviewing some typical surface hydrology 
model, I decided to use the following scheme in my ecosystem model.** 
<span style="color: red;">**This approach uses the maximum and minimum 
temperature and two parameters to decide the precipitation type.** 
<span style="color: red;">**When it is a mixture event, a linear method is 
used estimate the portion of rain or snow in precipitation.** 

<div style="text-align: left;"><div class="separator" style="clear: both; 
text-align: center;"><div class="separator" style="clear: both; text-align: 
center;">[<img border="0" height="420" 
src="https://4.bp.blogspot.com/-Q12F-KpAIQ8/WIPWzRA4L-I/AAAAAAAAUgs/QQh9sJu8_j0N1KTNe29yZ8RAc33QvCijwCLcB/s640/snow_or_rain.jpg" 
width="640" 
/>](https://4.bp.blogspot.com/-Q12F-KpAIQ8/WIPWzRA4L-I/AAAAAAAAUgs/QQh9sJu8_j0N1KTNe29yZ8RAc33QvCijwCLcB/s1600/snow_or_rain.jpg) 
<div style="text-align: left;">Copy right of  Purdue University. Please 
contact me if you want to use this figure. Thanks.<div style="text-align: 
left;"> 
<div style="text-align: left;"> 