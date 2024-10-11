Thanks to long filename support and alphabetically sorted file- and directory listings, using the file browser is straightforward. Press MEGA65's <kbd>Help</kbd> key to open the on-screen-menu while the C64 is running and either select `8:<Mount Drive>`, `PRG:<Load>` or `CRT:<Load>` using the cursor keys and <kbd>Return</kbd>. Here is how the browser works:

* Navigate up/down using the <kbd>Cursor up</kbd> and <kbd>Cursor down</kbd> keys
* Page up and page down using the <kbd>Cursor left</kbd> and <kbd>Cursor right</kbd> keys
* <kbd>Return</kbd> mounts a disk image (`.d64`), loads a program file (`.prg`) or load cartridge image (`.crt`)
* <kbd>Run/Stop</kbd> exits the file browser without mounting/loading
* The file browser remembers the browsing history, i.e. even while you climb directory trees, when you mount the next image, the file selection cursor is positioned where you left off. This is very convenient for mounting multiple subsequent disks of a demo or game in a row.
* Support for both SD card slots: The back slot has precedence over the bottom slot: As soon as you insert a card to the back slot, this card is being used. SD card changes are detected in real-time; also while the file browser is open.
* Within the file browser you can use <kbd>F1</kbd> to manually select the internal SD card (bottom tray) and <kbd>F3</kbd> to select the external SD card (back slot).
* The file browser defaults to the folder `c64` in the root of the SD card if this folder exists. Otherwise it defaults to the root folder.
* The file browser only shows files with a valid file extension for the mode it is currently in: Mounting disk images (`.d64`), loading programs (`.prg`) or loading cartridges (`.crt`).
* If you just want to unmount a `.d64` file, just press <kbd>Space</kbd> when the selection is on the "8:"-line of the main menu. That immediately unmounts the disc. This does not work with `.prg` and `.crt` files. To unmount a virtual cartridge, please deselect `Simulate Cartridge` by selecting `Use hardware slot` instead.

The filebrowser has some limits, especially on the number of directory entries. As a rule of thumb, do not put more than 500 files or subdirectories into one directory.