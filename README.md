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

c) the flashing process with acquired files, which goes like:
> fastboot oem cdms

> fastboot --disable-verity --disable-verification flash vbmeta vbmeta.img

// renaming the twrp.img to recovery.img //

> fastboot flash boot recovery.img

### and, of course, always remember to threat others with... kidneyZ
