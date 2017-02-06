---
title:  "Keplerian Disk"
date:   2017-2-6
description: Evolution of a Keplerian gas disk
---

So we've seen how Cholla does with rotating flows in general, but how about the classic problem
of a disk in Keplerian rotation? Generally, there are two challenges in simulating such disks 
with a static grid code: first, the orbital speeds near the center of the disk can get arbitrarily large
as the resolution of the simualtion is increased, and second, the advection errors lead to artificial 
accretion through the disk.

To set up a rotating gas disk, I've followed the initial conditions from Krumholtz et al. (2004). There,
the potential is set by assuming a single solar mass at the center, with the velocities set by $$v^2 = GM/r$$.
The disk is assumed to be 10K and isothermal, with a radius $$r_{0} = 2\times10^15$$ cm and a power-law 
surface density profile $$\Sigma = \Sigma_{0}(r_{0}/r)$$, with $$\Sigma_{0} = 0.1$$ $$\mathrm{g}\mathrm{cm}^{-2}$$.
Because the disk is in Keplerian rotation, the surface density should not change with time. 


**Results**

The simulation is run for approximately 25 orbits of the cells at the smallest radius, 
or a single orbit at $$r = 1\times10^15$$ cm. I used a 128x128 grid with custom boundaries set to 
reproduce the correct velocites. I'm again using PPMC, an exact Riemann solver, and CTU.
The movies below show the evolution in the surface density profile and velocities as a function of 
radius, as well as a log-scale image of the surface density. For the radial plots, the exact solution
is plotted as a blue line, while red points show the simulation results. The point plotted on the surface density image
represents the inferred motion of a particle at that radius, and is merely there to guide the eye.

<div style="text-align: center">
<video src="{{ site.url }}assets/movies/r_sigma_128.mov" width="400" height="400" controls preload></video>
<video src="{{ site.url }}assets/movies/velocity_128.mov" width="400" height="400" controls preload></video>
<video src="{{ site.url }}assets/movies/sigma_128.mov" width="400" height="400" controls preload></video>
</div>

<br>

Clearly, Cholla has the most trouble at the center of the grid, as expected. The average L1 surface density and velocity errors
by the end of the simulation are about 1% and 0.06%, respectively, where I've normalized by the exact surface density
and velocity at each point. However, the errors for points near the center of the disk are much larger, as can be seen in the 
movies. When I increase the resolution by a factor of two, the simulation breaks. That said, as a test of the 2D potential, I'd say
this is pretty good (and since I'm not going to be simulating Keplerian disks, I don't think I need to investigate sink particles
or other fixes to these issues at this time).

