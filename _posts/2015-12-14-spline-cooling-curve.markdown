---
title:  "Spline cooling curves"
date:   2015-12-14
description: GSL spline from Cloudy cooling curve
---

Once a cooling curve has been generated with Cloudy, we need to use
an interpolation to create a cooling function in Cholla. The plot below
shows the result of an interpolation done using the GSL cubic spline function.
The cooling curve was generated with Cloudy and assumes solar metallicity gas, 
the Haardt & Madau '05 background + CMB, and $$n_h = 1$$.

<img src="{{ site.url }}assets/images/spline_coolingcurve.png">


