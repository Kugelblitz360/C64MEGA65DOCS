The C64 Core has the following limitations when you want to save data:

* An already mounted ``.d64`` image can be changed. You can write data (save) to an existing ``.d64`` file. *You can not create a new file / empty disk image while inside the core*. Please wait until the disk drive LED has turned off before removing the Micro SD Card, resetting or power cycling.
* A mounted ``.crt`` file will **not** be changed. When you save something in an Easyflash or Gmod2 cartridge that is a file on your SD Card, it will **not** be written to the SD Card and will not survive a reset or power cycle.
* The built-in 3.5 inch disk drive is not supported at all in the C64 core.

These limitations do not apply to real hardware: If you connect a real disc drive, a SD2IEC or PI1541 device, or a physical Easyflash or Gmod2 cartridge (or their emulations on a Kung Fu Flash), everything will work as planned.

*Why?* The current implementation of the SD Card file system can not *create* files at all and also can not modify the size of files. It finds a file on the card and then writes directly to the positions of that file on your card. This works well with ``.d64`` files, but there are problems with ``.crt`` files because they actually have no fixed size due to emulators offering to not store unused banks, so they theoretically can shrink and grow (a behaviour you can see in the VICE emulator as "Optimize Image when saving" in its Easyflash options).

Tip: For emergencies, always keep an ``empty.d64`` file on your SD Card that you can rename later and mount when you need to save something on short notice.

For your convenience you can download an empty disk image [here](empty.d64).