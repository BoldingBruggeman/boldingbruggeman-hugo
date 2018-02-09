+++
author = "Jorn Bruggeman and Karsten Bolding"
date = "2018-02-09T00:00:00+02:00"
description = ""
draft = false
image = "/portfolio/img/igotm.png"
showonlyimage = false
title = "iGOTM"
weight = 25

+++

A GOTM simulation for any point in the world with only 2 clicks.
Selecting a geographical position using Google Maps and clicking 'Simulate' will make an one year (2016) GOTM simulation with results presented in the browser.

Try it out [here](https://igotm.bolding-bruggeman.com).

<!--more-->

iGOTM is built around GOTM and a number of public datasets. After you pick a
location, the server retrieves the water depth (from ETOPO1), meteorological
conditions (ERA-Interim) and initial temperature/salinity profiles (World
Ocean Atlas). It then runs GOTM on our back-end servers to produce plots of
temperature, salinity and diffusivity. All typically within 10 seconds.

The aim of this service is to show case the capabilities and performance of
GOTM, the power of python-based tools for web interactivity, and not in the
least, our company's ability to build web services such as this. ;-)

Any two-click model comes with caveats. The main ones: (1) Regions strongly
influenced by horizontal transports will not be simulated correctly as iGOTM
lacks a mechanism to prescribe horizontal gradients or transports; this
typically affects salinity in regions near rivers (salinity will drift). (2)
Tides are currently not included, so tidally driven mixing and changes in
elevation are not accounted for. (3) Regions that are ice covered for part
of the year will not be simulated correctly as GOTM lacks an ice model
(instead of ice cover building up you'll typically see strong mixing).

iGOTM currently allows you to simulate one year only (2016). This is a
conscious decision to reduce the load on our servers. We will expand the
service in the future with the ability to perform longer simulations
(ideally the full ERA period, 1979-present) and to include biogeochemistry.
Given the computational cost of these features, they will be made available
as a paid, subscription-based service.

### The technical details ...

iGOTM uses [nginx](https://nginx.org/en/) as frontend webserver. Nginx reverse proxies simulation tasks to [tornado](http://www.tornadoweb.org/en/stable/) servers which are responsible for the actual GOTM simulation via a [python](http://www.python.org/) wrapper around the Fortran based GOTM executable. Plots (created with [matplotlib](https://matplotlib.org/)) are fed back to Nginx for presentation.

iGOTM uses a secure connection using [LetsEncrypt](https://letsencrypt.org/) issued certificates.

All plots use the [cmocean](https://matplotlib.org/cmocean/) color maps.

### Further information

Bug reports, questions, comments and suggestions are all welcome. Please
send these to igotm@bolding-bruggeman.com.

