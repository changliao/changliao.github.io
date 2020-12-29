---
layout: post
title: Some thoughts on respiration and the role of microbe
date: '2018-04-15T19:34:00.000-07:00'
author: Chang Liao
tags:
- Mineralization
- Soil Respiration
- Decomposition
- Heterotrophic Respiration
modified_time: '2019-03-14T09:31:38.668-07:00'
thumbnail: https://1.bp.blogspot.com/-DCNtYUutdDg/WtN94E6zjPI/AAAAAAAAgoU/Mon50PmrG7sEpFQ_1vXzt1c-ukr9saseQCKgBGAs/s72-c/carbon-pool.png
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-3291670825912419859
blogger_orig_url: https://changliao.blogspot.com/2018/04/ecosystem-modeling-008.html
---

I was recently upgrading some components within the [<span style="color: 
red;">**ECO3D**](https://ecosystem3d.blogspot.com/p/welcome.html) model, 
specifically the carbon pool and fluxes in vegetation, litter and soil. 

The overall scheme of these components are illustrated in Figure 1: 
<div class="separator" style="clear: both; text-align: center;">[<img 
border="0" data-original-height="461" data-original-width="712" height="258" 
src="https://1.bp.blogspot.com/-DCNtYUutdDg/WtN94E6zjPI/AAAAAAAAgoU/Mon50PmrG7sEpFQ_1vXzt1c-ukr9saseQCKgBGAs/s400/carbon-pool.png" 
width="400" 
/>](https://1.bp.blogspot.com/-DCNtYUutdDg/WtN94E6zjPI/AAAAAAAAgoU/Mon50PmrG7sEpFQ_1vXzt1c-ukr9saseQCKgBGAs/s1600/carbon-pool.png)<div 
class="separator" style="clear: both; text-align: center;">Figure 1. The 
carbon pool and flux.<div class="separator" style="clear: both; text-align: 
left;"> 
<div class="separator" style="clear: both; text-align: left;">While it is 
well-known that the incoming carbon flux is mainly from photosynthesis 
process, which is also been well studied, the challenge is the outgoing carbon 
flux.<div class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">Without 
considering wildfire, etc., disturbance, "**respiration**" is generally 
considered the major pathway through which carbon is released back into the 
atmosphere. However, for individual site, horizontal carbon flux (DOC and DIC, 
etc.) is also important but it only services as a transport pathway.<div 
class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">In most 
terrestrial ecosystem modeling, respiration is broken into autotrophic 
respiration and heterotrophic respiration (Figure 2).<div class="separator" 
style="clear: both; text-align: center;">[<img border="0" 
data-original-height="361" data-original-width="401" height="288" 
src="https://3.bp.blogspot.com/-pFUlNH8PbiI/WtN_lYHxWQI/AAAAAAAAgog/0ksaYqRdS4g_5hUH_WeUeegB1qj3bW2LACKgBGAs/s320/respiration.png" 
width="320" 
/>](https://3.bp.blogspot.com/-pFUlNH8PbiI/WtN_lYHxWQI/AAAAAAAAgog/0ksaYqRdS4g_5hUH_WeUeegB1qj3bW2LACKgBGAs/s1600/respiration.png)<div 
class="separator" style="clear: both; text-align: center;">Figure 2. 
Respiration in terrestrial ecosystem.<div class="separator" style="clear: 
both; text-align: left;">Fundamentally, respiration is a biological and 
biochemical process occurs in cellular level. And it is assumed to convert 
organic component to energy, which the opposite process of photosynthesis.<div 
class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">In different 
fields, these processes are often labeled "soil respiration", "decomposition", 
"mineralization" and "immobilization", etc., which causes lots of confusion 
for researchers from different background.<div class="separator" style="clear: 
both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">Here I am trying 
to identify the major pathway and difference between these processes.<div 
class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">First, though 
respiration occurs at cellular level, we need to understand where these cells 
are located. For autotrophic respiration, which is usually consisted of 
maintenance respiration and growth respiration throughout the vegetation, it 
takes places within the vegetation canopy, stem and root. And the rate of 
respiration is controlled by the nutrient availability within vegetation and 
climate factors.<div class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">For 
heterotrophic respiration, it usually takes place within microbe, which uses 
this process to obtain energy. Along with this process, large organic carbon 
molecular maybe decomposed into small molecular and carbon dioxide/water will 
be produced. In another word, this respiration process is linked with 
decomposition process. In some cases, small inorganic carbon may be produced 
and the respiration is also coupled with the so called "mineralization".<div 
class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">As a result, 
heterotrophic respiration is always linked with decomposition and 
mineralization but they are not exchangeable because they all have different 
focus under different context. For example, when litter is decomposed in the 
early stage due to physical process such as heat, it is generally not 
considered as respiration or mineralization. <div class="separator" 
style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;">Because of its 
dependency of microbe activity on temperature, these processes are often 
modeled using a Q10 function. However, care must be taken to consider the 
board definition of decomposition and other factors. Other than that, when 
modeling these processes, we must make sure they share the same 
characteristics because they are possibly taking place within the same 
cellular level.<div class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;"> 
<div class="separator" style="clear: both; text-align: left;"> 