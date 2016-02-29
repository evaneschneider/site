---
title:  "Other Tests"
date:   2016-2-29
description: Hydro tests of different integration methods 
---

Running the PPMP-Roe integration scheme with a lower cfl number (0.25) does 
alleviate the cross-patterns in the 2D sphere-wind test. (Also see the KH tests
at the bottom of <a href="http://evaneschneider.github.io/site/2016/KH_test/">this
post</a>.

With the cfl number set to 0.4:
<img src="{{ site.url }}assets/images/circle_wind_cross_pattern.png">

With the cfl number set to 0.25:
<img src="{{ site.url }}assets/images/circle_wind_normal.png">


However, the implosion test at late times doesn't look great with this integration
scheme:
<img src="{{ site.url }}assets/images/PPMP_implosion_late.png">


The unsplit methods do much better with this test, but the predictor-corrector scheme (VL)
still doesn't preserve symmetry. (This is an old problem, and as far as I could tell
was not due to a bug, just something strange happening on the GPU).

<img src="{{ site.url }}assets/images/PPMP_VL_implosion_late.png">

That said, I *was* able to run a 2D cloud-wind test with the VL integrator (with dual energy
and the H correction), and the result looks far more symmetric than the PPM-only integration.
<img src="{{ site.url }}assets/images/circle_wind_PPMP_VL_hcorrect.png">


