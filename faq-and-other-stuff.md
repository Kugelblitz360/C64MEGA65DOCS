This page contains questions and answers that have been brought up by users of the Core over the past two years. Please check the list to the right if you came here for a specific problem.

## Top Issues
Well, there really is no real ranking of questions repeated over and over yet, but these here have been asked more often than others or simply feel important. We tried to group similar issues in the full list so this just links to the full answers below.

**SD Card file corruption** - please see [here](#important-information-about-micro-sd-cards) and if you have an R3 machine [here](#unexplainable-general-weird-behaviour)

**No picture on HDMI** - please see [here](#no-picture-on-a-connected-hdmi-display)

**Cartridge/Hardware does not work** - please see [here](#i-can-not-run-a-specific-cartridgeextension) and [here](#the-core-does-not-work-when-a-cartridge-is-inserted)

**Keyboard does not work** - please see [here](#the-keyboard-is-not-working)

**Barcode like display** - please see [here](#unsual-picture-after-a-reset-barcode)

**My game progress is gone after reboot** - please see [here](#i-saved-a-game-but-when-i-reboot-it-is-gone)

## What is this R3 / R6 thing I keep reading about?

There are several different version of the MEGA65 and the differences are explained [here](installation.html#differences-between-mega65-revisions).


## Video Issues
#### No picture on a connected HDMI display
Please check [here](vga-and-hdmi-output.html#hdmi-troubleshooting).

#### Strange picture on a VGA display
Please try the  ``Auto Adjust`` function or similar on your VGA display, and make sure that you have turned off [HDMI Flicker-Free](vga-and-hdmi-output.html#the-hdmi-flicker-free-option).

If you are using a flat screen rather than a bulky CRT, please do not use the 15 KHz modes, but if you have a bulky CRT, please try the [15 KHz mode](vga-and-hdmi-output.html#retro-15-khz-for-cathode-ray-tubes).

#### Unsual picture after a reset ("barcode")
A small but significant number of users have reported a problem with the C64 Core only showing vertical bars after a reset or irregularly after a number of minutes. It looks like this:

<img src="barcode1.webp" style="width:200px">
<img src="barcode2.webp" style="width:200px">

This behaviour is limited to R6 boards and is a very specific timing issue with the so-called "HyperRAM" component of the MEGA65. There is a temporary fix available in form of a new Alpha version of the Core. The only change is regarding this specific behaviour, but it can not be ruled out that the fix has negative side effects. If you want to install this version of the Core, please click the following link to download the installation files and follow the usual procedures:

https://t.ly/ujcev

You can also install the released version of the Core and this specific fixed alpha version in different slots of the MEGA65 for comparison.

**Do not install this version of the Core unless you repeatedly see those vertical bars.**


## Loading and Running Games

#### How do I load a game?
If you have stored C64 software on your SD Card, there are three ways:
* A ``.crt`` file for a game cartridge will automatically start after you have mounted it.
* A ``.prg`` file that you loaded will be automatically started if it is a standard program - if it does not autostart, it is either not a full programm (data files often also carry the prg extension) or requires start with a SYS command and a startadress that the Core can not know.
* A ``.d64`` file is a mounted disk image. The C64 never autostarted disks. You manually have to load a programm first. Unless several programs are stored on the same disk, please type in the following command:

```
LOAD "*",8,1
```

and press <kbd>Return</kbd> and wait (the 1541 disk drive is VERY slow in its original state, load times of up to three minutes are possible). In some cases you then need to start the programm manually by typing

```
RUN
```

and pressing <kbd>Return</kbd>. 

If there are several programs stored on a disk, please refer to Commdore 64 and 1541 documentation on the web.

#### A game or demo does not run correctly
Please check the following list of potential solutions:
* Is the game/demo compatible with PAL? The Core does not support NTSC-only software.
* Have you turned on the [REU emulation](the-1750-ram-expansion-unit.html)? This is not compatible with many games and should usually be switched off.
* Have you tried turning off [HDMI Flicker-Free](vga-and-hdmi-output.html#the-hdmi-flicker-free-option)? It does help with some very timing-intolerant programs and especially original copy protections.
* Some modern demos require the specific timing of the 8521 CIA. Turn it on by selecting [CIA: Use 8521 (C64C)](the-main-menu.html#cia-use-8521-c64c). Turn it off for any game you are playing, we have seen instances of games behaving weirdly when this is turned on.
* Try power cycling the MEGA65. A simple reset might leave residues in the C64 memory that interferes with some programs. Unlike a real C64, even a short power cycle clears the C64 memory.
* Do you have additional devices on the IEC bus? Some programs refuse to run if they see a device ``#9``, ``#10`` and so on. Try switching off the IEC bus in the menu.
* Some programs (even some cartridges) refuse to run or crash when [JiffyDOS](jiffydos-and-alternative-kernals.html) is active, switch to the [standard Kernal](the-main-menu.html#kernal-standard).
* Some copy-protected programs require a real 1541 drive or an exact 1541 emulation. Currently the Core does support a Pi1541-device on the IEC bus (and thinks it is a real 1541). Ultimate64 devices currently do not work. The 1541 emulation in the Core might be upgraded to a similar level of compatibility to these devices in the next version (end of 2025!).

If you find some game or demo that still does not work, be so kind to create an issue in the official Github: https://github.com/MJoergen/C64MEGA65/issues

#### A specific .prg file will not load correctly
There are programming tricks in some ``.prg`` files that will simply not work with the fast direct load of the Core. Put the ``.prg`` file into a ``.d64``, mount the disk, and it should work.

## General Menu Usage

#### The screen goes black when I select JiffyDOS
As JiffyDOS is commercial software, it is not included. Please see the section on [JiffyDOS](jiffydos-and-alternative-kernals.html).

#### The built-in freezer does not work
Unfortunately the MEGA65 calls its system menu a "Freezer" but on the C64 this is usually something slightly different. The MEGA65 Freezer is only part of the MEGA65 and can not be accessed when any other core, including the C64 Core, is active. Because the C64, unlike the C65, had no <kbd>Help</kbd> button, it uses this instead of <kbd>Restore</kbd> to access the Core menu.

The <kbd>Restore</kbd> key of the C64 calls a "Non-Maskable Interrupt" which can be used in conjunction with some of the freezer cartridges and is used in some demos or games, for example to reset game options to their default. In the C64 Core this functionality is fully replicated, so the <kbd>Restore</kbd> key has no additional function.

Please also see the documentation about cartridges, especially [this section](c64-cartridges.html#freezer-cartridges).

#### The file browser does not display all files
First of all, the file browser will only display files with the currently appropriate extension, i.e. when mounting a disk, it will only show directories and ``.d64`` files. Also there is a limit of roughly 625 directory entries per directory, so putting for example all files from the OneLoad collection into one directory will not work. Try to keep a directory to a maximum of 300 files or subdirectories (you can nest directories very deep). Try creating directories for every first letter of the files or sort your games by genres or developers.

#### The file browser does not react
If you have many files in a directory, the file browser needs a few seconds to gather all information. Unfortunately you currently get no visual feedback that the file browser is working. Please wait a few seconds and also make sure that you do not have hundreds of files in a directory if you are in a hurry.

#### How can I pause the C64?
Just like a real C64, the C64 Core for the MEGA65 has no pause function. If you need pause functionality, you might want to look at C64 emulation on a PC instead.

#### The Core forgets the settings after a reboot
The Core requires a settings file with a specific length in a specific place. If this file is not there when the Core starts, it will not save settings. Please check [here](installation.html#config-file).

#### How can I unmount a virtual cartridge file?
To unmount a virtual cartridge, please deselect `Simulate Cartridge` by selecting `Use hardware slot` instead.

## Input Problems

#### The keyboard is not working
If your keyboard is working while you are using the MEGA65 core but you cannot type properly while using the C64 core and the <kbd>Help</kbd> menu works fine then please check if you have an **Amiga Mouse** or a joystick or other device with activated auto-fire connected to one of the control ports. If so, please remove it and you will be able to type properly. Please also see the section on [Joystick and Mouse](joysticks-paddles-mice.html).

#### The mouse is not working
The C64 Core, unlike the MEGA65 core, does **not** support Amiga-style mice. You need to use a C64 compatible mouse. Please see the section on [Joystick and Mouse](joysticks-paddles-mice.html).

#### The paddle is not working
There are several lists on the internet that claim that certain games (a prominent example is `Krakout`) could be played with a paddle. Most of these lists are unfortunately wrong. If a game does not specifically mention paddle control in the title screen, it most likely does not have it. [More on paddles here](joysticks-paddles-mice.html#paddles).

#### My lightgun is not working
Lightguns require a 15 KHz VGA setup and will not work with HDMI monitors or any flatscreen TFT connected to VGA. [More on lightguns here](joysticks-paddles-mice.html#lightgun-and-lightpen).

#### A gamepad / joystick is not working
The C64 Core is incompatible with controllers designed for SEGA consoles, the CD32, the Atari 7800 and the 3DO, even if they have the same plug. Please see the section on [Joystick and Mouse](joysticks-paddles-mice.html).


## Saving data

#### I saved a game but when I reboot, it is gone
Most likely you have used an Easyflash or Gmod version of a game mounted as a virtual cartridge, a ``.crt`` file. Unfortunately the Core does not write back the cartridge memory to the SD card when it is changes. You need to find a version of the game that saves games to a mounted `.d64` image (or a connected real drive). Also make sure that you created an image for saved games before starting the game, as the Core can not create empty disks for you. For your convenience you can download an empty disk image [here](empty.d64).

#### I need to save something to an empty disk
The C64 Core can not create or format disks. You need to have some spare empty ``.d64`` files on your SD Card. For your convenience you can download an empty disk image [here](empty.d64).

## Disk drive issues

#### I can not hear any drive sounds
That is correct. The C64 Core does not have emulated drive sounds when a ``.d64`` is mounted

#### I can not format a .d64 file
That is correct. While most commands that access the contents of a ``.d64`` file work, the format routine of the virtual 1541 does not. For your convenience you can download an empty disk image [here](empty.d64).

#### I can not open a specific .d64 file
The C64 Core does not support ``.d64`` files that include error maps. Please see [here](working-with-disks-and-drives.html#supported-d64-variations).

#### I can not access the 3.5 inch disk drive
That is correct. The C64 Core does not access the internal disk drive of the MEGA65.

## Other hardware issues

#### I can not run a specific cartridge/extension
The C64 Core has not yet implemented a 100% version of the cartridge port. Cartridges with very special timing or DMA access do not work. Prominent examples are Kernal replacement in EasyFlash3, the Ultimate II(+) and the physical REU units. Find out more about this [here](c64-cartridges.html).

Also, if your cartridge has a Reset button that works, but still does not activate the cartridge, please make sure that you enabled the cartridge port of the MEGA65 in the main menu by selecting `Use hardware slot` - if that option is off, the cartridge will not work (but the reset line still does).

#### The Core does not work when a cartridge is inserted
You might have to update the MEGA65 CORE #0. This issue is described [here](installation.html#issues-with-cartridge-compatibility).

#### I can't connect to a network
That is correct. The C64 Core does not use the Ethernet port. You need to be in MEGA65 mode for all network file transfers.

#### Can I access the MEGA65 Realtime Clock from the C64 Core?
Yes you can. The Core does emulate the **CP-Uhr F83**, a clock module that is plugged into the C64 tape port. In the current version of the Core it is always active. This is equivalent to the **Tape RTC (PCF8583)** device in the VICE emulator. Currently this clock module can not be switched off and has no user options. You can find additional info here: https://github.com/MJoergen/C64MEGA65/blob/master/doc/RTC.md

#### SD2IEC / Pi1541 issues
If you have errors with SD2IEC or Pi1541 devices, please check if they light up when you connect them to the MEGA65, but not their power supplies. If their LEDs light up faintly, these devices are not fully protected against the +5V of the IEC bus. We have seen data transfer problems with these devices and right now can only recommend replacing devices. More details can be found [here](working-with-disks-and-drives.html#sd2iec-and-pi1541).

## Hacks, Tips and Tricks

#### How can I power peripherals that are plugged into the tape port of a C64?
The MEGA65 does not have a tape port, some devices like some SD2IEC versions use the tape port to get their 5 Volts. There is a hack to get this from a location on the MEGA65 motherboard described in the Discord [here](https://discord.com/channels/719326990221574164/1271433803386060845/1271433803386060845). This is a hack and could theoretically damage hardware, so is only recommended if you really know what you are doing.

#### Can I replace the C64 Kernal with my own?
Currently you can use one custom Kernal per Micro SD Card by naming your files specifically and selecting JiffyDOS in the Core. Please find instructions [here](jiffydos-and-alternative-kernals.html#installing-other-kernals-than-jiffydos).

#### Can I change the color palette of the C64 Core?
The C64 Core uses carefully measured colors that are as close as possible to the PAL C64 output. These colors look pale, especially compared to NTSC machines, but are currently your only option. So no, you can not change the palette.

For color nerds it might be an interesting additional info, that we actually implemented this carefully measured color scheme:

https://www.pepto.de/projects/colorvic/

#### Can the Core run GEOS?
GEOS works very well on the MEGA65 using Version 5.1 of the core. AmokPhaze101 wrote a great step-by-step documentation:

1. Download GEOS [using this download link](https://github.com/MJoergen/C64MEGA65/raw/master/doc/assets/geos.zip)
2. Work with AmokPhaze101's tutorial: [View and download PDF](https://github.com/MJoergen/C64MEGA65/blob/master/doc/GEOS_WITH_THE_C64_CORE.pdf)
3. Learn how to use the [Real Time Clock](https://github.com/MJoergen/C64MEGA65/blob/master/doc/RTC.md)

## Important information about Micro SD Cards

**First and foremost: Always use the proper command for your computers operating system to *eject* the Micro SD card when you added files to it via your computer. If you just take it out it might damage the filesystem because write caches have not been written fully.** This is true for Windows, Mac, Linux, Android or whatever other clever device you use. Even the MEGA65. If you write files to the Micro SD Card while in MEGA65 mode via the Ethernet connection, you should always wait a second or two before resetting or turning off the MEGA65. Writes are done immediately, but modern Micro SD cards have an internal cache and if they lose power during a write cycle you will get data loss. 90% of all errors on Micro SD cards can be traced back to them being taken out of a desktop/laptop computer without using the respective eject command first.

Do not use Micro SD Cards larger than 32 GB.

Please make sure that your Micro SD Card has been formatted either by the MEGA65 tool or by the official SD Card formatting software found here for various operating systems:

https://www.sdcard.org/downloads/formatter/

The Operating System of your computer might offer to format ``FAT32`` but in reality you will get extra unwanted files, small other issues in the filesystem and in the end something that NOT follows official specifications. Also refrain from partitioning the Micro SD Card into several partitions.

Please immediately after formatting the card create a directory called ``c64`` and copy the Config File called ``c64mega65`` into it. It needs to be the version that came with the installed version of the Core, _it needs to be exactly the correct size!_

Please use a good brand-name card like Samsung, Verbatim or SanDisk. They are really cheap these days anyway.

If you see oddities with your card, your best option is to take a computer, copy all the files off the card, format it, then copy all the files back to the card in order to have a proper file and directory structure. And don't forget to eject.

## Unexplainable general weird behaviour

There is a hardware problem with the older R3 revisions of the MEGA65 and its HDMI output. A monitor that is plugged in can **back power** the MEGA65. This will lead to all kinds of problems especially with the Micro SD card access ending in overall instability of the whole system.

**You can skip the following paragraphs if your MEGA65 is an R6 revision.**

If your MEGA65 is connected to any HDMI device: Never switch-on this device before you have successfully switched-on your MEGA65. Or to put it the other way round: **Always switch-on your MEGA65 first** and **THEN** switch-on your HDMI device (monitor, frame grabber, etc.).

For the C64 core this means: While your MEGA65 and your HDMI device are switched off: Hold the <kbd>No Scroll</kbd> key while you switch on the MEGA65 and while the HDMI device is still off. Now, you can switch on your HDMI device and use the MEGA65's core selection menu to select the C64 core. You can also use the key combination <kbd>No Scroll</kbd> + _number of the C64 core in the core menu_ to directly select the C64 core.

Another way to resolve the issue is to put a cheap HDMI switch between the
MEGA65 and your device. You will find two Amazon links to devices that are
known to work [here in Dan's MEGA65 Welcome Guide](https://dansanderson.com/mega65/welcome/hardware-issues.html?highlight=hdmi#failure-to-boot-and-keyboard-lights-glow-when-off).

