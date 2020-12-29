---
 
title: 'Ecosystem modeling: a look up table for system state variables'
date: '2016-05-09T12:13:00.000-07:00'
permalink: /posts/2016/05/09/eco3d-lookup-table
author: Chang Liao
tags:
modified_time: '2018-04-03T12:23:09.924-07:00'
---

A list of variables has been established to describe the ecosystem system 
state. Specially, these variables are from different process-based algorithms. 

|       Module       |        Variable        |             Description             |
|:------------------:|:----------------------:|:-----------------------------------:|
| Radiation          | Shortwave              | Incoming shortwave radiation        |
|                    | PAR                    | Photosynthetically active radiation |
| Evapotranspiration | Potential ET           | Total potential evapotranspiration  |
| Interception       | canopy depth           | Depth of rain and snow in canopy    |
|                    | canopy ET              | ET from the canopy                  |
|                    | Net rain               | Net rain from canopy                |
|                    | Net snow               | Net snow from canopy                |
| Snow               | SCA                    | Snow cover area                     |
|                    | Snow albedo            | Snow albedo                         |
|                    | Snow ET                | Snow sublimation                    |
|                    | Snowmelt               |                                     |
|                    | SWE                    | Snowpack water equivalent           |
|                    | SWE temperature        | Temperature of the snowpack         |
| Infiltration       | Infiltration           |                                     |
| Surface runoff     | Surface runoff         |                                     |
|                    | Surface runoff upslope | Surface runoff from upslope         |
| Soil               | Dunnian runoff         |                                     |
|                    | Dunnian runoff upslope |                                     |
|                    | Interflow              |                                     |
|                    | Interflow upslope      |                                     |
|                    | Soil moisture          |                                     |
|                    | Soil to groundwater    |                                     |
| Groundwater        | Groundwater inflow     |                                     |
|                    | Groundwater outflow    |                                     |
|                    | Groundwater upslope    |                                     |