The MEGA65 has a built-in C64 compatiblity mode that can be reached by either typing ``GO64`` or by holding down the <kbd>MEGA</kbd> key when you power on your computer.

This GO64-Mode is only an approximation of a real C64, with some enhancements and many compatibility problems. The real C65 would have had a different CPU than the C64. It can, in theory, run C64 software but in reality it has different timings and does have different "opcodes". Quite a lot of games that have specific timing needs or any kind of copy protection would have failed. The MEGA65 accurately models these failures.

There are some things you can do with GO64 that are not possible with the C64 Core (but might be in the future). Please refer to the MEGA65 documentation for details on these features:

* The build-in disk drive is accessible in GO64 mode. It is "invisible" while using the C64 Core.
* The GO64 mode can be switched into a high-speed CPU mode which would make especially BASIC programs run a lot faster than on a real C64. The C64 Core always runs at the original C64 speed.
* The MEGA65 freezer (press <kbd>RESTORE</kbd> for approx. 1 second) is not available in the C64 core.
* The Ethernet port can not be accessed in the C64 core.
* GO64 Mode only supports .d81 images as mounted disks. On the other hand, the C64 Core only supports .d64 images as mounted disks.

If you are writing software for the C64 that can use any of these features and does not require full compatibility, the GO64 mode might be better suited for you.

**If you want to play C64 games or use published C64 software, you need to run the C64 Core.**