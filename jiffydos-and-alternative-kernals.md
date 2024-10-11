## What is JiffyDOS?

JiffyDOS is a replacement of the Kernal of the C64 as well as the ROMs of the 1541 disk drive that replaces the communication between these devices with much faster routines. Many disk functions are sped up by a factor of ten. JiffyDOS is very compatible with all kinds of software and considered to be the best software-only replacement for the C64.
Learn more about JiffyDOS in the [C64 Wiki](https://www.c64-wiki.com/wiki/JiffyDOS).

## How can I get JiffyDOS?

JiffyDOS is commercial software that you need to buy. It is not included with the C64 Core. We recommend that you either buy from

[Restore-Store (click here)](https://restore-store.de/89-jiffydos)

or from

[RETRO Innovations (click here)](http://store.go4retro.com/search.php?search_query=JiffyDOS&x=0&y=0).

You need to buy and download two ROM images, one for the C64 and one for the
1541. While both shops use the same name for the C64 ROM image, the name for
the 1541 ROM image differs:

* C64 ROM image: **JiffyDOS 64 KERNAL ROM Overlay Image**

* 1541 ROM image at Restore-Store: **JiffyDOS 1541 DOS ROM Overlay Image**

* 1541 ROM image at RETRO Innovations: **JiffyDOS 1541/1541C/1541II DOS ROM Overlay Image**

Make sure you double-check the name of what you buy, otherwise you might
end up with a ROM variant that is not supported by the C64 core.

You can buy additional ROMs for real hardware drives that you own. As the C64 Core does not support the 3,5" disk drive in the MEGA65, you also can not install the 1581-JiffyDOS ROM in the Core, but if you own a real 1581, the Core will support it with the Kernal ROM installed.

## Prepare JiffyDOS for the C64 Core

When you bought the ROMs, you received ZIP files. Unpack the ZIP files and get the `.bin` files from these.

The C64 for MEGA65 core needs two files to run JiffyDOS and each of them needs
to be exactly `16 kB = 16,384 bytes` in size. One file is the C64 Kernal+Basic ROM
`jd-c64.bin` and one file is the 1541 DOS ROM `jd-c1541.bin`. Perform the
following steps to create these files from the `*.bin` files you purchased.

### C64 Kernal ROM: `jd-c64.bin`

1. Download the C64 BASIC ROM [`basic.901226-01.bin` from zimmers.net](http://www.zimmers.net/anonftp/pub/cbm/firmware/computers/c64/basic.901226-01.bin)
2. Copy the BASIC and the JiffyDOS ROM together into one file. See below for detailed instructions for your operating system.
3. You now should have one file called `jd-c64.bin` that is 16384 bytes large

#### Example for the macOS and Linux terminal

The following commands assume that you are in a folder that is empty with the
exception of one file that is called `JiffyDOS_C64_6.01.bin`.

```bash
wget http://www.zimmers.net/anonftp/pub/cbm/firmware/computers/c64/basic.901226-01.bin
cat basic.901226-01.bin JiffyDOS_C64_6.01.bin > jd-c64.bin
```

#### Example for the Windows command prompt

The following command assumes that you are in a folder that contains the
following two files: `JiffyDOS_C64_6.01.bin` and `basic.901226-01.bin`.

```cmd
copy /b basic.901226-01.bin+JiffyDOS_C64_6.01.bin jd-c64.bin
```

Hint: Do not omit the `/b` (for binary) in the copy command above.

### C1541 DOS ROM: `jd-c1541.bin`

The JiffyDOS download package contains two `*.bin` files. Take the one that
is exactly `16 kB = 16,384 bytes` in size and rename it to `jd-c1541.bin`.

## Install JiffyDOS for the C64 Core

1. Turn off the MEGA65 and remove the SD Card that will be active when you use the Core. The default is to use the SD Card at the back of the machine when one is inserted, otherwise the SD Card at the bottom is used.
2. Make sure you have a `c64` folder in the root directory of the SD card.
3. Copy `jd-c64.bin` and `jd-c1541.bin` to the `c64` folder of your SD card.
4. Re-Insert the SD Card, turn on the MEGA65 and start the C64 core
5. Select "JiffyDOS" in the "Kernal" submenu of the core's menu

If you want the core to remember that you seleced JiffyDOS next time you start the MEGA65, make sure that you that you also have the config file `c64mega65` installed in your `c64` folder. (See [Core Installation](installation.html#config-file))

## Installing other Kernals than JiffyDOS

While the Core officially has no function to install other Kernal ROMs, there is no check whether the JiffyDOS-Kernal actually is JiffyDOS. If you want to install your own kernal you can name any 16KB Basic+Kernal ROM `jd-c64.bin` and any 16KB 1541 ROM `jd-c1541.bin` and they are activated if you select JiffyDOS in the Core menu. Just make sure you have installed both files, even if you only want to replace the C64 Kernal, you need to supply the standard 1541 ROMs then.

For example we have successfully tested **JaffyDOS**, a modified JiffyDOS Kernal. There is no reason why other Kernals should not work, but they are not tested. JaffyDOS can be found with your favourite Internet Search Engine.

Pro Tip: You can have different Kernels on different Micro SD Cards if for whatever reason you need to try more than one custom Kernal.

## Compatibility with hardware

Any external drive that works with JiffyDOS will work with the Core when JiffyDOS is active. To get the faster speed, of course the drive has to be equipped with the specific JiffyDOS ROMs. An external 1541 (not emulated) needs JiffyDOS ROMs installed locally to get faster speeds.

If you have an SD2IEC device with current firmware, it will work with the JiffyDOS Kernal active and give you very fast loading speeds.

## Installing other floppy speeders

Floppy speeders that require an additional cable (e.g. DolphinDOS) are not supported by the Core. Floppy speeders that require additional RAM on the 1541 also are not supported.

Cartridge-based floppy speeders work, unless they are external Kernal replacements which currently are not supported. Please see the page about [cartridges](c64-cartridges.html#other-cartridges-tested-and-working) for further information.

Mounted 1541 images (`.d64` files) support most Cartridge-based floppy speeders and JiffyDOS. Disks that are formated with different encodings than the standard format (stored as `.g64` files) are not supported at all currently. Also, you can not create new disk images inside the core. Formatting disks will not work at all.