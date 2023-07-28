<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Running Windows on the POCO X3 Pro

## Driver updating

### Prerequisites

- [UEFI](https://github.com/woa-vayu/edk2-msm/releases/latest)
- [Modded TWRP/OFOX](../../../releases/Recoveries)
- [DriverUpdater](https://github.com/WOA-Project/DriverUpdater/releases/latest)
- [Drivers](https://github.com/woa-vayu/Vayu-Drivers/releases/latest)

#### Start TWRP recovery through the PC with the command

```cmd
fastboot boot <twrp.img>
```

> If you already have TWRP installed, just hold the power and vol+ buttons at startup

> You will need to disable MTP in Mount
#### Execute script

```cmd
adb shell msc.sh
```

### Assign letters to disks

#### Start the Windows disk manager

> Once the X3 Pro is detected as a disk

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
assign letter=x
```

#### Exit diskpart
```diskpart
exit
```


### Check what type of panel you have

```cmd
adb shell cat /proc/cmdline
```
> Look for `msm_drm.dsi_display0` almost at the bottom

> If your device is `Tianma`, `msm_drm.dsi_display0` will be `dsi_j20s_36_02_0a_video_display`

> If your device is `Huaxing`, `msm_drm.dsi_display0` will be `dsi_j20s_42_02_0b_video_display`

### Install Drivers

> Replace `<vayudriversfolder>` with the actual location of the drivers folder
> Replace `<paneltype>` with the actual panel type (tianma/huaxing)

```cmd
.\driverupdater.exe -d <vayudriversfolder>\definitions\Desktop\ARM64\Internal\vayu_<paneltype>.txt -r <vayudriversfolder> -p X:
```


### Boot with Windows bootable UEFI image

```
fastboot flash boot <uefi.img>
```

## Finished!
