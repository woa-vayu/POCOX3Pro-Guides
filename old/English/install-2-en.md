<img align="right" src="https://github.com/woa-vayu-archive/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">

# Running Windows on the POCO X3 Pro

## Installation
> [!NOTE]
> It is recommended to open CMD or powershell as an admin now, if you haven't already on the last page, and then access the platform-tools folder using the `cd C:\path\to\platform-tools` command, replacing the path with the actual path of the folder.
> Use the same window in the entire guide, do not close it.

### Prerequisites
- [ARM Windows esd](https://worproject.com/esd) (Select - Version:  ```11``` Build:  ```22631.2861``` Architecture:  ```ARM64``` Edition:  ```CLIENT``` Language:  ```select your language```)
    
- [Drivers](https://github.com/woa-vayu-archive/Vayu-Drivers/releases/latest)

- [Recovery image](https://github.com/woa-vayu-archive/Port-Windows-11-POCO-X3-Pro/releases/tag/Recoveries) (should already be installed)

### Boot back into recovery to start installing Windows
> If your recovery has been replaced by the stock recovery, flash it again using
```cmd
fastboot flash recovery <recovery.img> reboot recovery
```

#### Execute msc 
> If it asks you to run it once again, do so
```cmd
adb shell msc
```

### Diskpart
> [!WARNING]
> DO NOT ERASE, CREATE OR OTHERWISE MODIFY ANY PARTITION WHILE IN DISKPART!!!! THIS CAN ERASE ALL OF YOUR UFS OR PREVENT YOU FROM BOOTING TO FASTBOOT!!!! THIS MEANS THAT YOUR DEVICE WILL BE PERMANENTLY BRICKED WITH NO SOLUTION! (except for taking the device to Xiaomi or flashing it with EDL, both of which will likely cost money)

```cmd
diskpart
```
  
#### Select the Windows volume of the phone
> Use `list volume` to find it, replace "$" with the actual number of **WINVAYU**
```diskpart
select volume $
```

#### Assign the letter X
```diskpart
assign letter x
```

#### Select the ESP volume of the phone
> Use `list volume` to find it, replace "$" with the actual number of **ESPVAYU**
```diskpart
select volume $
```

#### Assign the letter Y
```diskpart
assign letter y
```

#### Exit diskpart
```diskpart
exit
```

### Installing Windows
> Replace `<path\to\install.esd>` with the actual path of install.esd (it may also be named install.wim)

```cmd
dism /apply-image /ImageFile:<path\to\install.esd> /index:6 /ApplyDir:X:\
```

> If you get `Error 87`, check the index of your image with `dism /get-imageinfo /ImageFile:<path\to\install.esd>`, then replace `index:6` with the actual index number of Windows 11 Pro in your image

### Installing drivers
> Unpack the driver archive, then open the `OfflineUpdater.cmd` file

> If it asks you to enter a letter, enter the drive letter of **WINVAYU** (which should be X), then press enter
  
#### Create Windows bootloader files for the EFI
> If an error occurs when copying boot files, check `diskpart` to see if **ESPVAYU** still has letter Y. If it does not, add any other letter (such as K) and replace the Y in the below command with said letter respectively
```cmd
bcdboot X:\Windows /s Y: /f UEFI
```

#### Remove the drive letter for ESPVAYU
> If this does not work, ignore it and skip to the next command. This phantom drive will disappear the next time you reboot your PC.
```cmd
mountvol y: /d
```

### Reboot to Android
```cmd
adb reboot
```

> Set up your device, then go to the last step

## [Last step: Set up Dualboot](/guide/English/dualboot-en.md)


















