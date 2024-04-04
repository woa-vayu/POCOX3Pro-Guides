<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Running Windows on the POCO X3 Pro

## Installation

## Partitioning your device

### Prerequisites
- ```Unlocked bootloader```

-  ```Brain```
  
- [```Recovery Image```](https://github.com/woa-vayu-archive/Port-Windows-11-POCO-X3-Pro/releases/tag/Recoveries)

- [```Android platform tools```](https://developer.android.com/studio/releases/platform-tools)

### Notes
> [!Warning]
> All your data will be erased! Back up now if needed.
> 
> DO NOT REBOOT YOUR PHONE if you think you made a mistake, ask for help in the [Telegram chat](https://t.me/winonvayualt).


> [!IMPORTANT]
> Make sure you use the MODDED TWRP Recovery throughout this whole tutorial as we provide tools to help aid this installation process and make it as easy as possible for you.
> 
> If you dont use it and you face any errors, consider it your fault and consider yourself alone if you try asking for support as you have deferred from the main guide.

### Partitioning your device and backup boot
> [!NOTE]
> Don't know how to start? Unzip the downloaded [```Android platform tools```](https://developer.android.com/studio/releases/platform-tools), then open ```command prompt``` or `powershell` as administrator and run the following command, replacing `"path\to\platform-tools"` with the actual path of the platform tools folder
```cmd
cd "path\to\platform-tools"
```
> Use this window throughout the entire guide. Do not close it.

##### Flash the modified TWRP recovery
```cmd
fastboot flash recovery <recovery.img> reboot recovery
```

#### Partitioning your device

> If it asks you to run it once again, do so

> This is **optional**, but you can also **set custom sizes (by default, it splits the storage in half)**

> To set custom sizes do ```adb shell partition [TARGET WINDOWS SIZE IN GB]```

> Make sure you do not add GB at the end, just the number

```cmd
adb shell partition
```


#### Check if Android still starts
> Reboot to check if Android still works. If it doesn't boot, wipe all data in recovery and try again.

```cmd
adb reboot
```


## [Next step: Installing Windows](/guide/English/install-2-en.md)
