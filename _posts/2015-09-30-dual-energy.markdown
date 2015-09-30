---
title:  "Dual Energy Tests (Part 2)"
date:   2015-09-30 12:25:00
description: Testing the Enzo dual energy switch 
---

This post focuses on when the dual energy formalism should have an effect. From Bryan et al., 2014 (hereafter B14):
"It should be stressed that as long as the parameter $$\eta_1$$ is small enough the dual energy method
_will have no dynamical effect_.

Here, $$eta_1$$ refers to the ratio that determines whether a given cell updates its internal energy
using the conservative update vs. the non-conservative update. 
As given in B14, Equation 44:

$$
p =
\begin{cases}
\rho(\gamma - 1)(E - \mathbf{v}^2 / 2), (E - \mathbf{v}^2 / 2)/E > \eta_1, \\
\rho(\gamma - 1)e, (E - \mathbf{v}^2 / 2)/E < \eta_1. \\
\end{cases}
$$

For the following tests, we use the Teyssier 2015 (T15) nonconservative update (Equation 161): 

$$
\frac{e^{n+1}_\mathrm{prim} - e^n}{\Delta t} = - \nabla \cdot \mathbf{F}(e)^n - P^n \nabla \cdot \mathbf{u}^n
$$

We first investigate whether the statement above regarding dynamical impact is true for Cholla.

**The tests**

The tests shown below consist of a shock tube with periodic boundaries, 
to allow for high mach number bulk flow.

$$
\rho_L = 1.0,\quad v_L = 0.0,\quad p_L = 1.0 \\
\rho_R = 0.2,\quad v_R = 0.0,\quad p_R = 0.01 \\
\gamma = 1.4
$$

For the high mach number test, $$ v_L = v_R = 120 $$.


**Without Dual Energy**

Figure 1: PPMP, exact solver, no dual energy, $$ v_{bulk} = 100 c_s $$
<img src="{{ site.url }}assets/images/PPMP_exact_M100.png">

**With Dual Energy**

Figure 2: Same as figure one but with dual energy, $$eta_1 = 10^{-6}$$
<img src="{{ site.url }}assets/images/PPMP_exact_M100_tinyeta.png">

As expected, the dual energy formalism has no effect in this case. Practically speaking,
this is because the internal energy for each cell is reset to the conservatively calculated 
value at every timestep, NOT because the hydro update is working with a non-conservatively 
calculated internal energy.


