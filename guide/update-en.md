<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Running Windows on the POCO X3 Pro

## Driver updating

### Prerequisites
- A brain
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

### Check what type of panel you have

> Open cmd

```cmd
adb shell panel
```

### Install Drivers

Unpack the Drivers archive you've downloaded earlier and run the `OfflineUpdater_<paneltype>.cmd` script
> When it asks you for the drive letter, enter X:
  


### Boot with Windows bootable UEFI image

```
fastboot flash boot <uefi.img>
```

## Finished!
