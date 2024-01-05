<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Running Windows on the POCO X3 Pro

## Reinstallation

## Reinstalling Windows

### Prerequisites
- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)
- [Modified TWRP](../../../releases/Recoveries) (should already be installed)

#### Boot into TWRP
> If MIUI has replaced your recovery, boot to fastboot and run
```cmd
fastboot flash recovery path\to\twrp.img reboot recovery
```

#### Formatting the Windows partition
```cmd
adb shell format
```

## [Next step: Reinstalling Windows](/guide/install-2-en.md)
  
