---
title:  "Gresho Test"
date:   2016-12-19
description: The Gresho vortex test with Cholla
---

The Gresho vortex test is a notoriously difficult problem for grid-based (and SPH) 
codes. A rotating vortex is initialized such that the centrifugal force is balanced 
by the pressure gradient. The solution is time-independent. For these tests, I use
the initial conditions described in Liska & Wendroff (2003).

<div style="text-align: center">
<img src="{{ site.url }}assets/images/gresho_init.png">
</div>
