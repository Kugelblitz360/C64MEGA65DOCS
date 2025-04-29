You can not plug in a 1750 (or similar) RAM Expansion Unit, short **REU**, into the cartridge port as it requires DMA access which is not supported with the current revision of the Core. (Georam units will work, but are slower).

But you can simulate such a unit with the Core. Select `Simulate 1750 REU 512KB` in the `Expansion Port` section of the menu.

The 1750 512KB REU is as close to cycle accurate as it can go on a MEGA65. We are pretty constrained by the quirky HyperRAM implementation. This means our REU
is not perfect, but 99.9% perfect: It even runs the very picky
[TreuLove_ForReal1750Reu.d64](http://csdb.dk/getinternalfile.php/144854/TreuLove_ForReal1750Reu.d64)
version of Booze Design's Treu Love demo
([see CSDB page](https://csdb.dk/release/?id=144105))
that is supposed to only run on real hardware and also the absolutely awesome game
[Sonic the Hedgehog](https://csdb.dk/release/?id=212523) runs like a charme on the MEGA65.

Please feel free to browse
[CSDB's REU Releases](https://csdb.dk/search/advancedresult.php?form%5Bcategory%5D=releases&rrelease_type%5B%5D=6)
and enjoy them on your MEGA65.

The REU also works perfectly with GEOS: Configure a RAM drive, copy the programs, fonts and file you want to work with on the RAM drive and enjoy a 10x acceleration of your GEOS workflows. Don't forget to copy the results of your work on a "real disk" before ending your GEOS session so that all your data is persistently saved to the MEGA65's SD card. See also the section [Working with disks and drives](working-with-disks-and-drives.html) and the [documentation for working with GEOS](geos-on-the-mega65-c64-core.html).

Compatibility advice: **Only turn on the REU for software that is explicitly supporting the REU.** Otherwise you might experience random crashes of otherwise very stable software. Explanation: The REU itself is 99.9% compatible so you can count on it. But the majority of C64 software does not support the REU. Some of the software even gets unstable, if you have the REU activated. The reason for this effect is, that when the REU is activated, certain addresses in the C64 memory space that are normally free to be used for the software are not usable any more. If it happens that this software needs to work with these addresses and a REU is installed/activated, then the software crashes.