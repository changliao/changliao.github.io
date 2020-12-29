---
layout: post
title: Hole and Boundary
date: '2018-05-21T17:00:00.000-07:00'
author: Chang Liao
tags:
- Boundary
- Spatial Discretization
modified_time: '2018-05-24T13:13:00.901-07:00'
blogger_id: tag:blogger.com,1999:blog-5219825485683920737.post-321035658140862055
blogger_orig_url: https://changliao.blogspot.com/2018/05/model-development-003.html
---

We sometimes do not understand well enough of what we are dealing with in our 
daily life. 
I was lucky enough to attend a seminar by Achille C. Varzi a few years ago, 
which inspired me on this topic: looking at hole and boundary from a different 
perspective. 

This post is a mixture of both philosophy and Earth Science (but which 
discipline isn't driven by philosophy anyway?) The topic of this post is about 
hole and boundary, which are very common objects in our daily life. 

By the definition from Wikipedia: A hole is a hollow place, an opening 
in/through a solid body, or an excavation in the ground. In another word, a 
hole exists because there is a closed **Boundary** between two different types 
of materials (often one of them is air). For example, a donut has a hole. 

Now the question is how should we define boundary, which is not an easy task 
if you look closer. 
For example, where is the boundary between a lake and its surrounding land? If 
you draw a polygon around the lake, you will soon realize that you cannot find 
a perfect location where the line should be. This is similar to the case you 
cannot find the right rule to measure the total length of the coastal line. 
The scale matters in these cases. 

We haven't touched time yet. As time passes on, the water level in a lake is 
very likely to change. 

There are many more interesting examples. Here are a few: 
1. When do we consider the food/drink is part of our body, the moment they 
enter into our mouth or they are actually digested? 
1. When do we call a baby is born? 
1. When do we call a person is dead? 
<div>The list goes on but I will now focus on the boundary in Earth 
Science.<div> 
<div>First, when we look at the map of any Earth image, there is a boundary 
because computer/photo must has one. But in fact the boundary of Earth is very 
unclear to us, the land surface? near surface atmosphere? outer space? This is 
critical because you have to consider these differences in different 
scenarios. For example, if you are to simulate or analyze the formation and 
impact of volcano eruption, you might have to consider deep geology features 
and all the way to the atmosphere. 

If you look "horizontally" (even though Earth is not flat), what boundary 
should we use? Land-Ocean-Sea Ice? They are changing constantly. On land, we 
are more familiar with political boundaries, the so called "nations" or 
"states", etc. These artificial boundaries are somewhat senseless in some 
cases. For example, the shape of states in USA and the boulder between USA and 
Canada. 

Then there is a problem, we cannot accurately simulate some processes without 
crossing boundaries. It is like we cannot estimate the stream discharge in 
Columbia River, WA, without knowing the snow conditions from Canada. Another 
example is the water data sharing between China and India (see 
[here](http://www.bbc.com/news/world-asia-41303082)). 

Recognizing the issues brought out by boundaries, we need to understand most 
of our Earth science activities do not have clear boundaries. This field 
itself is an interdisciplinary. As we are talking about scales, no matter in 
time or in spatial, there are lots of factors are involved. For example, if we 
are using watershed as a boundary for a land surface modeling, we have to 
consider whether the boundary applies to groundwater system. Also, the 
watershed delineation itself is DEM resolution dependent. So how can we 
justify the watershed is accurate enough for the application. 

Because linking different processes from different components implies a 
"mapping" process, we are basically mapping the boundaries. For example, a 
mapping from atmosphere to ocean suggests we need to make sure the boundaries 
have overlap. 

While not all mappings are perfect, there some approaches might be better than 
the others. I think a better understanding of boundary and how we should 
define boundary can help us to design a better Earth system modeling 
framework.<div> 


References: 

[https://plato.stanford.edu/entries/holes/](https://plato.stanford.edu/entries/holes/) 