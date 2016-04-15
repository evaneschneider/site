---
title:  "Mass Evolution, Part 2"
date:   2016-4-15
description: Further exploration of mass evolution 
---

This post adresses two questions:

* Are the simulations converged for mass evolution?
* How does the initial density contrast affect the mass evolution?

I attempt to answer the first question with the following plot, which shows the mass
evolution as a function of cloud crushing time for the $$n_h = 1$$ sphere simulation
at 3 different resolutions: 16, 32, and 64 cells / $$R_{cl}$$. The mass fraction is calculated
as the amount of material above a given density threshold (in this case $$n = 0.05 cm^{-3}$$
as compared to the intial mass of the cloud.

<img src="{{ site.url }}assets/images/041516_swn1_mass.png">

From this plot, I don't know if we're converged. It's maybe worth noting that Scannapieco's 
convergence tests measured "mix fractions" not mass fractions, which may make a difference
in a convergence study.

I can make the same plot using different density thresholds to measure the cloud mass,
<img src="{{ site.url }}assets/images/041516_swn1_mass_thresholds.png">
but that doesn't change the convergence much. In the plot above, the solid line represents a 
threshold of 1/20 the initial cloud density, while the dotted and dot-dash lines represent
1/10 and 1/3, respectively.

To address the second question, I plot below the mass evolution for simulations with different
intial density contrasts.

<img src="{{ site.url }}assets/images/041516_sphere_mass.png">

As expected, the evolution of the $$n_h = 0.2$$ sphere falls between the $$n_h = 0.1$$ and 
$$n_h = 1.0$$ cases. Watching a movie of the simulation 
(<a href="http://brown.as.arizona.edu/~evan/temp/swn02_lowres.mov">here</a>), we see that the $$n_h = 0.2$$
cloud cools more effectively than the $$n_h = 0.1$$ cloud, but it loses significantly more
of its initial mass than the $$n_h =0.5$$ case. To me, it looks like about half the cloud follows
the adiabatic track, as indicated by the initial steep dropoff a $$t \sim 5 t_{cc}$$, and the
other half gets dense enough to cool and follow the radiative track.


