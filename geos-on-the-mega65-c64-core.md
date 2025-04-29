This document describes the very basic steps required to run GEOS on the MEGA65 c64 core.

For an exhaustive description and resources about GEOS, visit https://www.lyonlabs.org/commodore/onrequest/geos/index.html

For video resources about using GEOS and other retro stuff, visit https://www.youtube.com/@MyDeveloperThoughts

## Pre-Requistes

In the Mega65 configuration, ensure the joystick mouse mode is configured as <bold>Normal</bold>

<img src="GEOS-01.jpg">
<img src="GEOS-02.jpg">

Connect a Mouse or a Joystick on Port 1

If using a mouSTer adapter, ensure it is configured as a "C64" mouse. In the .ini file, you should have:

<img src="GEOS-03.jpg">
<img src="GEOS-04.jpg">

For an exhaustive description of the mouSTer adapter, refer to this youtube video :
https://youtu.be/L8rbam3OjGY?si=j_sLrAJJI2a0sDCz

## Files needed

Copy the following files to the "c64"directory of your SD card:
* `GEOS64.D64`
* `APPS64.D64`
* `GEOCALC.D64`
* `SPELL64.D64`
* `WD-CALC.D64`
* `WD-PAINT.D64`
* `WD-WRITE.D64`
* `WRUTIL64.D64`

If you do not have your own version of GEOS, a tested version is available [here](https://github.com/MJoergen/C64MEGA65/raw/master/doc/assets/geos.zip).

You also need an empty D64 file to save data to. You can use this file: 
[empty.d64](empty.d64). Of course you can rename this on your PC to any other `name.d64`. Remember that the Core currently can not create .d64 files for you, they need to be present on the SD Card. See also [here](saving-data-with-the-c64-core.html).

## After starting the C64 Core

* Enter Menu: <kbd>HELP</kbd>
* Ensure the virtual REU is enabled: `Simulate 1750 REU 512KB`
*	Ensure JiffyDos is **not** enabled: `Kernal: Standard`

<img src="GEOS-07.jpg">

* Mount geos64.d64

<img src="GEOS-08.jpg">
<img src="GEOS-09.jpg">

* Load main GEOS program by typing `LOAD "GEOS",8,1` and <kbd>Return</kbd>. This will load and start GEOS desktop automatically.
 
<img src="GEOS-10.jpg">

## Configuring the Pointer
 
Press <kbd>MEGA</kbd> + <kbd>I</kbd> to display the device selector.

<img src="GEOS-12.jpg">

When no device has been selected yet, use four Cursor-Keys move the blue arrow. 

To use a mouse, move the arrow to `COMM 1351` and press <kbd>Return</kbd>, then move the arrow to `OK` and again press <kbd>Return</kbd>.

<img src="GEOS-12.jpg">
 
The mouse is now configured and ready to be used.
 
To use a mouse, move the arrow to `JOYSTICK` and press <kbd>Return</kbd>, then move the arrow to `OK` and again press <kbd>Return</kbd>.
 
<img src="GEOS-19.jpg">

The Joystick is now configured and ready to be used. At any time you can re-configure the device with <kbd>MEGA</kbd> + <kbd>I</kbd>.

## Configuring the REU

Initialize the REU virtual drive with <kbd>MEGA</kbd> + <kbd>Left Shift</kbd> + <kbd>B</kbd>

<img src="GEOS-20.jpg">

We now have a REU ram drive called "RAM 1571" and we are going to copy the applications to it.

## Copying Applications to REU

Mount the disk called `apps64.d64`

<img src="GEOS-19.jpg">
 
Move the mouse pointer on to the `System` disk, left click on the `system` disk, it will switch to the `Applications` disk.

<img src="GEOS-23.jpg">

<img src="GEOS-24.jpg">
 
Left click once on `DESK TOP`to select it, then click again and a blue copy of the desktop icon is highlighted.

<img src="GEOS-25.jpg">

<img src="GEOS-26.jpg">
 
Drag the blue icon on to `RAM 1571`, then left click to trigger the copy to the REU.

<img src="GEOS-27.jpg">
 
Please wait until the Drive LED of the MEGA65 stops flashing. Then proceed the exact same way to copy `GEOWRITE` and `GEOPAINT` to the RAM 1571 drive.

 ## Copying Applications back to an empty disk
 
While you can use your applications on the REU drive, it's content will be lost when you leave the C64 Core or turn off the MEGA65. In order to save your work, please mount an empty disk and copy the needed applications back to that disk.

Mount the `empty.d64` disk.

<img src="GEOS-33.jpg">

Left click on the `Applications` disk, GEOS discovers the empty disk and ask to confirm that you want to convert it to GEOS format.

<img src="GEOS-34.jpg">

<img src="GEOS-35.jpg">
 
Left click on `YES`. We now have an empty disk on which we are going to copy the content from REU drive. Left click on `RAM 1571` drive B to access its content.

<img src="GEOS-38.jpg">

Copy all applications to the `Disk A` by dragging their icons onto it.

<img src="GEOS-39.jpg">

Left click again on `Disk A`, then double click `GEOWRITE` to start it.

<img src="GEOS-43.jpg">

Left click on "CREATE" to create a new document, enter a name and then press <kbd>Return</kbd>.

<img src="GEOS-45.jpg">

<img src="GEOS-47.jpg">

Type some text, then left click on `File` `Update` to commit your edit to the file on disk.

<img src="GEOS-50.jpg">

Left click on `File` `Quit` to exit GEOWRITE.

<img src="GEOS-51.jpg">

<img src="GEOS-52.jpg">

You can now either start Geowrite again or click on the document that appeared on the disk.

The same principles apply to Geopaint. For Geocalc you first need to copy the application from the `geocalc.d64` disk to the REU and then to an empty disk.