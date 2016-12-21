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

Let's check the math. The velocity in the gresho problem is specified in polar
coordinates, which I need to convert to Cartesian. Given $$x = r \mathrm{cos}\theta$$, 
$$y = r \mathrm{sin}\theta$$, I get $$v_{x} = v_{r}\mathrm{cos}\theta - r v_{\theta} \mathrm{sin}\theta$$, 
$$v_{y} = v_{r}\mathrm{sin}\theta + r v_{\theta}\mathrm{cos}\theta$$. Given that $$v_{r} = 0$$,
that gives $$v_{x} = -r \mathrm{cos}\theta v_{\theta}$$ and $$v_{y} = r \mathrm{cos}\theta v_{\theta}$$.
I calculate $$\theta$$ from $$x$$ and $$y$$ using $$\theta = \mathrm{arctan}(y/x)$$.

I'm running the test until t = 3.0 on a 40x40 grid with transmissive boundaries, PPMC,
the exact solver, and CTU. It's improved, but the initial pressure doesn't seem to be
balancing the velocities, so perhaps I'm calculating the initial velocities wrong.

<div style="text-align: center">
<video src="{{ site.url }}assets/movies/gresho_line.mov" width="500" height="250" controls preload></video>
<video src="{{ site.url }}assets/movies/gresho_image.mov" width="500" height="250" controls preload></video>
</div>
