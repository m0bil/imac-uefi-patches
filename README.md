# imac-uefi-patches
Firmware UEFI mods for 2011 iMacs

Some patches may work on other same era Macs. Look at description inside patch for detailed information.

## How to use

 - Make a backup of your iMac firmware (bios).

 - Depending on patch type, use [UEFITool version 0.28](https://github.com/LongSoft/UEFITool/releases/tag/0.28.0) or UEFIPatch (part of UEFITool 0.28) to apply patches to your bios.


## How to backup you firmware (bios)

Create a [GRML linux](https://github.com/Ausdauersportler/GRML-FLASH/releases) usb, boot from it and use flashrom command to dump your eeprom: `flashrom -p internal -r my_bios.img`  
If reading fails with error "Multiple flash chip definitions..." add option `-c "CHIP_MODEL"` to flashrom.  
Do multiple reads and make sure they are the same. Always keep a backup of this file.

## How to program you firmware (bios)

Write back modified bios to eeprom chip using a hardware programmer like CH341A + SOIC clip.  
If you have previously applied the [eeprom unprotection patch](https://github.com/m0bil/imac-uefi-patches/tree/main/flash-protection-bypass) you can instead use a software programming like flashrom from Linux or _Intel Flash Programming Tool_ (FPT) from Windows or UEFI Shell.

## Warning

You should be familiar with how to disassemble your system and hardware programming of the eeprom chip. While this patches have been extensively tested,  there is always the risk of breaking some hardware parts.

**PROCEED AT YOUR OWN RISK!**
