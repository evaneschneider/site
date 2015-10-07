---
title:  "PPM tests"
date:   2015-10-07 4:25:00
description: High mach number piecewise parabolic tests 
---

After the last post, I discovered a couple of bugs in the reconstruction 
techniques that were leading to very poor internal energy 
solutions on the square wave test. The results have improved considerably, 
but there is still some assymmetry, which is especially pronounced when using 
third order reconstruction (PPMP or PPMC). This post investigates the assymetries 
in the high mach number square wave test.

Figure 1: PPMP, exact solver, dual energy
<img src="{{ site.url }}assets/images/PPMP_exact_M800_de.png">

Figure 2: PPMC, exact solver, dual energy
<img src="{{ site.url }}assets/images/PPMC_exact_M800_de.png">

First of all, is the assymetry caused by another bug? To test this, I run the 
same tests, but with the velocity reversed:

Figure 3: PPMP, exact solver, dual energy, reversed velocity
<img src="{{ site.url }}assets/images/PPMP_exact_M800_de_reverse.png">

Figure 4: PPMC, exact solver, dual energy, reversed velocity
<img src="{{ site.url }}assets/images/PPMC_exact_M800_de_reverse.png">
