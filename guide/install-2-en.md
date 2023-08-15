<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Running Windows on the POCO X3 Pro

## Installation

## Installing Windows

### Prerequisites

- [Windows on ARM image (Windows 11 is recommended)](https://uupdump.net/)
- [UEFI image](https://github.com/woa-vayu/edk2-msm/releases/latest)
- [DriverUpdater](https://github.com/WOA-Project/DriverUpdater/releases/latest)
- [Drivers](https://github.com/woa-vayu/Vayu-Drivers/releases/latest)
- [Modified TWRP](../../../releases/Recoveries) (should already be installed)

#### Boot into TWRP

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
adb shell "dmesg | grep dsi_display_bind"
```
> If your panel is `Tianma`, it will show `dsi_j20s_36_02_0a_video_display`

> If your panel is `Huaxing`, it will show `dsi_j20s_42_02_0b_video_display`

### Install Drivers

> Replace `path\to\drivers` with the actual location of the drivers folder
> Replace `paneltype` with the actual panel type (tianma/huaxing)

```cmd
.\driverupdater.exe -d path\to\drivers\definitions\Desktop\ARM64\Internal\vayu_paneltype.txt -r path\to\drivers -p X:
```

  

### Create Windows bootloader files

```cmd
bcdboot X:\Windows /s Y: /f UEFI
```

  
  

## Allow unsigned drivers

> If you don't do this you'll get a BSOD

```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" testsigning on
```

### Unssign disk letters
  
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

#### if you have a microSD card use this

```cmd
adb push <uefi.img> /external_sd
```


### Make a backup of your existing boot image
> You need to do it just once

> Put it to the microSD card if possible


### Flash the uefi image from TWRP
Navigate to the `uefi.img` file and flash it into boot

## Boot back into Android
> Use your backup boot image from TWRP

## Finished!
