---
title:  "Moving Gresho Test"
date:   2016-12-29
description: The moving Gresho vortex test with Cholla
---

The moving Gresho vortex test is identical to the Gresho test describd in the 
previous post, except that the fluid is given a constant velocity boost
in the x-direction. Here, I apply a velocity boost of $$v_x = 1.0$$ and show
the results at $$t = 3.0$$, after the vortex has moved across the domain three
times. I'm using periodic boundaries and a $$40\times40$$ cell grid.

<div style="text-align: center">
<img src="{{ site.url }}assets/images/moving_gresho_final.png">

<video src="{{ site.url }}assets/movies/moving_gresho.mov" width="500" height="250" controls preload></video>
</div>

<br>

**L1 error**

The L1 errors at $$t = 3.0$$ are 0.9% for density and 167% for vorticity. I'm not sure why
the vorticity errors are so high in comparison to the ppm results in Liska & Wendroff,
but I think it may have to do with the accuracy of my vorticity calculation. Looking at the
initial conditions (shown in the previous post), the vorticity is already off from the exact solution by a lot. 
Given that the density errors are comparable to the results in LW03, I'd say this test looks about as good (bad)
as I'd expect.

