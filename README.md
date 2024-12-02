# EtPwtC
## Equalizing the P with the C
short description: a place to bind all the steps and files necessary for unlocking and tuning the XIAOMI Redmi 13C, regardless of the model, Gale - Gust
### 1. Determining the model in question, Gale or Gust



### 2. Unlocking the Bootloader
### 3. Flashing custom-twrp recovery, depending on the model, in this case combo (Gale - Gust)
a) determining which miui version you are running

b) selecting the appropriate miui version, making sure it matches your region (Global, EEA, Taiwan) from:

[ https://mifirm.net/model/gale.ttt ]
> if necessary, as my model came with the miui version I couldn't find, to update to the available versions from the mifirm site (example 14.0.2 to 14.0.16) + sidenote, the unlocked bootloader persists through the update process (at least from my experience)
> > super necessary, critical step, in general, for acquiring boot.img and vbmeta.img, which we'll be using to, like boot, to flash it on top of the recovery, and to integrate the sideloaded recovery into the boot image, and for vbmeta, to be able to disable verity and verification of the loaded images via fastboot (bypassing integrity checks)

> extract the boot.img and vbmeta.img from the archives image folder and, for simplicity, copy the aforementioned files in the root directory where your adb/fastboot.exe resides

c) the flashing process with acquired files, includes the following steps:
> fastboot oem cdms

> fastboot --disable-verity --disable-verification flash vbmeta vbmeta.img

// renaming the twrp.img to recovery.img //

> fastboot flash boot recovery.img

> fastboot reboot recovery

// in case you get the "unknown reboot target recovery" message, depending on the fastboot cli version//

> do the 'barbara streisand' or the 'steven spielberg'

> fastboot boot recovery.img

// you should se your screen boot up to the TWRP logo, go past the screen and depending if you have a screen lock, greet you with a pattern-unlock grid or, if you didn't set up a screen lock beforehand, you'll be greeted with a TWRP menu //

// in case you end up on the TWRP logo, not going past the boot screen, then you probably flashed a wrong recovery image, not built against your current platform, and for that purpose there is the section UN-bricking the SOFT-brick-ed device, because it became soft like jelly on the touch and the only remedy is to throw bricks at it, piling them up on the top of the phone so we can later on, as I mentioned, UN-brick it //


// this is the part where we flash the original boot.image back, through the TWRP recovery, so we can later on, after flashing the boot.img, embed/flash the current TWRP/recovery image withing the current boot.img, actually, installing the TWRP recovery, via the recovery //



// as all of the mentioned steps were, in fact, preparation steps, as the REDMI 13c doesn't have a dedicated recovery partition, and we were bypassing the boot.img sequence which was replaced with a recovery, twrp one, only to be able, finally, to compensate for the lack of a dedicated recovery partition with embeding, integrating the assets of the recovery image within the boot.img //

### and, of course, always remember to treat others with... kidneyZ
