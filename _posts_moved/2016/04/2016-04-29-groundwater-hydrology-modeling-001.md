---
 
title: 'Groundwater hydrology modeling: relation between steady state and transient
  simulation in MODFLOW simulation'
date: '2016-04-29T17:15:00.001-07:00'
permalink: /posts/2016/04/29/modflow-steady-state
author: Chang Liao
tags:
- MODFLOW
- Groundwater
modified_time: '2016-04-30T13:52:52.856-07:00'
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-8738608850004999002
blogger_orig_url: https://changliao.blogspot.com/2016/04/groundwater-hydrology-modeling-001.html
---

Standard groundwater modeling usually uses the three-dimensional Richard's 
equation to describe the groundwater flow. Solution to the Richard equation 
usually requires numerical methods such as finite-difference equation used in 
USGS MODFLOW. 
To solute the array of equations within MODFLOW, an initial head is required 
regardless of steady state (SS) or transient (TR) simulation. 
As the MODFLOW manual states that in a steady state simulation, the storage 
terms are ignored since storage of each grid cell is constant with time. 
One of the common problems to run the MODFLOW is  that we don't have the 
initial head data for the simulation. Therefore it is usually suggested that a 
SS simulation could be run at first to provide the head for the TR simulation. 
This is because SS is independent with initial head, but TR isn't. 
However, whether placing the SS simulation ahead of TR simulations is doubtful 
in many practices! Here are the explanations: 
First, the SS flow equation should only be simulated when the system is in 
equilibrium state.By definition, the steady state flow equation means for each 
grid cell, the flow and storage don't change with time. In most natural 
scenarios, these requirements are rarely met. However, the hydrologic system 
may be very close to equilibrium under certain circumstances. For instance, 
during winter time, the water flow is ignorable if most hydrologic processes 
are impaired due to the snow cover and frozen ground. 

Second. even if the hydrologic system is close to equilibrium, inappropriate 
settings for the SS simulation will produce unrealistic results. In order to 
achieve the steady state for each grid cell, numerical method solver will 
redistribute the water within the hydrologic system through the head 
redistribution. After the SS simulation, head distribution may be rather 
different compared with reality. Several aspects may account for the 
discrepancy: 1) source/sink terms including pumping, infiltration are not 
accurate enough; 2) boundary condition is not accurate or missing; 3) model 
structure, layer settings have flaws which can't match up the reality. 

Essentially, the head distribution at any given stress period is sufficient 
enough to start a simulation. However, approach to establish the head 
distribution remains the challenge. For cases started with SS, dedicated 
considerations of the above aspects may provide reliable results. Or else, 
reasonable assumption of initial head may yield even better results for TR 
simulation. 

On the other side, model calibration could provide an approach to further 
reduce the uncertainty in initial head distribution even though these related 
variable are not best described as parameters. 