---
layout: post
title: 'Ecosystem modeling: uncertainty quantification'
date: '2017-04-23T20:29:00.000-07:00'
author: Chang Liao
tags:
modified_time: '2018-04-03T12:18:36.976-07:00'
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-381685099575089801
blogger_orig_url: https://www.changliao.us/2017/04/ecosystem-modeling-007.html
---

I recently read a few news articles of skeptical attitudes towards climate 
change, and I decided to write something about it. I am not trying to promote 
climate change, but instead I want to point out there is great uncertainty in 
our current Earth system modeling. 

Uncertainty quantification (UQ) is an important step in most numerical 
simulation processes. In general, a simulation without uncertainty 
quantification is less convincing. (I was surprised that an invited speaker in 
department seminar said he doesn't care about uncertainty.) 

However, how to conduct uncertainty quantification itself is a challenge, 
especially for highly nonlinear ecosystem modeling. 

First, I will invite you to read the Wikipedia UQ here: 

[https://en.wikipedia.org/wiki/Uncertainty_quantification](https://en.wikipedia.org/wiki/Uncertainty_quantification) 
which serves as an overview of the concept I will discuss below. 

Uncertainty comes from lots of sources and nearly every step we take in our 
Earth system modeling has uncertainty. We, scientists as well as engineers 
spent great efforts to reduce the uncertainty. That is why climate modelers 
always try to improving our estimates year by year. As a result. you may read 
papers like "something is potentially underestimated previously". (That is 
also why you see 7-day weather broadcasting is always changing.) 

We don't know what we don't know. That is why we may never be able to consider 
everything, which is reasonable for scientific research. Decades ago, we 
didn't consider well the groundwater and surface water interactions in most 
hydrology modeling. Today, we still do NOT always consider! 

Another big issue in Earth system modeling is that we are generally reluctant 
to spend too much efforts in UQ. Peer reviewers are not always interested in 
your UQ. However, they must be interested in your scientific questions and 
results. In an environment that publication is the major measure of your 
academic accomplishments, the quality of science is likely weakened. 

Unlike experimental science, Earth system modeling is very much like a black 
box. Indeed you can see the source code of the model, but you can seldom 
reproduce the whole research since there are lots of pre-processes and 
post-processes involved but yet unveiled. 

Assumptions. We made too many assumptions. There are many reasons we have to. 
One of the reason is the computational demand. 

We always want more data. But the reason we need to simulate is we don't have 
enough data and there is also some data cannot be measured directly. Even we 
measured data, they are not true values in most cases. 

If you look at the climate change prediction again, you can tell where the 
uncertainty comes from better. 

1. We don't have high quality input data; 
1. We made assumptions in lots of processes; 
1. We ignored lots of processes; 
1. We don't know lots of processes we don't know yet; 
1. We made mistakes or even misconducts. 

However, that is also why we are working hard to reduce the uncertainty.  A 
few years back, the weather broadcast was as good as today's? I doubt. 