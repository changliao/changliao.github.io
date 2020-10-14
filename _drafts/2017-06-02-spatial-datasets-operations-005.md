---
layout: post
title: 'Spatial datasets operations: an overview of global climate dataset and interpolation'
date: '2017-06-02T07:18:00.000-07:00'
author: Chang Liao
tags:
- Anusplin
- ANN
modified_time: '2018-04-03T12:17:59.571-07:00'
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-1037807517236776229
blogger_orig_url: https://www.changliao.us/2017/06/spatial-datasets-operations-005.html
---

Climate dataset is literally the most important data in climate change 
research. Great efforts have been made to prepare climate dataset over the 
decades. 

In my recent project, I need to prepare some climate dataset at global scale. 
Then I have to take some time to finish a review of current state of climate 
dataset at global scale. 

First, I want to emphasize "global scale" including both arctic and antarctic. 
Because I will use this data in a three-dimensional ecosystem simulation, a 
special configuration of the data structure will be used, which is completely 
different from traditional approaches. 

Second, where or how can we get the climate data? 

The easiest source we can turn to is existing global climate dataset, such as 
CRU dataset, NCEP dataset. I try not to get into details of these data but 
rather list the source and state some critical aspects that we have to take 
into consideration. 

CRU: 
[http://www.cru.uea.ac.uk/data](http://www.cru.uea.ac.uk/data) 

[http://www.ipcc-data.org/observ/clim/cru_climatologies.html](http://www.ipcc-data.org/observ/clim/cru_climatologies.html) 
NCEP: 

[https://www.esrl.noaa.gov/psd/data/reanalysis/reanalysis.shtml](https://www.esrl.noaa.gov/psd/data/reanalysis/reanalysis.shtml) 
ECMWF 

[https://www.ecmwf.int/en/research/climate-reanalysis](https://www.ecmwf.int/en/research/climate-reanalysis) 
WorldClim 
[http://www.worldclim.org/](http://www.worldclim.org/) 

Pros: 
1. Easy to use 
1. Global coverage 

Cons: 
1. Missing polar regions 
1. Coarse resolution 


Based on meteorology site observations, many spatial interpolation methods can 
also be used to produce spatial dataset. 
IDW 

[https://en.wikipedia.org/wiki/Inverse_distance_weighting](https://en.wikipedia.org/wiki/Inverse_distance_weighting) 
Kriging 
[https://en.wikipedia.org/wiki/Kriging](https://en.wikipedia.org/wiki/Kriging) 

Pros: 
1. Easy to implement 

Cons: 
1. Data not well distributed 
1. Algorithm uncertainty 


There are also advanced tools can be used to prepare climate data. 
ANUSPLIN 

[http://fennerschool.anu.edu.au/research/products/anusplin-vrsn-44](http://fennerschool.anu.edu.au/research/products/anusplin-vrsn-44) 
PRISM 
[http://www.prism.oregonstate.edu/](http://www.prism.oregonstate.edu/) 

Pros: 

1. Could potential on global scale 


<div>Cons:<div>1. Computational demand 
1. Hard to implement 
<div> 
Recently, Artificial Neural Network has also been used for spatial 
interpolation. But current tests show that ANN may not be as good as 
traditional approaches. 

Pros: 
1. Easy to use 

<div>Cons:<div>1. Uncertainty 
<div> 
<div>I want to highlight that our use of latitude/longitude in spatial 
resolution will cause issues in polar regions. This is because of the 
underlying mathematics definition of latitude/longitude. There are a few 
solutions to this issue but that is currently out of the scope in this post. I 
will provide some hint here that may be used to address this issue. 
[http://www.discreteglobalgrids.org/](http://www.discreteglobalgrids.org/) 

So what could potentially be the best choice? 
As for now, I see the potential in ANN since it is nonlinear and could 
potentially performance well compared with traditional approaches. 