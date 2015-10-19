---
title:  "Spherical cloud in wind"
date:   2015-10-19 10:00:00
description: Evolution of a spherical cloud in a wind 
---

Since we have a version of dual energy that at least doesn't 
seem to produce wildly incorrect results, I am returning to 
the cloud/wind tests to see if it improves the results.

**Background**

These tests follow the intial conditions from the Cooper et al. 2009 
paper. A high density ($$n_{cl} = 91 \mathrm{cm}^{-3}$$) sphere is placed in pressure equilbrium 
with a hot, low density wind ($$n_{wind} = 0.1 \mathrm{cm}^{-3}$$, $$T = 5 \times 10^6 \mathrm{K}$$). 
The mach number of the wind is approximately 4.6 ($$v_{wind} = 1200 \mathrm{km/s}$$). The cloud is 
intitally at rest, and the evolutuion of the simulation follows the stages characteristic of a 
cloud/shock interaction: a forward shock is driven into the cloud, while another shock reflects back 
into the hot wind; the cloud flattens and compresses in the direction perpendicular to the flow, as 
another shock is driven into the back of the cloud; the forward shock intitally transmitted into the 
cloud reaches the back and the cloud begins to expand downstream of its inital position; the cloud 
fragments and is destroyed by hydrodynamical instabilities.

**The problem**

This test has proven difficult to run with Cholla, for reasons that I have not 
entirely pinned down. Reasons that I have looked into include:

1) *The failure of the CTU or Van Leer integrators as a result of the transverse flux update 
step.* I am unable to run this test in the adiabatic regime with either the CTU or VL integrator and 
any reconstruction technique. However, I can run the test if I leave out the transverse flux 
update step in CTU (i.e. just do normal PPM).

2) *The need for a dual energy update.* If I run this test with cooling, it breaks relatively 
quickly even without the transverse flux update. Negative pressures are produced after the final update 
step, and eventually the code crashes. With dual energy the situation is improved somewhat (see below), 
but still not fixed.

3) *Unstable cooling?* I may need a better way to incorporate the cooling. With dual energy, the 
crash occurs not as a result of negative densities or pressures after the final update, but because 
of a failure in the Riemann solver in a region of very low density behind the cloud. I have not spent 
much time on this yet.

**Current Results**

A movie of the sphere/wind test without cooling, with PPMP, the exact solver, and a simple
integrator can be found here: brown.as.arizona.edu/~evan/temp/sphere_wind_nocool.mov

A movie of the sphere/wind test as above but with cooling and dual energy (B14 switch) 
can be found here: brown.as.arizona.edu/~evan/temp/sphere_wind_wcool.mov

