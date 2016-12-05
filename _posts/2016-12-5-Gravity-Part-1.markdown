---
title:  "Gravity (Part 1)"
date:   2016-12-5
description: Implementing Static Gravity in Cholla 
---

The time has come to implement a gravitational potential in **Cholla**.
To do this, I'll need to couple the gravitational source terms to the
momentum and energy equations:

$$ S_m = \rho \nabla \phi $$ and $$ S_E = \rho \mathbf{v} \dot \nabla \phi$$,
where $$\grad \dot \phi = \mathbf{g}$$ is the gradient of the gravitational 
potential (i.e. the gravitational acceleration).

To start, I've tried coupling the gravitational source terms
in the simplest way possible to the hydro equations, via an the operator-split
update at the end of the hydro step. This takes the form:



I'll start with a simple, 1D constant gravitational acceleration in
y-direction. Below is a test of a 2D Rayleigh-Taylor instability
with the following parameters: $$\rho_{upper} = 2.0$$, $$\rho_{lower} = 1.0$$,
$$\mathbf{g}_{y} = 0.1$$, $$\gamma = 1.4$$. The two fluids are initally in
hydrostatic equilibrium, so the initial pressure $$P = P_0 - \rho*g*y$$,
where $$P_0 = 1.0/\gamma + \frac{1}{2} \rho_{lower} * g$$ is set such that the
sound speed in the lower fluid is 1.0 at the interface. The inital velocities
are perturbed according to $$v_y = 0.01*cos(6\pi*x)*exp(-(y-0.5)^{2}/0.1)$$, a
single mode perturbation that tapers off from the interface.

Below is a movie showing the evolution of the fluid until $$t = 8.5$$.

<video src="{{ site.url }}assets/movies/rayleigh_taylor.mov" width="200" height="600" controls preload></video>
