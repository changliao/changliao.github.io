---
title: 'Model calibration with alternative options'
date: 2020-09-29
permalink: /posts/2009/09/model-calibration-with-alternative-options/
tags:
  - Model calibration
  - Optimization
  - PyPEST
---
PyPEST is a project that I worked on a little bit last year. I attempted to make PEST available to Python developers so model calibration can be easy and efficient.

So far PyPEST supports MACES, SWAT, MODFLOW, PRMS, etc. There is still much work needed for testing.

MACES has a structure much like SUMMA (https://summa.readthedocs.io/en/latest/configuration/SUMMA_configuration/).

During run time, the model may use different algorithms for a single process. As a results, the model may have many different configurations in applications.

The question is then how we can calibrate a model with alternative options. Shall we treat each option as a parameter or not? Mathematically, we can certainly do so with some tweak because anything can be considered parameter internally. In this way, we may easily pick out the best configuration. There are drawbacks as well. For example, when we treat option as parameter, the commonly used gradient search and sensitivity analysis will be affected. Also, adding them will increase computational demand.

A more realistic strategy is that we can calibrate classified by configuration. This will increase the complexity of file system but decrease the complexity of parameter control.

We can then find out the best configuration using another global search. This will also enable us to compare the performance between configurations.