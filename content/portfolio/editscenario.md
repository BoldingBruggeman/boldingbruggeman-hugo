+++
author = "Jorn Bruggeman"
date = "2017-05-31T13:58:54+02:00"
description = "EditScenarion generates Fortran namelist file(s) from xml formatted configuration files"
draft = false
image = "/portfolio/img/editscenario.png"
showonlyimage = false
title = "EditScenario"
weight = 40

+++

EditScenario is a 
[python](http://www.python.org) 
script used to generate and manipulate Fortran namelists - based on XML formatted configuration file.

<!--more-->

EditScenario.py can be operated in both a scriptable and GUI based way.

EditScenario requires a schema definition for the Fortran namelists to 
generate as well as a file with actual settings for a specific configuration. 
The use of XML as configuration language allows for a much richer experince 
compared to Fortran namelists including – in addition to variable values – 
human readable descriptions and variable units.

EditScenario is 
[downloadable](https://github.com/BoldingBruggeman/editscenario/releases) 
as a *wheel*-file and can be installed like this:

```script
pip install editscenario-0.11-py2-none-any.whl <--user>
```

<--user> if for per user installation - if omitted installation will be for all
users.

After installation the following can be used a a guide for use:

```script
editscenario -h
```

EditScenario comes with a close cousin - *nml2xml* converts an namelist-based
to a XML-based one so that *editscenario* can be used.

```script
nml2xml -h
```



