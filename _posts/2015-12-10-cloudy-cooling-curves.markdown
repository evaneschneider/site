---
title:  "Cloudy cooling curves"
date:   2015-12-10
description: Details of various cooling curves
---

The following plots show cooling / heating curves generated with
Cloudy. Spefically, they are the result of modifying the
hazy_coolingcurve program to take into account the Haardt & Madau 
background.

The plot below shows the cooling and heating functions for solar metallicty
gas with three average densities: $$n_h = 0.1$$, $$n_h = 1$$, and $$n_h = 10$$. 
The default cloudy background is used, which includes the CMB and radio to x-ray
background (see Hazy). A galactic cosmic ray background is also included, as it 
dominates the chemistry of the molecular gas.
<img src="{{ site.url }}assets/images/coolingcurve_solar_CIE.png">

The following plot modifies the background described above. Instead of the default 
background, it uses the Haardt & Madau background (HM05). The CMB and cosmic rays 
are still included.
<img src="{{ site.url }}assets/images/coolingcurve_solar_PIE.png">

So, the question is - do we need to include cooling for gas below 
$$10^4$$ K? At low densities it won't be able to cool, so it is probably okay to 
neglect it (should I include a heating term at these densities?). 
At densities greater than $$n_h \approx 0.1$$ the gas is clearly still 
able to cool, but the efficiency has dropped by 2-3 orders of magnitude, so perhaps the 
cooling times are long enough that we can still safely ignore cooling in this regime?
