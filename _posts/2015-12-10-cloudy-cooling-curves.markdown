---
title:  "Cloudy cooling curves"
date:   2015-12-10
description: Details of various cooling curves
---

The following plot shows three cooling / heating curves generated with
Cloudy. Spefically, they are the result of modifying the
hazy_coolingcurve program to take into account the Haardt & Madauu 
background.

The plot below shows the cooling and heating functions for solar metallicty
gas with three average densities: $$n_h = 0.1$$, $$n_h = 1$$, and $$n_h = 10$$. 
The default cloudy background is used, which includes the CMB and radio to x-ray
background (see Hazy). A galactic cosmic ray background is also included, as it 
dominates the chemistry of the molecular gas.
<img src="{{ site.url }}assets/images/coolingcurve_solar_CIE.png">

The following plot modifies the background described above. Instead of the default 
background, it uses the Haardt & Madauu background (HM05). The CMB and cosmic rays 
are still included.
