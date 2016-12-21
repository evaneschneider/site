---
title:  "Gresho Test"
date:   2016-12-19
description: The Gresho vortex test with Cholla
---

The Gresho vortex test is a notoriously difficult problem for grid-based (and SPH) 
codes. A rotating vortex is initialized such that the centrifugal force is balanced 
by the pressure gradient. The solution is time-independent. For these tests, I used
the initial conditions described in Liska & Wendroff (2003). 

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


The velocity in the gresho problem is specified in polar
coordinates, which I convert to Cartesian. Given 

<div style="text-align: center">
$$x = r \mathrm{cos}(\phi),   y = r \mathrm{sin}(\phi),$$
</div>

I get 

<div style="text-align: center">
$$v_{x} = v_{r}\mathrm{cos}\phi - v_{\phi} \mathrm{sin}(\phi),   
v_{y} = v_{r}\mathrm{sin}(\phi) + v_{\phi}\mathrm{cos}(\phi)$$
</div>

(where $$v_{\phi} = r \frac{d(\phi)}{dt}$$). Since $$v_{r} = 0$$,
that gives

<div style="text-align: center">
$$v_{x} = -\mathrm{cos}(\phi) v_{\phi},   v_{y} = \mathrm{cos}(\phi) v_{\phi}.$$
</div>

I calculate $$\phi$$ from $$x$$ and $$y$$ using $$\phi= \mathrm{arctan}(\frac{y}{x})$$ and 
$$r$$ using $$r^2 = x^2 + y^2$$.

In plotting the data, I have to convert the other direction, from $$v_{x}, v_{y}$$ to 
$$v_{\phi}$$. After a similar derivative analysis, I get 

<div style="text-align: center">
$$v_{\phi} = r \frac{x v_y - y v_x}{x^2 + y^2}$$.
</div>

How about the vorticity? Vorticity is the curl of the velocity field, so in 2D it's 

<div style="text-align: center">
$$\omega = \nabla \times v = (\frac{d(v_y)}{dx} - \frac{d(v_x)}{dy})\hat{z}$$.
</div>
