---
title:  "Sphere wind tests"
date:   2015-11-02
description: Comparison of two sphere wind results 
---

Below are two images from the sphere-wind test with cooling and dual energy. The image on the left uses
1/2 CTU, the Roe solver, and PPMP, while the image on the right uses 1/2 CTU, the Roe solver, and PLMC.

<img style="float: left; width: 48%; margin-right: 1%; margin-bottom: 0.5em;" src="{{ site.url }}assets/images/cloud_roe_ppmp.png">
<img style="float: left; width: 48%; margin-right: 1%; margin-bottom: 0.5em;" src="{{ site.url }}assets/images/cloud_roe_plmc.png">

There seems to be more assymetry in the left image. Additionally, the PPMP reconstruction seems to be 
inhibiting the Kelvin-Helmholtz instabilities.
