<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Running Windows on the POCO X3 Pro

## Method 1: Dualbooting Android and Windows seamlessly (requires root) (recommended)
> [!NOTE]
>
> While method 1 is the recommended method, you should also probably set up method 2 as a fallback method

### Prerequisites
- [Magisk](https://github.com/topjohnwu/Magisk/releases/latest)
- [Modified TWRP](../../../releases/Recoveries)
- [NTFS Android Magisk Module](../../../releases/ntfsdroid)
- [UEFI](https://github.com/woa-vayu/msmnilePkg/releases/latest)
- [Android Boot Flashing App](../../../releases/dualboot)

#### Adding NTFS Support to android
- Install Magisk if you haven't already
- Install the NTFS Android magisk module through the Magisk manager

#### Application Setup
> [!NOTE]
>
> In order to mount Windows while you're booted in Android, you need to "shut down" Windows properly. To do this, restart Windows and then boot into TWRP as the screen fades to black. From here you can switch back to Android using the backup you made earlier.
- Download the StA Installer and the APK, then install the APK
- Create a folder named "UEFI" on your internal storage
- Copy the uefi image into the UEFI folder
- Open the app and allow any root access it wants
- Press the "BACKUP ANDROID BOOT" button, then dismiss the popup
- Press the "Mount/Unmount Windows button, then dismiss the popup
- Go to your file explorer and Windows should be mounted in sdcard/Windows (your internal storage). Move the StA Installer and boot.img backup into this folder
- Return to the WOA helper app and press "Quickboot to Windows"
- After Windows boots, run the StA installer in the C:\ directory
> You may need to disable any antivirus software present, if the installer does not work

#### Booting to Android
  
  - Run the new shortcut on your desktop as **ADMINISTRATOR**

#### Booting to Windows
  
  - Run the app
  - Press "Quickboot to Windows"

> If quickboot does not work, you may have shut down Windows incorrectly. If this happens, use the "Flash UEFI" button and manually reboot your phone.
  
## Finished!




## Method 2: TWRP (doesn't require root)
> Only recommended if you really don't want to root your device, because it is quite a bit slower to switch

### Prerequisites
- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)
- [Modified TWRP](../../../releases/Recoveries)
- [UEFI](https://github.com/woa-vayu/msmnilePkg/releases/latest)

#### Boot to TWRP
> If your recovery has been replaced by the stock recovery, boot to fastboot and run
```cmd
fastboot flash recovery path\to\twrp.img reboot recovery
```

> On unrooted devices MIUI might replace your recovery whenever you leave it. If this happens, flash the same TWRP image again while in TWRP. This prevents MIUI from replacing it.

#### Back up Android boot image
Use the TWRP backup feature to make a backup of your Android boot image, preferably on an SD card if possible. Name this backup "Android".

#### Flash UEFI
Flash the provided UEFI image in TWRP into the boot partition.

#### Back up Windows boot image
Make a backup of your boot image just like you did with Android, this time call it "Windows".

#### Optional: Setting up the StA app
Copy the boot.emmc.win file (should be 128MB) to the /win folder through TWRP's file manager, then rename it to boot.img), then download the StA installer in Windows and run it. This will create a "Switch to Android" shortcut on your desktop.
> You may need to disable any antivirus software that may be installed if the StA installer does not work

#### Booting to Android
Boot to TWRP and restore the "Android" backup, then reboot your phone.
> Or run the "Switch to Android" shortcut on your desktop as an **ADMINISTRATOR**, if you used the optional StA method

#### Booting to Windows
Boot to TWRP and restore the "Windows" backup, then reboot your phone.

## Finished!
