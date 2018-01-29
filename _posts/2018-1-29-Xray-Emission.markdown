---
title:  "Xray Emission"
date:   2018-1-29
description: A first look at the soft x-ray emission from the outflow models
---

In an attempt to connect the outflow simulations I've been doing to observations, I've decided to try to model the x-ray emission from the hot plasma and compare it to what's seen in M82. I'll start with a simple model for the diffuse soft x-ray emission. Briefly, for a given cell in the simulation, I've got a density $$\rho$$, that I can convert to a number density, $$n$$, by assuming that the gas is ionized, so $$n = \rho / \mu m_p$$, where $$\mu = 0.6$$ and $$m_p$$ is the mass of a proton. Given this number density, I can also calculate a volume-averaged temperature for the gas in the cell, $$T = e (\gamma - 1.0) / n k_B$$, where $$e$$ is the internal energy density (tracked in the dual-energy version of Cholla), $$\gamma$$ is the adiabatic index (assumed to be 5/3), and $$k_B$$ is the Boltzmann constant. I can then calculate the total radiative luminosity from the cell via a cooling function $$\Lambda$$.

I'll start with the analytic cooling function that was used for these simulations, which is a fit to a CIE curve made with Cloudy assuming solar abundances. I can then create a surface brightness map for the soft X-rays by integrating $$n^2 \Lambda$$ along the line of sight for a given projection in my simulation. Only cells with temperatures in the soft X-ray band are included in the integration. I convert from temperature to energy by assuming $$E = \frac{3}{2} k_B T$$, as appropriate for a monatomic gas. The result for the $$512\times 512 \times 1024$$ adiabatic simulation at 60 Myr with central injection feedback looks like this:

<img src="{{ site.url }}assets/images/512_Xrays_60.png">

Clearly, the soft x-rays are highly collimated in this simulation. Interestingly, in this adiabatic simulation, the collimation is a result of the gas outside the cone actually being too hot to emit in the soft X-ray band. Interestlying, the total soft X-ray luminosity for the entire simulation volume is $$L_x = 2.9\times10^{40}$$, which is suprisingly close to the total oberserved luminosity. For example, Strickland et al. (2004) calculate an observed diffuse soft X-ray luminosity for M82 of $$L_x = 4.3\times10^{40}$$ (see their Table 9).

Here's the same map but for the 512-resolution clustered feedback simulation (which includes cooling), so is actually self-consistent:

<img src="{{ site.url }}assets/images/512_cluster_Xrays_60.png">

Here we see much less evidence for collimation. 

