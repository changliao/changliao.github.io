---
layout: post
title: A review on dissolved organic carbon modeling
date: '2020-01-11T15:48:00.001-08:00'
author: Chang Liao
tags:
- Lateral Flow
- DOC
- Carbon
- LSM
modified_time: '2020-01-11T15:48:36.928-08:00'
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-6610303072478595743
blogger_orig_url: https://www.changliao.us/2020/01/a-review-on-dissolved-organic-carbon.html
---

Researchgate and Mendeley recommend some nice papers to me based on my own 
publications. Here are some quick review on the DOC modeling I read today. 

The first one: 
Simulation of dissolved organic carbon concentrations and fluxes in Chinese 
monsoon forest ecosystems using a modified TRIPLEX-DOC model 
This model is unlikely ready for spatial simulation. It does not consider DOC 
from litterfall as well. 
There is some confusion about the term "DOC leaching", which should include 
both from litter and soil. 

The second one: 
ORCHIDEE MICT-LEAK (r5459), a global model for the production, transport, and 
transformation of dissolved organic carbon from Arctic permafrost regions–Part 
1: Rationale, model description, and simulation protocol 
This model seems to very complex in terms for DOC modeling. It does capture 
some most important processes. But some statements are not convincing due to 
the complexity of the model. Also, it does not consider lateral flow process 
well enough. 

Compared with my earlier study, there are some limitations in current land 
surface modeling: 


1. Current LSM resolution is so coarse that they don't consider land-land 
interactions. They only consider land-river, land-lake interactions. As a 
result, in the future development, if we plan to run LSM simulation at high 
resolution (1k~5k), the current LSM structure is not ready and great efforts 
are needed to modify the connectivity; 
1. DOC in the groundwater is not well represented. This is mainly because LSM 
generally cannot simulation deep groundwater including confined groundwater 
system; 
1. The current state of LSM are not ready to be coupled with ocean in terms of 
grid discretization. A unified grid is required to couple global LSM with 
ocean model. It is highly likely we need an adaptive resolution grid to 
represent and resolve some interface issue because of computational and 
scaling issue. 
<div>It is important for us to develop model with the idea of simplicity.<div> 
<div>There is still lots of work to do. 