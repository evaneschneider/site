---
title:  "Spherical cloud tests"
date:   2015-10-19 10:00:00
description: Evolution of a spherical cloud in a hot wind 
---

Since we have a version of dual energy that doesn't 
seem to produce wildly incorrect results, I am returning to 
the cloud/wind tests to see if it improves the results.

**Background**

These tests use the intial conditions from the Cooper et al. 2009 
paper. A high density ($$n_{cl} = 91$$ $$\mathrm{cm}^{-3}$$) sphere is placed in pressure equilbrium 
with a low density hot wind ($$n_{wind} = 0.1$$ $$\mathrm{cm}^{-3}$$, $$T_{wind} = 5 \times 10^6$$ $$\mathrm{K}$$). 
The mach number of the wind is approximately 4.6 ($$v_{wind} = 1200$$ $$\mathrm{km/s}$$). The cloud is 
initially at rest, and its evolutuion progreses through the stages characteristic of a 
cloud/shock interaction: a forward shock is driven into the cloud, while another shock reflects back 
into the hot wind; the cloud flattens and compresses in the direction perpendicular to the flow; 
the forward shock initially transmitted into the 
cloud reaches the back and the cloud begins to expand downstream of its inital position; the cloud 
fragments and is destroyed by hydrodynamical instabilities.

**The problem**

This test has proven difficult to run with Cholla, probably for a multitude of reasons. 
Problems that I have looked into include:

1) *The CTU and Van Leer integrators fail as a result of the transverse flux update 
step.* I am unable to run this test in the adiabatic regime with either the CTU or VL integrator,
regardless of the reconstruction technique or Riemann solver. However, I can run the test if I 
leave out the transverse flux update step in CTU (i.e. just do normal PPM). I don't currently 
have a fix for this.

2) *Dual energy may be needed for cooling.* If I run this test with cooling, the code produces negative
pressures relatively quickly even without the transverse flux update. Eventually the code crashes, but 
I'm not clear on whether the crash is caused by negative densities after the final update, or a 
failure of the Riemann solver in the lowest density regions. With the current implementation of dual energy 
the situation is improved somewhat, in the sense that the internal energy gets corrected to a positive 
number. However, the code still crashes, at around the same time it crashed without dual energy.

3) *Unstable cooling?* With dual energy, the crash occurs not as a result of negative densities or 
pressures after the final update, but because of a failure in the Riemann solver in a region 
of very low density behind the cloud. I have not spent much time on this yet, but it may be the 
primary problem.

**Current Results**

A movie of the sphere/wind test without cooling, with PPMP, the exact solver, and a simple
integrator can be found <a href="brown.as.arizona.edu/~evan/temp/sphere_wind_nocool.mov">here</a>.

A movie of the sphere/wind test as above but with cooling and dual energy (B14 switch) 
can be found <a href="brown.as.arizona.edu/~evan/temp/sphere_wind_wcool.mov">here</a>.

