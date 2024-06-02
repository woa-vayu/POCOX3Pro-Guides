<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2PocoX3ProWindows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">

# Running Windows on the POCO X3 Pro

## Uninstallation

### Why is this needed?
If you want to uninstall Windows, this is used instead of deleting partitions manually to avoid human error + writing a whole dedicated guide to just uninstalling.

If you want to relock your bootloader you'll need your partition table to be stock.

### Prerequisites
- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)
  
- [Recovery Image](https://github.com/woa-vayu-archive/Port-Windows-11-POCO-X3-Pro/releases/tag/Recoveries)

### Flash and boot modified recovery
> Replace `<recovery.img>` with the actual path to the recovery image
```cmd
fastboot flash recovery <recovery.img> reboot recovery
```

#### Restore the partition layout
> [!Warning]
> This will wipe your Android files. Backup first if needed.
```cmd
adb shell restore
```

### Reboot to Android 
```cmd
adb reboot 
```

## Done!






















