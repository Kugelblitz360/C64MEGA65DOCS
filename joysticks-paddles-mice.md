The good news: The C64 Core supports the complete input logic of the DE-9 ports (sometimes called DB9) of a Commodore 64. Just about everything that you can plug into a C64 will also work with the Core. (See the end of this page for the rare exceptions).

The bad news: Only peripherals that work on a real C64 will work here.

# Warning - incompatible hardware
Do not plug in DE-9-sticks or mice that are not C64 compatible. Especially not:
* Gamepads and Joysticks for SEGA, 3DO and CD32 game consoles
* Atari 7800 joysticks (sometimes used with Atari Flashback Retro consoles)

These use different pins on the port and even might damage your MEGA65. This has nothing to do with the C64 Core - it's just simple electricity.

There are many DE-9 (DB9) to USB cables available online that you might be tempted to use as joystick controllers, but they will not work as these are for serial connections and not for game controllers. The same is true for DE-9 extension cables that usually are so called "Nullmodems" and cross wires, so will not work with controllers. If you buy adapters or extensions, specifically ask for game controller use and avoid anything that says "serial".

## Switching ports virtually
One of the major annoyances of the C64 is that 80% of games control Player 1 by Control Port 2. Due to the way the keyboard and joystick ports are wired up, Control Port 1 and the keyboard interfere with each other and pressing fire on Port 1 is equivalent to hitting <kbd>Space</kbd>. But many older games and especially games that have a two player mode put the first player on Control Port 1. This leads to often needing to unplug and replug in the other port - or just having two joysticks constantly connected.

The C64 Core has a very nice solution for this: You can just switch the ports virtually. Just use the `Flip Joystick Port` function in the [menu](the-main-menu.html#flip-joystick-ports) accessible with the <kbd>Help</kbd> key.

## Joysticks
The Core supports two joysticks on the two DE-9 ports. As there is no user port on the Mega65, there is no support for any of the 4-joystick hardware mods that are floating around.

The Core supports all logic for 2, 3 and 5 button **C64 compatible** joysticks because these only use standard C64 functions.

Buttons 2 and 3 are realized via two unused lines for the paddles (basically emulating full left and full right on the paddle as a digital line rather than analog). If you want to modify a standard Competition Pro to support Buttons 2 and 3, you can find instructions here:

http://wiki.icomp.de/wiki/DE-9_Joystick

Buttons 4 and 5 are realized by a pure software trick: You can not press Up and Down at the same time and you can not press Left and Right at the same time, so these combinations can be used as buttons 4 and 5.

Further details on this, instructions for an adapter and patched C64 games can be found here:

https://github.com/crystalct/5plusbuttonsJoystick/tree/main

You can also program a **Mouster** to turn any USB-gamepad into a 5 button C64 controller. The same can be done with a **Unijoysticle** which even supports Bluetooth game controllers.

https://github.com/willyvmm/mouSTer

https://github.com/ricardoquesada/unijoysticle2

## Paddles
Standard DE-9 paddles are fully supported. Two paddles only need one port, so you can connect two pairs of two paddle, i.e. four paddles. These include original Commodore paddles and Atari CX30 paddles (for 2600 and/or Atari 400). Please be reminded that those paddles are pretty ancient analog technology that is not very precise. If you have control troubles while using a paddle, it is not a bad implementation inside the Core, but either in the game itself or the paddle simply has gone bad over the years. Current rereleased Atari CX30 paddles from 2023 for the recent Atari console rebuilds are getting very good reviews from users. Four games that have great paddle control are ``Omega Race (Commodore)``, ``Sea Wolf (Commodore)``, ``Arkanoid (Ocean)`` and for four players the modern ``Space Lords (RGCD)``.

## Mice
Only the Commodore 1350 type and 1351 type mice are supported. Amiga and Atari ST mice use a totally different way of communication on the DE-9 port and as the Core does not translate signals at all, no software on the C64 can use it. This is tricky because the MEGA65 in MEGA65 mode supports Amiga-style mouse control. **When you leave an Amiga-style mouse plugged in, it can render the keyboard unresponsive in the C64 Core.**

As Amiga-style "Tank" mice are widely available it is planned to support these in a future version of the Core (see the [roadmap](https://github.com/MJoergen/C64MEGA65/blob/master/ROADMAP.md)).

The **1350** type mouse basically is a joystick so it works with everything but, diplomatically said, is "not very precise".

The **1351** type mouse needs special software (GEOS being the most prominent example) and is a lot better but still not on a level with how we expect mouse control to behave today, so if it feels "wrong" to you and you have not experienced mouse control on a real C64, please be assured that it is not a problem of the Core.

If you need to control the Core with a mouse, your best option today is to aquire a **Mouster** device or a **TIKUS USB adapter** that can be setup to convert any USB mouse into a 1351 mouse. Unfortunately in its current software version Mouster can not automatically switch into 1351 mode but needs to be configured for this (it autoconfigures mice Amiga-style). The TIKUS needs to be in 1351/GEOS mode (blinks 3 times). Please check the documentation for these devices at these links:

https://github.com/willyvmm/mouSTer

https://lotharek.pl/productdetail.php?id=244

Other known mouse-converters seem to be out of stock or require PS2-mice which also are hard to get these days.

## Lightgun and Lightpen
In theory any standard C64 lightgun or lightpen connecting only to the DE-9 port should work. It **requires** a CRT on the VGA output with 15 KHz. [Please check the page about 15KHz output in this documentation.](vga-and-hdmi-output.html#retro-15-khz-for-cathode-ray-tubes) *We have not tested this and can only say it SHOULD work.*

## Bi-directional devices
All of the above devices basically are switches that are turned on and off and the C64 can read the status of these switches. The C64 can also send data to the device but this has been used only in very rare hardware projects:

* Trap Them Controller (sold out)
* Protovision Protopad (still in prototype stage)
* real time clock on CMD SmartMouse / SmartTrack (rare)
* Ninja SNES Pad (extremely rare)
* Multijoy (PCB available on their site)
* Atari CX21/CX50 (reproduction PCB available)

The hardware of the MEGA65 R6 revision is capable of accessing bi-directional devices, but the C64 Core does not support this (yet), so all these controllers are unsupported.