+++
author = "Jorn Bruggeman"
date = "2017-05-31T13:58:54+02:00"
description = "Auto Calibration in PYthon"
draft = false
image = "portfolio/img/config_acpy.png"
showonlyimage = false
title = "ACPY"
weight = 50

+++

**ACPy** is an auto-calibration utility for 
[GOTM](http://www.gotm.net)
 and 
[fabm0d](http://www.fabm.net)
. **ACPy** is written in 
[Python](http://www.python.org).

<!--more-->

**ACPy** is configured via an xml formatted file. The example below is from the 
PROGNOS project, Lake Kinneret GOTM set-up. The configuration has optimized for
7 parameters in the model (the 8th is a dummy variable for testing). The y-axis
is the maximum likelihood value and  the x-axes show the span for
the different parameters. **ACPy** supports logaritmic parameters - as the 
upper right panel shows.

<!--
The configuration file consists of 
5 sections transports, executable, setup, parameters and observations.
-->

{{< figure src="/portfolio/img/acpy_example.png" >}}

-----

## License

A licensed version of **ACPy** can be obtained by contacting BB. The license 
fee is Euro 500,- for a personal license allowing the holder of the license to
run on any number of computers. The license file is **strictly** personal
and must under no circumstances be distributed to third parties.

The licensed version of **ACPy** will be provided as a _wheel_ file and must 
be installed on the computer(s) using the command:

```
pip install <name_of_wheel_file> <--upgrade> <--user>

<--upgrade> <--user> are optional.

<--upgrade> if ACPy is already installed on the system
<--user> if installation is not system wide
```

The licensed and non-licensed versions of **ACPy** will produce the same
results when run on the same configuration (except for difference inherent in
statistical methods where you draw random numbers from distributions).

So what is the difference - and why should I pay for a license:

1. The presence of a valid license-file will enable **ACPy** running in 
   parallel mode - both on shared memory computers (multiple cores) and
   distributed memory computers (clusters).
2. Further development of **ACPy** will 100% depend on additional funding.
3. Support will require a valid license-file.

The development of **ACPy** has been considerable work and started when Jorn 
Bruggeman worked in Oxford as a personal tool. Since then BB have added new 
features and made it much more generic and user friendly. 

The main advantage of a auto-calibration tool is time-saving (and hopefully 
better model simulations). So if time is of any value to you - consider 
buying a license - for the time we have saved you.

