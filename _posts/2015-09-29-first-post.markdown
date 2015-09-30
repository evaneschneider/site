---
title:  "Dual Energy Tests"
date:   2015-09-29 12:25:00
description: Experimenting with different dual energy formulations 
---

Relevant equations:

From Teyssier 2015, Equation 161
$$
\frac{e^{n+1}_{prim} - e^n}{\Delta t} = - \nabla \cdot F(e)^n - P^n \nabla \cdot u^n
$$

Using a shock tube test with periodic boundaries, to allow for high mach number bulk flow.

<span>
$$ \rho_L = 1.0, v_L = 0.0, p_L = 1.0 $$
$$ \rho_R = 0.2, v_R = 0.0, p_R = 0.01 $$
$$ \gamma = 1.4 $$
</span>

For the high mach number test, $$ v_L = v_R = 120 $$.


**Without Dual Energy**

Figure 1: PPMP, exact Riemann solver, CTU
<img src="{{ site.url }}assets/images/PPMP_exact.png">

Figure 2: same as Figure 1, but with bulk velocity <span> $$ v_{bulk} = 100 c_s $$ </span>
<img src="{{ site.url }}assets/images/PPMP_exact_M100.png">
