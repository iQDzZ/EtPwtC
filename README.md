# EtPwtC
## Equalizing the P with the C
short description: a place to bind all the steps and files necessary for unlocking and tuning the XIAOMI Redmi 13C, regardless of the model, Gale - Gust
### 1. Determining the model in question, Gale or Gust



### 2. Unlocking the Bootloader
### 3. Flashing custom-twrp recovery, depending on the model, in this case combo (Gale - Gust)
#### a) determining which miui version you are running

#### b) selecting the appropriate miui version, making sure it matches your region (Global, EEA, Taiwan) from:

[ https://mifirm.net/model/gale.ttt ]
> if necessary, as my model came with the miui version I couldn't find, to update to the available versions from the mifirm site (example 14.0.2 to 14.0.16) + sidenote, the unlocked bootloader persists through the update process (at least from my experience)
> > super necessary, critical step, in general, for acquiring boot.img and vbmeta.img, which we'll be using to, like boot, to flash it on top of the recovery, and to integrate the sideloaded recovery into the boot image, and for vbmeta, to be able to disable verity and verification of the loaded images via fastboot (bypassing integrity checks)

> extract the boot.img and vbmeta.img from the archives image folder and, for simplicity, copy the aforementioned files in the root directory where your adb/fastboot.exe resides

#### c) the flashing process with acquired files, includes the following steps:
> fastboot oem cdms

> fastboot --disable-verity --disable-verification flash vbmeta vbmeta.img

// renaming the twrp.img to recovery.img //

> fastboot flash boot recovery.img

> fastboot reboot recovery

// in case you get the "unknown reboot target recovery" message, depending on the fastboot cli version//

> do the 'barbara streisand' or the 'steven spielberg'

> fastboot boot recovery.img

// you should se your screen boot up to the TWRP logo, go past the screen and depending if you have a screen lock, greet you with a pattern-unlock grid or, if you didn't set up a screen lock beforehand, you'll be greeted with a TWRP menu //

// in case you end up on the TWRP logo, not going past the boot screen, then you probably flashed a wrong recovery image, not built against your current platform, and for that purpose there is the section UN-bricking the SOFT-brick-ed device, because it became soft like jelly 2 the touch and the only remedy is to throw bricks at it, piling them up on top of the phone so we can later on, as I mentioned, UN-brick it //


#### d) this is the part where we flash the original boot.image back, through the TWRP recovery, so we can later on, after flashing the boot.img, embed/flash the current TWRP/recovery image withing the current boot.img, actually, installing the TWRP recovery, via the recovery


> Within the TWRP menu go to the INSTALL TAB > select by, tapping in the bottom section, 'INSTALL IMAGE' option > select the original boot.img you placed on your phone > proceed with 'SWIPE TO FLASH' action

> GO BACK to the MENU, AVOID! REBOOTING


// as all of the mentioned steps were, in fact, preparation steps, as the REDMI 13c doesn't have a dedicated recovery partition, and we were bypassing the boot.img sequence which was replaced with a recovery, twrp one, only to be able, finally, to compensate for the lack of a dedicated recovery partition with embedding, integrating the assets of the recovery image within the boot.img //

// this is the part where we are, actually installing the TWRP, embedding it within the boot.img file //

> from the MAIN MENU, select the ADVANCED tab > select 'Flash current TWRP' option and proceed with the 'SWIPE TO FLASH' action > when completed, select the 'boot to SYSTEM' option or do a simple reboot if such option, while in recovery, arises

> REBOOT, by the time it starts loading the system, unplug the usb cable from the REDMI phone, REBOOT or power off the system > Press Power button while holding the volume up button, after the initial vibration of the phone, release the power button and keep holding the volume up button until the TWRP boot screen shows up > you successfully installed a custom recovery to your phone

### 4. Rooting the phone with the MAGISK solution
### 5. SOFT-unbrick method

## 
##
## P to the C part, stands for, bringing the Pee to the Cee, or the big P to the little C, or Performance to the... cLock

### GPU mod, MEDIATEK chipset, MALI G52 MC2 gpu
// observation wise, starting with the integrated 90 fps, refresh rate option for XIAOMI, that isn't persistent or existent at all, countering with a quick remedy to the given problem, taking into account that you have root access, and a terminal utility, for this example will be using termux app //

> tsu

> echo 90 > /sys/class/graphics/fb0/mtkfb_fps

##
### CPU mod, MEDIATEK chipset, HELIO G80, 6 kleine cores, 2 groSSe cores
// observation, starting with the 'all in wonder' magisk module, that brings the 'performace tab' to the mediatek chipset devices, isn't persistent at all, while the 2 big cores appear to be 'capped' at 2GHz, the remaining 6 little piggies roam throughout the dynamic clock table, quick remedy to the aforementioned, also, with the help of termux app //

// checking the available frequency table for the 6 little cores, opposed to the 2 big cores, divided into 2 group policies, policy0 (for the little cores) and policy6 (for the big cores) //

> cat /sys/devices/system/cpu/cpufreq/policy0/scaling_available_frequencies

// enabling the ppm driver for fixed, 'capped' clocks

> echo 1 > /proc/ppm/enabled

// setting the fixed core regime, divided into 2 clusters, [0] cluster for the little ones, [1] cluster for the big ones, projecting the policy enforcment mentioned above, for the 6 little cores //

> echo 0 1800000 > /proc/ppm/policy/hard_userlimit_max_cpu_freq

> echo 0 1800000 > /proc/ppm/policy/hard_userlimit_min_cpu_freq

// no-BS persistency check for the capped frequency against 6 little cores //

> watch -n 1 'cat /sys/devices/system/cpu/cpu[0-5]/cpufreq/scaling_cur_freq'







### and, of course, always remember to treat others with... kidneyZ
