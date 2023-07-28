<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Running Windows on the POCO X3 Pro

## Uninstallation

### Why is this needed?

If you have followed the old guide your partition order will be too different and may have some consequences if you dont restore your stock partition table.

If you want to uninstall windows this is used instead of deleting partitions manually to avoid human error + writing a whole dedicated guide to just uninstalling.

If you want to relock your bootloader you'll need your partition table to be stock.

### Prerequisites

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)
- [gpt_both0.bin](../../../releases/tag/binaries) (old method)
- [Modded TWRP/OFOX](../../../releases/Recoveries) (new method)

#### New method

##### Flash and boot modified recovery

```cmd
fastboot flash recovery path\to\twrp.img 
fastboot reboot recovery
```

##### Execute the restore script

```cmd
adb shell restore
```

##### Done!

#### Old method (in case the new one didn't work)

##### Restore GPT
> Replace ```path\to\gpt_both0.bin``` with the path to the gpt_both0.bin file.

```cmd
fastboot flash partition:0 path\to\gpt_both0.bin
```

##### Erase userdata to avoid bootloop and restore FS size
```cmd
fastboot -w
```
