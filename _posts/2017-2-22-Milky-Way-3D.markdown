---
title:  "Milky Way 3D"
date:   2017-2-22
description: Generating the ICs for a 3D gas disk 
---

Once we add a third dimension, the initial conditions for an isothermal disk get a bit more complex.
In addition to balancing the radial components of the gravitational potential with circular velocity, 
I now need to balance the vertical acceleration via a pressure gradient, i.e. I need to make sure the 
disk is in hydrostatic balance. Given that the pressure and density can be related for an isothermal 
gas via the expression $$P = \rho c_{s}^{2}$$, this translates to calculating the vertical density profile 
at each radial location in the disk.

**The gravitational potential**

The static potential for the disk will once again be based on the Milky Way. Because it is spherically 
symmetric, the NFW halo can thus be expressed in exactly the same way as the 2D case, but for reasons that 
will become clear momentarily, I will express it in cylindrical coordinates, $$(r, z)$$:

$$\Phi(r, z)_{h} = - \frac{G M_{halo}}{\sqrt{r^2 + z^2}f(c_{vir})}\mathrm{ln}(1+\frac{\sqrt{r^2 + z^2}}{r_h}).$$

Again, $$f(y) = \mathrm{ln}(1+y) - \frac{y}{1+y}$$, $$x = \sqrt(r^2 + z^2) / r_{h}$$, and  $$r{_h}$$ is the halo scale 
length (see previous post for variable values).

The potential of the disk now has a vertical component, and becomes a Miyamoto-Nagai profile:

$$\Phi(r, z)_{d} = - \frac{G M_{d}}{\sqrt{r^2 + (r_{d} + \sqrt{z^{2} + z_{d}^{2}})^2}},$$

where $$r_{d} = 3.5$$ kpc is the disk scale length and $$z_{d} = 0.2 r_{d}$$ is the disk scale height. From
these potentials, I can calculate the radial acceleration and associated circular velocity at every value 
of $$z$$, exactly as I did in the 2D case, as well as the vertical acceleration, $$g_{z}$$, at any 
point in $$r$$.


**Hydrostatic Equilibrium**

The potential described above gives the circular motion of the gas in the disk. For the 
disk surface density profile, I will again use an exponential in the radial direction:

$$\Sigma(r) = \frac{M_{g}}{2\pi r_{g}^2} e^{-\frac{r}{r_{s}}},$$

where $$r_{g}$$ is the gas disk scale length. I thus have the boundary conditions required in order to 
calculate the vertical density profile at each location in radius, as follows. I start with the equation 
for hydrostatic equilibrium in the vertical direction,

$$\frac{\mathrm{d}P}{\mathrm{d}z} = -\rho g_{z},$$

where $$g_{z}$$ is the vertical acceleration due to the combined halo+disk potential 
($$\frac{\mathrm{d}\Phi}{\mathrm{d}z}$$). Given $$P = \rho c_{s}^{2}$$, I can solve 
for $$\rho(z)$$, the density profile as a function of $$z$$, at a given $$r$$. First, 
I substitue in $$\rho$$ for $$P$$,

$$\frac{\mathrm{d}\rho}{\mathrm{d}z} = -\frac{\rho g_{z}}{c_{s}^2}.$$

Then, I rearrange and integrate both sides:

$$\frac{\mathrm{d}\rho}{\rho} = -\frac{g_{z}}{c_{s}^2}\mathrm{d}z ,$$

$$\mathrm{ln}(\rho) + A = \frac{\Phi}{c_{s}^2} + C,$$

where I have substituted $$\Phi$$ for the integral of $$g_{z}\mathrm{d}z$$. Exponentiating and 
rewriting the constant of integration, I get

$$\rho = B e^{(\frac{\Phi}{c_{s}^2}+C)}.$$

To solve for the constants, we need boundary conditions. We can set $$B$$ by saying that 
$$\rho = \rho_{0}$$ when $$z = 0$$, where $$\rho_{0}$$ is the central density at a given $$r$$. Then we have

$$\rho = \rho_{0} e^{(\frac{\Phi}}{c_{s}^2} - \frac{\Phi_0}{c_{s}^2})},$$

where $$\Phi_{0}$$ is just the value of $$\Phi$$ evaluated at $$z = 0$$. To solve for $$\rho_0$$, we apply 
the constraint that the integral of the density profile over $$z$$ must equal the surface density, 

$$\Sigma = \int_{0}^{\infty} \rho_{0} e^{(\frac{\Phi_{0}}{c_{s}^2} - \frac{\Phi}{c_{s}^2})} \mathrm{d}z.$$

Generally, this integral will need to be evaluated numerically.
