# Installing Windows on your POCO X3 Pro

## Files/Tools Needed

Modified TWRP:

| File Name                                       | Android version |
|-------------------------------------------------|-----------------|
| [twrp-3.7.1_12-vayu.img](https://github.com/woa-vayu/POCOX3Pro-Guides/raw/main/Files/twrp-3.7.1_12-vayu.img) | Android 12/12.1/13/14 |
| [twrp-3.7.0_11-vayu.img](https://github.com/woa-vayu/POCOX3Pro-Guides/raw/main/Files/twrp-3.7.0_11-vayu.img) | Android 11 |

- [Windows on ARM image](https://arkt-7.github.io/woawin/)

- [Drivers & UEFI](https://github.com/woa-vayu/POCOX3Pro-Releases/releases/latest)

### Boot into TWRP
>
> If your recovery has been replaced by the stock recovery, flash it again using

```cmd
fastboot flash recovery path\to\moddedtwrp.img reboot recovery
```

#### Execute the msc script
>
> If it asks you to run it once again, do so

```cmd
adb shell msc
```

### Diskpart
>
> [!WARNING]
> DO NOT ERASE, CREATE OR OTHERWISE MODIFY ANY PARTITION WHILE IN DISKPART!!!! THIS CAN ERASE ALL OF YOUR UFS OR PREVENT YOU FROM BOOTING TO FASTBOOT!!!! THIS MEANS THAT YOUR DEVICE WILL BE PERMANENTLY BRICKED WITH NO SOLUTION! (except for taking the device to Xiaomi or flashing it with EDL, both of which will likely cost money)

```cmd
diskpart
```

#### Select the Windows volume of the phone
>
> Use `list volume` to find it, replace `$` with the actual number of **WINVAYU**

```diskpart
select volume $
```

#### Assign the letter X

```diskpart
assign letter x
```

#### Select the ESP volume of the phone
>
> Use `list volume` to find it, replace `$` with the actual number of **ESPVAYU**
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
>
> [!Warning]
> DO NOT USE 24H2!!!

> Replace `path\to\install.esd` with the actual path of install.esd (it may also be named install.wim or 22631.2861.XXXXXXX.esd)

```cmd
dism /apply-image /ImageFile:path\to\install.esd /index:6 /ApplyDir:X:\
```

> If you get `Error 87`, check the index of your image with `dism /get-imageinfo /ImageFile:path\to\install.esd`, then replace `index:6` with the actual index number of **Windows 11 Pro** in your image

### Copying your boot.img into Windows

- Drag and drop the **rooted_boot.img** from the **platform-tools** folder into the **WINVAYU** disk in Windows Explorer, then rename it to **boot.img**.

### Installing Drivers

- Unpack the driver archive, then open the `OfflineUpdater.cmd` file

> If it asks you to enter a letter, enter the drive letter of **WINVAYU** (which should be **X**), then press enter

#### Create Windows bootloader files
>
> If any error shows up, such as "Failure when attempting to copy boot files", open `diskpart` again and assign any new letter to **ESPVAYU**, then replace the letter `Y` in the next command with the letter that you just added.

```cmd
bcdboot X:\Windows /s Y: /f UEFI
```

#### Remove the drive letter for ESP
>
> If this does not work, ignore it and skip to the next command. This phantom drive will disappear the next time you reboot your PC.

```cmd
mountvol y: /d
```

### Reboot to fastboot

```cmd
adb reboot bootloader
```

#### Boot into the UEFI
>
> Replace `path\to\vayu-uefi.img` with the actual path of the UEFI image

```cmd
fastboot boot path\to\vayu-uefi.img
```

### Reboot to Android
Your device should reboot by itself after +- 10 minutes of waiting, after which you will be booted into Android, for the last step.

## [Last step: Setting up dualboot](4-dualboot.md)
