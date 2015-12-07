---
title:  "Cloud density evolution"
date:   2015-12-07
description: Density evolution of a turbulent cloud 
---

The following images and plot are products from a cloud-wind simulation with the following parameters:

- Resolution: 1024x384x384
- Size: 80x30x30 pc
- Wind density: $$n_{wind} = 0.1 \, \mathrm{cm}^{-3}$$
- Wind temperature: $$T_{wind} = 5 \times 10^6 \, \mathrm{K}$$
- Wind velocity: $$v_{wind} = 1200 \, \mathrm{km} \, \mathrm{s}^{-1}$$
- Average cloud density: $$n_{cloud} \approx 75 \, \mathrm{cm}^{-3}$$
- Cloud radius: 5 pc
- Cloud mass: $$\approx 800 \, \mathrm{M}_{\odot}$$

All material with a number density higher than $$n = 1.0$$ is considered part of the cloud.

The following four snapshots show the evolution of the cloud over the first 400,000 years 
of the simulation. Snapshots are spaced 100,000 years apart.

<img src="{{ site.url }}assets/images/cloud_wind_0000.png">
<img src="{{ site.url }}assets/images/cloud_wind_0050.png">
<img src="{{ site.url }}assets/images/cloud_wind_0100.png">
<img src="{{ site.url }}assets/images/cloud_wind_0150.png">
<img src="{{ site.url }}assets/images/cloud_wind_0200.png">

Below is a density pdf showing all the material in the simulation. Lines correspond to the 
five snapshots above, with the color gradient going from darkest (snapshot 0) to lightest 
(snapshot 400k).

<img src="{{ site.url }}assets/images/cloud_wind_density.png">
