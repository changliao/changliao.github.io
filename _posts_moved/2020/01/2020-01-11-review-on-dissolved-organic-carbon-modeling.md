---
title: 'A review on dissolved organic carbon modeling'
date: 2020-01-11
permalink: /posts/2020/01/11/review-on-dissolved-organic-carbon-modeling/
tags:
  - Dissolved organic carbon
---
Researchgate and Mendeley recommend some nice papers to me based on my own publications. Here are some quick review on the DOC modeling I read today.

The first one:
Simulation of dissolved organic carbon concentrations and fluxes in Chinese monsoon forest ecosystems using a modified TRIPLEX-DOC model
This model is unlikely ready for spatial simulation. It does not consider DOC from litterfall as well.
There is some confusion about the term "DOC leaching", which should include both from litter and soil.

The second one:
ORCHIDEE MICT-LEAK (r5459), a global model for the production, transport, and transformation of dissolved organic carbon from Arctic permafrost regions–Part 1: Rationale, model description, and simulation protocol 
This model seems to very complex in terms for DOC modeling. It does capture some most important processes. But some statements are not convincing due to the complexity of the model. Also, it does not consider lateral flow process well enough.

Compared with my earlier study, there are some limitations in current land surface modeling:


* Current LSM resolution is so coarse that they don't consider land-land interactions. They only consider land-river, land-lake interactions. As a result, in the future development, if we plan to run LSM simulation at high resolution (1k~5k), the current LSM structure is not ready and great efforts are needed to modify the connectivity;
* DOC in the groundwater is not well represented. This is mainly because LSM generally cannot simulation deep groundwater including confined groundwater system;
* The current state of LSM are not ready to be coupled with ocean in terms of grid discretization. A unified grid is required to couple global LSM with ocean model. It is highly likely we need an adaptive resolution grid to represent and resolve some interface issue because of computational and scaling issue.

It is important for us to develop model with the idea of simplicity.

There is still lots of work to do.