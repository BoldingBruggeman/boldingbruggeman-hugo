+++
author = "Jorn Bruggeman"
date = "2017-05-31T13:58:54+02:00"
description = "General Ocean Turbulence Model"
draft = false
image = "portfolio/img/gotm.png"
showonlyimage = false
title = "GOTM"
weight = 80

+++

The General Ocean Turbulence model is both a state-of-the-art turbulence 
library for flows in natural waters and a 1D water column model.

<!--more-->

GOTM was initiated by Hans Burchard and Karsten Bolding in 1998 and the first 
public release was in 1999. BB has always been responsible for maintaining 
the code – first using CVS and later using git. BB has provided numerous code 
contributions and has participated very active on the developers and users 
mailing lists.

The turbulence library of GOTM is used in a number of 3D ocean models - such as

GOTM is used as the primary test bed for Framework for Biogeochemical Models 
[FABM](portfolio/fabm/).

GOTM has its own [web-site](http://www.gotm.net) where in-depth information can be found.

Here we will just provide some information on new features BB is doing on the core 
GOTM code. This does not include utilities described elsewhere on this site - 
but only changes to the core part of the GOTM source code. This is typically 
new features that requires a significant knowledge of the entire code base - but
 also quite some resources in terms of implementation and testing time.

## Developments by BB

The table below describes the on-going GOTM developments at BB. As described 
[here](/business/) it is very difficult to get funding for pure model development.
On the other hand - to bring things forward - you can't wait for funding agencies 
to be ready.

BB has therefor initiated projects using BB resources - that hopefully someday can be 
released for general use - but it will require funds.

<!--
| Feature &emsp;&emsp;&emsp;&emsp;&emsp;&emsp; | Status&emsp | Price | 
| Feature | Status | Price |
-->

| Feature&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; | &emsp;&emsp;Status&emsp;&emsp;&emsp; | &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;Price (Euro) |
| ------------------------------------------- |:------------------------------------:| -----------------------:|
|[Hotstart](#hotstart)                        |     90 % - july 2017                 |  15.000,-               |
|[Assimilation](#assimilation)                |     50 % - july 2017                 |  75.000,-               |
|                                             |                                      |                         |

~~Jorn - shall we consider a html table here~~

----------------
### Hotstart

#### Rationale

Even though GOTM simulations typically executes quite fast there are use cases 
where dividing the simulation in parts do make sense. One example is when doing i
a coupled physical/bio-geochemical simulation. It is desirable to have the i
physical fields in balance before bio-geochemistry is switched on. A second example i
is when doing ensemble data-assimilation studies. Here starting the simulation i
from a analyzed state is mandatory.

#### Implementation details

The hotstart feature in GOTM is implemented on top if the *field_manager* utilising 
the possibility to add attributes to variables. For state variables – and other 
variables necessary to perform a hotstart – an extra attribute state is added during 
registration in the *field_manager*. The *output_manager* utilizes the state attribute 
information when creating a list of fields that must be either written to - or read 
from - the hotstart file. The link to the data in the NetCDF formatted hotstart file 
is done through the name variable in *the field_manager*. Having no hard-coded link 
between variables names in the model code and data in the hotstart file make a very 
flexible and extendable scheme. Bio-geochemical models not even implemented in FABM 
will work seamlessly during hotstart.

The use of the hotstart facility is controlled through two variables in the 
**gotm_run.nml** namelist. A boolean – **hotstart_offline** – and a variable to hold 
the name of the file with the hotstart data – **hotstart_file**. If hotstart_offline 
is true the time information in the time namelist must match the time information 
contained in hotstart_file.

#### Present status

The implementation is 90% finished and only some corner cases still needs to be 
addressed. The correctness of implementation has been tested in the following way:

-  A full simulation is done and the hotstart file is saved.
-  A new simulation is made identical to the original one – but including a hotstart time sometime during the simulation period. The hotstart file from the final part of the simulation is saved.
-  The two saved hotstart files are compared using the md5sum algorithm. If the sums are identical so are the hotstart files – and so are the simulations.

Below is shown the result from the Northern North Sea (nns_annual) standard 
test case. A hot-start has been injected at july 1st in the simulation year.

{{< figure src="/portfolio/img/hotstart_md5sum.png" >}}

----------------

### Assimilation
<!--
#### Rationale

#### Implementation details

#### Present status
-->
