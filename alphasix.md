Work has started on a 6.0 version of the C64 core. A release is planned for late 2026 or early 2027. This page gives you an overview on new features as well as download links for **untested** Alpha versions.

## Download location
The current Alpha 1 version can only be downloaded in the Discord Channel:

https://discord.com/channels/719326990221574164/794775503818588200/1472615052065505464

## IDE64 Support
The IDE64 cartridge is supported by the current Alpha version of the Core. There is no IDE64-simulation, you need an actual interface cartridge. This is still experimental - we need data whether this fully works from users.

## RTC disable
The current release of the 5.2 core emulates a Real Time Clock connected to the C64 tape port, mainly to run with GEOS. Unfortunately a very limited number of programs will crash when this clock is active. The current 6.0 Alpha turns the clock off again, so these programs will run, but you will lose the RTC functionality. Later versions will make the clock switchable in the User Interface.

More details about the RTC can be found [here.](https://github.com/MJoergen/C64MEGA65/blob/master/doc/RTC.md)

## Other features planned
To see a list of features that are planned, please check out the list of issues labeled "V6" in the Github of the C64 Core. You can directly access this list [here.](https://github.com/MJoergen/C64MEGA65/issues?q=is%3Aissue%20state%3Aopen%20label%3AV6)
This is not a guarantee that these features will be implemented, everything is under evaluation.

