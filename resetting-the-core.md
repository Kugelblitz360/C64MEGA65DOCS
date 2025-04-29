If you press the reset button of a cartridge (and you have an R6 or later release of the MEGA65), this will issue the standard C64 reset.

Nearly the same will happen if you press the Reset button on the left side of the MEGA65 briefly (less than 1.5 seconds) - we call this a **Soft Reset**. If you press it longer, you will do a **Hard Reset**

## Soft Reset
Briefly pressing the Reset button does reset the C64, but not the full MEGA65.

The C64 has a quite [sophisticated reset behavior](http://tech.guitarsite.de/cbm80.html), and some demos - such as ["That's the Way It Is"](https://csdb.dk/release/?id=11775&show=hidden) - make use of that, so that you can start certain parts when pressing the reset button. And also some games did - as a copy protection. This can be annoying when you want to exit a game and cannot:
  [Uridium](https://csdb.dk/search/?seinsel=all&search=uridium&Go.x=0&Go.y=0) and [Eagle's Nest](https://csdb.dk/search/?seinsel=all&search=eagles+nest&Go.x=0&Go.y=0) are examples for this. The bottom line is: A soft-reset will allow you to enjoy the original behavior including "reset demos", but you will also be stuck with the drawbacks.
	
## Hard Reset	

When you press the Reset button for longer than 1.5 seconds, the core will do a "forced reset" by simulating what is described [here](https://www.c64-wiki.com/wiki/Reset_Button) and what some cartridges like the Action Replay did. This will always reset the machine.

If you notice that the MEGA65's "POWER" LED turns blue, then you know that you pressed the reset button long enough to initiate a Hard Reset.

**IMPORTANT: Do not use the Hard Reset when a hardware cartridge is plugged in the Expansion Port of the MEGA65.**

The Core does ignore the CBM80 signature of a cartridge (or the RAM) when doing a Hard Reset - so the cartridge might not start but will be active in memory after the standard Reset which will have odd side effects (for example the Basic Bytes Free number will be smaller than usual). Just do another Soft Reset to get into a more useful state, the cartridge will be detected then. Some cartridges capture the Reset differently and will work even with a Hard Reset, but do not count on it.

If you need to do a full reset when a hardware cartridge is inserted, you can also powercycle the MEGA65. An inserted C64 cartridge will be detected and the C64 Core automatically started, in this case with the cartridge active.

## Soft vs. Hard Reset

The Soft Reset will only reset the C64, but not the Core itself. So your current settings and especially the file browser are left as-is. This is particularly useful when browsing large hierarchies of disk images. Imagine being in the fourth folder hierarchy of your disk image collection, browsing on page 10 of hundreds of files and then pressing reset: While a hard-reset let's you start over, including - again - browsing to the fourth folder of your disk image collection to page 10, the soft-reset let's you continue exactly where you left off.

**Currently, the Core will unmount the current ``.d64`` image when you soft-reset. You need to remount the disk.** (This behaviour is under discussion for further releases).

A Hard Reset will set back the file browser to the ``c64`` directory of the current SD Card and also will set back the system to the default options stored in the currently active SD Card.

## Getting back to the MEGA65 core

To get back to the MEGA65, you need to power cycle the machine, i.e. turn it off and on again. Please remember that the C64 Core will autostart when a physical C64 cartridge is inserted.