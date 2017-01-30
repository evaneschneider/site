---
title:  "Modified Gresho Test"
date:   2017-01-30
description: A modified Gresho vortex test for 'gravity'
---

To test the 2D static potential in Cholla, I've created a modified version of the
Gresho vortex test that balances the centrifugal force created by the angular velocity
profile with an artificially added centripetal acceleration. The centripetal acceleration
is added in the same operator-split manner as the gravitational acceleration would be, 
so it is effectively a test of the 2D static potential in Cholla. This acceleration takes the 
form

<div style="text-align: center">
$$g_{x} = -\mathrm{cos}(\phi)v_{\phi}^2 / r \quad \mathrm{and} \quad g_{y} = -\mathrm{sin}(\phi)v_{\phi}^2 / r,$$
</div>

where $$\phi$$ is again the angle calculated according to $$\phi= \mathrm{arctan}(\frac{y}{x})$$ and $$r$$ is
the distance from the center of the vortex. This acceleration is applied in an operator-split manner at the end of
the hydro update, according to

$$(\rho v_{x})^{n+1} = (\rho v_{x})^{n*} + \Delta t \frac{g_{x}(\rho^n + \rho^{n+1})}{2},$$

$$(\rho v_{y})^{n+1} = (\rho v_{y})^{n*} + \Delta t \frac{g_{y}(\rho^n + \rho^{n+1})}{2},$$

$$(E)^{n+1} = (E)^{n*} + \Delta t \frac{g_{x}(\rho^{n} + \rho^{n+1})(v_{x}^{n} + v_{x}^{n*}) + g_{y}(\rho^{n} + \rho^{n+1})(v_{y}^{n} + v_{y}^{n*})}{4},$$

where $$n^{*}$$ refers to values that have been updated for the hydro step. There is no correction 
to the density.

**Results**

The problem is run until t = 3.0 on a 40x40 grid with periodic boundaries. I'm using PPMC, the exact 
Riemann solver, and CTU. I'm now centering the domain at (x, y) = (0, 0) so I can calulate $$\phi$$ using the 
atan2 function. The movies below show the evolution in azimuthal velocity, pressure, and voriticty. Unlike the 
previous versions of the test, the pressure is now set to be a constant function of radius.

<div style="text-align: center">
<video src="{{ site.url }}assets/movies/modified_gresho_line.mov" width="500" height="250" controls preload></video>

<video src="{{ site.url }}assets/movies/modified_gresho_image.mov" width="500" height="250" controls preload></video>
</div>

The pressure looks a little crazy, but note from the top movie that the overall order of perturbations is not large.

<br>

**L1 error**

The L1 density error at $$t = 3.0$$ is now 0.07% on the $$40\times40$$ grid.

