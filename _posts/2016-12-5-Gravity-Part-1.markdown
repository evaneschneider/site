---
title:  "Gravity (Part 1)"
date:   2016-12-5
description: Implementing Static Gravity in Cholla 
---

The time has come to implement a gravitational potential in *Cholla*.
To do this, I'll need to couple the gravitational source terms to the
momentum and energy equations:

$$ \mathbf{S}_m = \rho \nabla \phi $$ and $$ S_E = \rho \mathbf{v} \cdot \nabla \phi$$,
where $$\nabla \phi = \mathbf{g}$$ is the gradient of the gravitational 
potential (i.e. the gravitational acceleration).

To start, I've tried coupling the gravitational source terms
in the simplest way possible to the hydro equations, via an the operator-split
update at the end of the hydro step. This takes the form (in 1D):

<div style="text-align: center">
$$(\rho v)^{n+1}_{i} = (\rho v)^{n}_{i} + \frac{\Delta t}{2} g (\rho^{n}_{i} + \rho^{n+1}_{i})$$

$$(\rho E)^{n+1}_{i} = (\rho E)^{n}_{i} + \frac{\Delta t}{4} g (\rho^{n}_{i} + \rho^{n+1}_{i})(v^{n}_{i} + v^{n+1}_{i})$$.
</div>

To test this, I'll start with the simplest potential, a 
1D constant gravitational acceleration in the y-direction. 

Below is a test of a 2D Rayleigh-Taylor instability
with the following parameters: $$\rho_{upper} = 2.0$$, $$\rho_{lower} = 1.0$$,
$$g_{y} = 0.1$$, $$\gamma = 1.4$$. The two fluids are initally in
hydrostatic equilibrium, so the initial pressure, $$P = P_0 - \rho g y$$,
where $$P_0 = 1.0/\gamma + \frac{1}{2} \rho g$$ is set such that the
sound speed $$c_s = 1.0$$ at the interface. The inital velocities
are perturbed according to $$v_y = 0.01 cos(6\pi x) exp(-\frac{(y-0.5)^{2}}{0.1})$$, a
single mode perturbation that tapers off from the interface. The test is run in a
domain $$x = [0.0, \frac{1}{3}]$$, $$y = [0.0, 1.0]$$, with periodic x-boundaries and
reflecting y-boundaries. For this run, I used 200x400 cells.

Below is a movie showing the evolution of the fluid until $$t = 8.5$$. The color-scale 
represents the density from $$\rho = 1.0$$ to $$\rho = 2.0$$.

<div style="text-align: center">
<video src="{{ site.url }}assets/movies/rayleigh_taylor.mov" width="200" height="600" controls preload></video>
</div>

While the instability does develop, the overall evolution of the fluid is quite bouncy. This is
likely because the operator-split gravity update does not couple the hydro and gravity fluxes
closely enough to preserve hydrostatic equilibrium. As a result, the fluid oscillates about the initial 
equilibrium solution. We can see this clearly if we initialize the fluid without the velocity perturbations:

<div style="text-align: center">
<video src="{{ site.url }}assets/movies/bouncy_equilibrium.mov" width="200" height="600" controls preload></video>
</div>


