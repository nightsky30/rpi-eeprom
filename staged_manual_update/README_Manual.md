Adapted from:

https://news.ycombinator.com/item?id=21670921

 - recovery.bin
 - One of the pieeprom files. Rename it to pieeprom.upd
 - One of the vl805 files. Rename it to vl805.bin
 - Generate the SHA256 sums of both files and place them in pieeprom.sig and vl805.sig (e.g. sha256sum pieeprom.upd > pieeprom.sig)

 - Place all files in /boot/firmware
 - Reboot

Upon reboot the Pi4 will see the recovery.bin and load it. It will detect the pieeprom.upd file and will then flash both pieeprom.upd and vl805.bin, rename itself to recovery.00x and reboot. During that next boot the recovery.bin doesn't exist any longer as it has been renamed and the boot process continues normally.
The key here is the name of the pieeprom.upd file. You can also name it pieeprom.bin, but in that case the recovery.bin isn't renaming itself and you'll have to manually delete the files from the SD card.
