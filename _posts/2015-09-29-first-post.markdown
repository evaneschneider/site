---
title:  "Dual Energy Tests"
date:   2015-09-29 12:25:00
description: Experimenting with different dual energy formulations 
---

**Relevant equations:**

From Teyssier 2015, the nonconservative internal energy update (Equation 161): 

<span>
$$
\frac{e^{n+1}_{\mathrm{prim}} - e^n}{\Delta t} = - \nabla \cdot \mathbf{F}(e)^n - P^n \nabla \cdot \mathbf{u}^n
$$
</span>

From Bryan et al. 2014, the nonconservative internal energy update (Equation 43):

<span>
$$
\rho^{n+1}_j e^{n+1}_j = \rho^n_j e^n_j + \frac{\Delta t}{\Delta x_j} (\bar{\rho}_{j + \frac{1}{2}} \bar{v}_{j + \frac{1}{2}} \bar{e}_{j + \frac{1}{2}} - \bar{\rho}_{j - \frac{1}{2}} \bar{v}_{j - \frac{1}{2}} \bar{e}_{j - \frac{1}{2}}) - \frac{\Delta t}{\Delta x_j} p^n_j (\bar{v}_{j + \frac{1}{2}} - \bar{v}_{j - \frac{1}{2}})
$$
</span>


**The tests**

Using a shock tube test with periodic boundaries, to allow for high mach number bulk flow.

<span>
$$
\rho_L = 1.0,\quad v_L = 0.0,\quad p_L = 1.0 \\
\rho_R = 0.2,\quad v_R = 0.0,\quad p_R = 0.01 \\
\gamma = 1.4
$$
</span>

For the high mach number test, $$ v_L = v_R = 120 $$.


**Without Dual Energy**

Figure 1: PPMP, exact Riemann solver, CTU
<img src="{{ site.url }}assets/images/PPMP_exact.png">

Figure 2: same as Figure 1, but with bulk velocity <span> $$ v_{bulk} = 100 c_s $$ </span>
<img src="{{ site.url }}assets/images/PPMP_exact_M100.png">
