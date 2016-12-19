---
title:  "Gresho Test"
date:   2016-12-19
description: The Gresho vortex test with Cholla
---

The Gresho vortex test is a notoriously difficult problem for grid-based (and SPH) 
codes. A rotating vortex is initialized such that the centrifugal force is balanced 
by the pressure gradient:

<div style="text-align: center">
$$
\begin{equation}
u_{\phi}(r) = 
\begin{cases}
5r, & 0 < r < 0.2 \\
2 - 5r, & 0.2 < r < 0.4 \\
0, & 0.4 < r
\end{cases}
\end{equation}
</div>
