---
title: "An unstructured Voronoi mesh framework for large-scale hydrologic and land surface models"
collection: publications
permalink: /publication/mpas_mesh
excerpt: 'Accurate representation of river networks and land surface heterogeneity is crucial for improving the performance of continental-to-global hydrologic and land surface models (LSMs). Traditional approaches rely on either coarse-resolution grids, which may oversimplify complex terrain and limit the accurate representation of key processes, or computationally demanding full-domain high-resolution meshes. This study expands upon our previous research on unstructured mesh-based hydrologic modeling by introducing a novel framework for generating Hydrologic Refined Meshes (HRMs). This framework seamlessly integrates crucial land surface features, including river networks, watershed boundaries, and lake boundaries, into the mesh generation process. The HRM framework provides a generalized, feature-driven workflow for strategic mesh refinement; here, we implement it within the Model for Prediction Across Scales (MPAS) architecture, leveraging its Centroidal Voronoi Tessellations (CVT) properties and dual-grid topology. The resulting variable-resolution ($4\sim50\, \textrm{km}$) Voronoi mesh accurately captures these features, demonstrating significant advantages in representing land surface heterogeneity. For instance, the mesh effectively captures surface elevation, resolving most key landscape features despite using nearly half the cell count. River networks are accurately represented by high-resolution cells aligned along their courses, resulting in a conceptual network that deviates by only approximately $1.1 \, \textrm{km}$ on average from the true river network. We demonstrate the applicability of this framework and evaluate the generated mesh using several key variables, including surface elevation and river networks.'
date: 2026-10-13
year: 2026
venue:  'Journal of Advances in Modeling Earth Systems'
paperurl: 'http://changliao.github.io/files/2026/mpas_mesh2026.pdf'
citation: 'Liao, C., Darren Engwirda, Donghui Xu, Tian Zhou, Zeli Tan, L. Ruby Leung. An unstructured Voronoi mesh framework for large-scale hydrologic and land surface models. Journal of Advances in Modeling Earth Systems. [Accepted]'
---

Liao, C., Darren Engwirda, Donghui Xu, Tian Zhou, Zeli Tan, L. Ruby Leung. An unstructured Voronoi mesh framework for large-scale hydrologic and land surface models. Journal of Advances in Modeling Earth Systems. [Accepted]
