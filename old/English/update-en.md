<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Running Windows on the POCO X3 Pro

## Updating Drivers

### Prerequisites
- [Recovery image](https://github.com/woa-vayu/POCOX3Pro-Guides/releases/tag/Recoveries)

- [UEFI image](https://github.com/woa-vayu/msmnilePkg/releases/latest)

- [Drivers](https://github.com/woa-vayu/Vayu-Drivers/releases/latest)

### Boot into TWRP
> If your recovery has been replaced by the stock recovery, flash it again using
```cmd
fastboot flash recovery <recovery.img> reboot recovery
```

#### Activate mass storage mode
> If it asks you to run it once again, do so
```cmd
adb shell msc
```

### Diskpart
```cmd
diskpart
```

#### Select the Windows volume of the tablet
> Use `list volume` to find it, it's the one named **WINVAYU**
```diskpart
select volume <number>
```

#### Assign the letter X
```diskpart
assign letter x
```

#### Exit diskpart
```diskpart
exit
```

### Installing drivers
Unpack the Drivers archive you've downloaded earlier and run the `OfflineUpdater.cmd` script
> When it asks you for the drive letter, enter **X**
  
### Reboot to fastboot to flash UEFI
> You can also use the WOA Helper app, in which case you can reboot with ```adb reboot```
>
> Make sure you use the latest UEFI, because Windows might not boot if you update drivers without updating the UEFI
```cmd
adb reboot bootloader
```

#### Boot with Windows bootable UEFI image
> Replace <uefi.img> with the actual path of the UEFI image
```cmd
fastboot flash boot <uefi.img>
```
## Finished!

















