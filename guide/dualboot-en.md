<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Running Windows on the POCO X3 Pro

## Dualbooting Android and Windows seamlessly

> [!NOTE] 
> This will work on any android version and kernel but it does take longer to boot into Android from Windows

### Prerequisites

- [Magisk](https://github.com/topjohnwu/Magisk/releases/latest)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

- [Modified TWRP](../../../releases/Recoveries)

- [NTFS Android Magisk Module](../../../releases/ntfsdroid)

- [UEFI](https://github.com/woa-vayu/msmnilePkg/releases/latest)

- [UEFI & Android Boot Flashing App](../../../releases/dualboot)

### Phone Setup

#### Adding NTFS Support to android

- Install Magisk if you haven't already
- Install the NTFS Android magisk module through the Magisk manager

#### Application Setup

- Install the APK provided
- Create a folder named "UEFI" on your internal storage
- Copy all uefi images into the UEFI folder
- Open the app and allow any root access it wants

### PC part

#### Flashing the recovery and booting it

- Reboot to the bootloader

- Run ```fastboot flash recovery <recovery.img> reboot recovery```

#### Transfering files to the phone

- When the recovery has booted run ```adb shell mount.ntfs /dev/block/by-name/win /win```
- Run ```adb shell dd if=/dev/block/by-name/boot of=/win/boot.img```
- Run ```adb push StA_installer.exe /win/Users/<username>/Desktop/StA_installer.exe```

#### Boot your phone into windows

- Do ```adb reboot bootloader``` to reboot into fastboot
- Do ```fastboot flash boot <UEFI File Here>.img reboot``` to flash the image and reboot the phone

#### Phone Setup - Windows

- Run the StA_installer.exe on your phone and follow any installation steps

#### Booting to android
  
  - Run the new shortcut on your desktop as **ADMINISTRATOR**

#### Booting to windows
  
  - Run the app
  - Press "Quickboot to windows"
  
## Finished!
