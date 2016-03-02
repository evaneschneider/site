---
title:  "HLLC solver"
date:   2016-3-2
description: Demonstration of the HLLC Riemann solver 
---

I wrote a new HLLC Riemann solver for Cholla. It is 
based on Toro's extension to the HLL solver that incoporates a contact wave (so
there are two intermediate states, instead of just one), and uses estimates for the
wave speeds described in Batten 1997. Advantages of this solver include the fact that
it does not require an iterative scheme to calculate the pressure (so is less expensive
than the exact solver), is positive definite (unlike a linearized solver), and is generally
less complicated than the Roe solver. Claims in the literature indicate that it is also 
highly robust and produces results that are competitive with an exact solver.

So, let's look at some tests. First the standard Sod shock tube, using PPMC.
Exact:
<img src="{{ site.url }}assets/images/sod_exact.png">
HLLC:
<img src="{{ site.url }}assets/images/sod_hllc.png">
Roe:
<img src="{{ site.url }}assets/images/sod_roe.png">

How about a strong shock?
Exact:
<img src="{{ site.url }}assets/images/strong_shock_exact.png">
HLLC:
<img src="{{ site.url }}assets/images/strong_shock_hllc.png">
Roe:
<img src="{{ site.url }}assets/images/strong_shock_roe.png">


Maybe a little worse on the internal energy, but I'd say they all handle that one okay, as well.
Now let's try an implosion test. Again using PPMC, also with
and without CTU.

Exact, early, without CTU (but with a CFL number = 0.1):
<img src="{{ site.url }}assets/images/implosion_early_exact.png">


Note - unlike the PPMP test, with PPMC at late times the implosion test looks
good, even without CTU. I'm looking into whether the problem was PPMP, the cfl number,
or the Riemann solver.

