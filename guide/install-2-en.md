<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Running Windows on the POCO X3 Pro

## Installation

## Installing Windows

### Prerequisites
- A brain
- A PC or another device running Windows 10 or 11
- [Windows on ARM64 image (Windows 11 only)](https://uupdump.net/)
- [UEFI image](https://github.com/woa-vayu/msmnilePkg/releases/latest)
- [Drivers](https://github.com/woa-vayu/Vayu-Drivers/releases/latest)
- [Modified TWRP](../../../releases/Recoveries) (should already be installed)

#### Boot into TWRP
> If your recovery has been replaced by the stock recovery, flash it again using
```cmd
fastboot flash recovery path\to\twrp.img reboot recovery
```

#### Execute the msc script

> If it asks you to run it once again, do so

```cmd
adb shell msc
```

  

### Assign letters to disks
  

#### Start the Windows disk manager

> Once the X3 Pro is detected as a disk
> (if it isn't, replug the device)

```cmd
diskpart
```


### Assign `X` to Windows volume

#### Select the Windows volume of the phone
> Use `list volume` to find it, it's the one named "WINVAYU"

```diskpart
select volume <number>
```

#### Assign the letter X
```diskpart
assign letter x
```

### Assign `Y` to esp volume

#### Select the ESP volume of the phone
> Use `list volume` to find it, it's the one named "ESPVAYU"

```diskpart
select volume <number>
```

#### Assign the letter Y

```diskpart
assign letter y
```

#### Exit diskpart
```diskpart
exit
```

  
  

### Install

> Replace `path\to\install.wim` with the actual path to install.wim,

> `install.wim` is located in sources folder inside your ISO
> (it might also be named `install.esd`)
> You can get it either by mounting or extracting the ISO

```cmd
dism /apply-image /ImageFile:path\to\install.wim /index:1 /ApplyDir:X:\
```

### Check what type of panel you have

> Open cmd

```cmd
adb shell panel
```

### Install Drivers

Unpack the Drivers archive you've downloaded earlier and run the `OfflineUpdater_<paneltype>.cmd` script
> When it asks you for the drive letter, enter X:
  

### Create Windows bootloader files

```cmd
bcdboot X:\Windows /s Y: /f UEFI
```



### Unassign disk letters
  
> So that they don't stay there after disconnecting the device

```cmd
diskpart
```


#### Select the Windows volume of the phone
> Use `list volume` to find it, it's the one named "WINVAYU"

```diskpart
select volume <number>
```

#### Unassign the letter X
```diskpart
remove letter x
```

#### Select the ESP volume of the phone
> Use `list volume` to find it, it's the one named "ESPVAYU"

```diskpart
select volume <number>
```

#### Unassign the letter Y

```diskpart
remove letter y
```

#### Exit diskpart
```diskpart
exit
```

## Boot into Windows

### Move the `<uefi.img>` file to the device

```cmd
adb push <uefi.img> /sdcard
```


### Make a backup of your existing boot image

> You need to do it now and also after every ROM update.

- To do this, go to the backup menu in TWRP

- Select Boot, and make sure the Internal Storage (or SD if possible) is selected for the backup destination

- Swipe!

### Flash the uefi image from TWRP
Navigate to the `uefi.img` file and flash it into boot

## Boot back into Android
> Use your backup boot image from TWRP

## Finished!
