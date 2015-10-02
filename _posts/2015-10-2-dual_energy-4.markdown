---
title:  "Dual Energy Tests (Part 4)"
date:   2015-10-02
description: Dissecting the internal energy update 
---

Here, I continue to use the high mach number square wave test from the 
previous post to try to figure out why the internal energy update is going 
wrong. At the end of the last post, I mentioned that the $Pdv$ term should always 
be 0 for the square wave test, because the velocity
should remain constant across cells. By the second timestep, this condition is
already violated. So, what happened in the first timestep to cause a velocity gradient?

As before, I use the Teyssier equation to update the internal energy:

$$
\frac{e^{n+1}_\mathrm{prim} - e^n}{\Delta t} = - \nabla \cdot \mathbf{F}(e)^n - P^n \nabla \cdot \mathbf{u}^n
$$

Note: $$e$$ in this equation is actually $$\rho e_{int}$$ in cholla notation. In practice, this equation
is represented in cholla as

$$
\rho^{n+1} e^{n+1} = \rho^n e^n + \frac{\Delta t}{\Delta x}(\bar{\rho}_{i-\frac{1}{2}}\bar{v}_{i-\frac{1}{2}}\bar{e}_{i-\frac{1}{2}} - \bar{\rho}_{i+\frac{1}{2}}\bar{v}_{i+\frac{1}{2}}\bar{e}_{i+\frac{1}{2}}) + \frac{\Delta t}{2 \Delta x} P^n (v^n_{i-1} - v^n_{i+1})
$$

Here, bars over a variable indicate that it is the sampled value from the Riemann solver. For $$\bar{e}$$ 
this just means an advected term. Because the flux term is density weighted, and the sampled velocities are equal,
*the flux terms should be identical*, and $$\rho e$$ should
remain constant across all cells.


This seems to be where the method is failing. In the first time step, the net flux is 0
across all cells *except the two at the density contacts.* Because the internal energy update 
is preferred over the total energy update using the Bryan switch, the total energy at the 
end of the first timestep reflects the slight perturbation. This gets translated to a slight 
perturbation in the pressure for the next timestep (since all the velocities remained equal at the 
end of the first timestep), and things spiral out of control from there.

So, is there a way to prevent the perturbation in $$\rho e_{int}$$, or is it endemic to the method, 
and a better solution is to prevent the switch from activating in this scenario? The Teyssier switch, 
for example, would never activate in the square wave test, no matter how fast the mach number.

Note: the same problem occurs using PPMC, so it's not an issue with contact steepening.

