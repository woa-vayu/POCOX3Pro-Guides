<img align="right" src="https://github.com/woa-vayu-archive/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">

# Running Windows on the POCO X3 Pro

## Partitioning your device

### Prerequisites
- Unlocked bootloader

- Brain
  
- [Recovery Image](https://github.com/woa-vayu-archive/POCOX3Pro-Guides/releases/tag/Recoveries)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

### Notes
> [!Warning]
> All your data will be erased! Back up now if needed.
> 
> DO NOT REBOOT YOUR PHONE if you think you made a mistake, ask for help in the [Telegram chat](https://t.me/winonvayualt).

> [!IMPORTANT]
> Make sure you use the MODDED TWRP Recovery throughout this whole tutorial as we provide tools to help aid this installation process and make it as easy as possible for you.
> 
> If you don't use it and you face any errors, consider it your fault and consider yourself alone if you try asking for support as you have deferred from the main guide.

> [!NOTE]
> Don't know how to start? Unzip the downloaded [```Android platform tools```](https://developer.android.com/studio/releases/platform-tools), then open ```command prompt``` or `powershell` as administrator and run the following command, replacing `"path\to\platform-tools"` with the actual path of the platform tools folder
```cmd
cd "path\to\platform-tools"
```
> Use this window throughout the entire guide. Do not close it.

### Flash the modified TWRP recovery
> Replace `<recovery.img>` with the actual path to the recovery image
```cmd
fastboot flash recovery <recovery.img> reboot recovery
```

#### Run the partitioning script
> Replace **$** with the amount of storage you want Windows to have (do not add GB, just write the number)
> 
> If it asks you to run it once again, do so
```cmd
adb shell partition $
```

### Check if Android still starts
Just restart the phone, and see if Android still works
```cmd
adb reboot
```
## [Next step: Installing Windows](/guide/English/install-2-en.md)





















