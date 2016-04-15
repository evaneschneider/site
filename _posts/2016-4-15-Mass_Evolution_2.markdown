---
title:  "Mass Evolution, Part 2"
date:   2016-4-15
description: Further exploration of mass evolution 
---

This post adresses two questions:
**Are the simulations converged for mass evolution?
**How does the initial density contrast affect the mass evolution?

I attempt to answer the first question with the following plot, which shows the mass
evolution as a function of cloud crushing time for the $$n_h = 1$$ sphere simulation
at 3 different resolutions: 16, 32, and 64 cells / $$R_{cl}$$. The mass fraction is calculated
as the amount of material above a given density threshold (in this case $$n = 0.05 cm^{-3}$$
as compared to the intial mass of the cloud.

<img src="{{ site.url }}assets/images/041516_swn1_mass.png">

From this plot, I don't know if we're converged. It's maybe worth noting that Scannapieco's 
convergence tests measured "mix fractions" not mass fractions, which may make a difference
in a convergence study.

I can make the same plot with different density thresholds,
<img src="{{ site.url }}assets/images/041516_swn1_mass_thresholds.png">
but that doesn't change the convergence much.

To address the second question, I plot below the mass evolution for simulations with different
intial density contrasts.

<img src="{{ site.url }}assets/images/041516_sphere_mass.png">


