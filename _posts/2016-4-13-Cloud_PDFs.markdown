---
title:  "Cloud PDFs"
date:   2016-4-13
description: A comparison of density PDFs for a turbulent cloud 
---

To create the initial conditions for the cloud-wind simulations, I need
to find a way of scaling the raw data from the Mach 5 isothermal turbulence
simulation data. Below are a png and pdf showing an excised region from the unscaled
data.

<img src="{{ site.url }}assets/images/cloud.png">
<img src="{{ site.url }}assets/images/cloud_PDF.png">

I'm only plotting and fitting to the cloud data (not the wind), and I've not tapered
the edge of the cloud, because I want to most clearly represent the underlying 
distribution. The fitting parameters are the mean and standard deviation for a
gaussian. As expected for isothermal turbulence, a log-normal distribution fits the
data well.

What happens if I just apply a linear scaling to the initial cloud density distribution?
Below is a PDF created by multiplying the original turbulence data by a constant factor
(in this case 0.27), in order to match the mean and initial mass of the $$n_h = 1$$ sphere
simulation.

<img src="{{ site.url }}assets/images/scaled_PDF.png">

The mean of the distribution has indeed shifted, but the width stays the same.
