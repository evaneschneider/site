---
title:  "Gresho Test"
date:   2016-12-19
description: The Gresho vortex test with Cholla
---

The Gresho vortex test is a notoriously difficult problem for grid-based (and SPH) 
codes. A rotating vortex is initialized such that the centrifugal force is balanced 
by the pressure gradient. The solution is time-independent. For these tests, I use
the initial conditions described in Liska & Wendroff (2003).

<div style="text-align: center">
<img src="{{ site.url }}assets/images/gresho_init.png">
</div>

I'm running the test until t = 3.0 on a 40x40 grid with transmissive boundaries. PPMC,
exact solver, CTU. Things don't look so good. At the moment I'm not sure whether the 
problem is the initial conditions, the boundaries, or the hydro integrator, but if the
L1 errors in LW03 really are listed in percentages, then my densitiy error is
over two orders of magnitude worse than the one they get for PPM, which doesn't seem
right.

<div style="text-align: center">
<video src="{{ site.url }}assets/movies/gresho_line.mov" width="600" height="300" controls preload></video>
<video src="{{ site.url }}assets/movies/gresho_image.mov" width="600" height="300" controls preload></video>
</div>
