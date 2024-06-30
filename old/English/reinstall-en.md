<img align="right" src="https://github.com/woa-vayu-archive/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Running Windows on the POCO X3 Pro

## Reinstallation
If you don't like your Windows version or you've bricked your Windows install, or anything else, you would probably just reinstall Windows. Thankfully this process is very easy.

> [!IMPORTANT]
> Quite obviously, this will erase all of your Windows files. If you'd like to back up any of them, you can do so by mounting Windows using the [WOA Helper](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/download/dualboot/woahelper.apk) app and manually copying any files you wish to keep


### Prerequisites

- ```Existing Windows and boot partitions``` (*If not met, [go back and just pretend this guide never existed](/guide/English/install-1-en.md)*)

- [```Recovery Image```](https://github.com/woa-vayu-archive/POCOX3Pro-Guides/releases/tag/Recoveries)

- [```Android platform tools```](https://developer.android.com/studio/releases/platform-tools)

#### Boot into TWRP
> If MIUI has replaced your recovery, boot to fastboot and run
```cmd
fastboot flash recovery <recovery.img> reboot recovery
```

### Format the partitions
> If it asks you to run it once again, do so
```cmd
adb shell format
```

## [Next step: Reinstalling Windows](/guide/English/install-2-en.md)
  
