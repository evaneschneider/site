---
title:  "Gresho Test"
date:   2016-12-19
description: The Gresho vortex test with Cholla
---

The Gresho vortex test is a notoriously difficult problem for grid-based (and SPH) 
codes. A rotating vortex is initialized such that the centrifugal force is balanced 
by the pressure gradient. The solution is time-independent. For these tests, I used
the initial conditions described in Liska & Wendroff (2003). As you can see from
the plot below, something still isn't right, because the vorticity is incorrect.

<div style="text-align: center">
<img src="{{ site.url }}assets/images/gresho_init.png">
</div>

I'm running the test until t = 3.0 on a 40x40 grid with transmissive boundaries, PPMC,
the exact solver, and CTU. It's improved, but the initial pressure doesn't seem to be
balancing the velocities, so perhaps I'm calculating the initial velocities wrong.

<div style="text-align: center">
<video src="{{ site.url }}assets/movies/gresho_line.mov" width="500" height="250" controls preload></video>
<video src="{{ site.url }}assets/movies/gresho_image.mov" width="500" height="250" controls preload></video>
</div>
