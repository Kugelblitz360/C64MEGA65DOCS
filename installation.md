The C64 Core is only of of many different cores for the MEGA65. A current list of cores can be found on a sister webpage:

https://kugelblitz360.github.io/m65-altcores/

## Where to find it?

The current release version of the Core can always be found on the official MEGA65 filehost. You can use this [direct link](https://files.mega65.org?id=896a012f-59e4-456c-b91f-7e989b958241) to the ZIP file that contains several versions of the Core.

## Which file to install?
You need the correct `.cor` file for your MEGA65. You can find a complete description of the different models on the [alternative cores site](https://cores.mega65.org/).

In most cases you just need to know whether you have an R3 or R6 model and pick the `.cor` file that has either R3 or R6 in its filename.

## How to install the Core?
Please either follow the instructions in the MEGA65 manual or the [instructions on the Alternative Cores site](https://cores.mega65.org/how-to-use-alternative-cores.html).
	 
## Additional files
The Core support loading virtual disks, cartridges and single programs from both SD card slots if the cards are formated in FAT32. We recommend formatting either with the MEGA65 tool or using the SD Card Formatter tool from the SD Card Association. The formatting options of your operating system might not create a 100% compliant FAT32 filesystem.

https://www.sdcard.org/downloads/formatter/

After formatting please create a folder called `c64` in the root directory of the SD Card. The Core will use this as the default/start folder for your C64 content. You can put your `.d64`, `.prg` and `.crt` files here or in subdirectories.

Optionally you can add install [JiffyDOS](jiffydos-and-alternative-kernals.html) or a Real-Time-Clock driver for Geos [RTC](https://github.com/MJoergen/C64MEGA65/blob/master/doc/RTC.md) (useful only on R6 boards).

To configure the Core after installing it, just start it and press the <kbd>Help</kbd> key anytime.

### Config file
If you want the core to remember the settings you made in the on-screen-menu,
then make sure that you copy the config file into the folder called `c64`. This `c64` folder needs to be located in the root folder of the SD card that is active when you boot the core. The config file is called `c64mega65` (with no file extension) and is located in the ZIP file that you downloaded from the [MEGA 65 filehost](https://files.mega65.org?id=896a012f-59e4-456c-b91f-7e989b958241).

The very first time you start the core after you copied the `c64mega65` config file into the `c64` folder, it will detect the new config file and present you with factory default settings when you press <kbd>Help</kbd> to open the on-screen-menu. After that, the core will always save the settings when you close the on-screen-menu and remember them when you restart the core at a later time. If you need to reset the Core to default settings for any reason, please replace the `c64mega65` file on the SD card with the version from the filehost.

### When changing SD cards
You can change SD Cards while running the Core, but this will have the side effect that your config file will be saved to this card and only if there already exists such a file as described above.

## Differences between MEGA65 revisions
There are subtle but important differences between the different revisions of the MEGA65. Here is a short description of the differences that have an effect on the C64 Core operation.

### Details of the revisions

| MEGA65 model   |   Years   | File name             | Comment
|:--------------:|:---------:|:---------------------:|-------------------------
| R2             | 2019-2020 | &lt;none&gt;          | R2 is a very rare pre-series model, only 20 of them were built. The C64 for MEGA65 core does not run on R2 machines.
| R3/R3A         | 2020-2023 | C64MEGA65-V5.2-R3.cor | R3 is the "DevKit" (100 were built) and R3A are batches 1 and 2. If your MEGA65 was manufactured before 2024 then you have an R3 or R3A machine.
| R4             | 2023      | C64MEGA65-V5.2-R4.cor | Development board on our way to the R6. Only 10 of them were manufactured (board only, no complete machines).
| R5             | 2023      | C64MEGA65-V5.2-R5.cor | Upgraded version of R4 that contains new circuits for the expansion port. Only 10 of them were manufactured (board only, no complete machines).
| R6             | 2024+     | C64MEGA65-V5.2-R6.cor | Latest and greatest MEGA65. Manufactured from 2024 on.

### Differences in the C64 Core operation

| Issue| Details | R3/R3A |R4 |R5 |R6
|:-:|:----:|:-:|:-:|:-:|:-:
| Bug: HDMI backpower issues| [Learn more](faq-and-other-stuff.html#unexplainable-general-weird-behaviour), what wide range of problems and strange effects HDMI backpower issues are creating and how to avoid these issues.| yes| no| no| no|
| DAC for analog 3.5mm audio jack| While on R3/R3A machines the analog audio that comes out from the 3.5mm audio jack is "OK" and sometimes is plagued by hissing and humming, the newer machines feature a high-quality audio digital to analog converter (DAC) that leads to a crystal clear output.| standard | DAC| DAC| DAC|
| Hardware cartridges: Bi-directional reset signal| Makes the core compatible with even more cartridges. Two examples that stand out are: (1) You do not need the "reset workaround" for the Kung Fu Flash (KFF) any more (2) Reset buttons and "special" buttons at most freezer cartridges are working now.| no| no| yes| yes|
| Supercapacitor for Real-Time-Clock (RTC)| Ensures that the MEGA65 remembers the date/time even if you did not install a CR2032 battery.| no| yes| yes| yes|
| Bug: Limited ability to pull Expansion Port's RESET to GND | R5 boards contain a bug that reduces compatibility as described [here](https://github.com/MJoergen/C64MEGA65/issues/118). Can be fixed by "modding" the board. Needs some soldering skills.| no| no| yes| no|

### Issues with Cartridge Compatibility
If only very few physical cartridges (and less than described [here](c64-cartridges.html)) are working, you need to update the MEGA65 CORE #0. This should only be relevant for machines that have been built before 2024.

To check if this is the case: Press the <kbd>Help</kbd> key while you experience the "not working" situation. If the [well-known C64 for MEGA65 menu](c64coremenu.jpg)
is not being shown after you pressed <kbd>Help</kbd>, then instead of the dedicated C64 core, the standard MEGA65 core is currently running which is the reason why your hardware cartridge is not working.

The core in slot #0 (which is the MEGA65 core) decides, which core needs to be started if a hardware cartridge is inserted into the MEGA65's Expansion Port. The old version that most of the R3 MEGA65 have installed is buggy and needs to be updated. The full procedure on how to do this is described here:

https://mega65.atlassian.net/l/cp/1fkp5zvQ

If your MEGA65 was manufactured and delivered in 2024 you do already have a working version of this CORE #0, although further updates might be available.