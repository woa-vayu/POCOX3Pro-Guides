# Reinstall Windows on your POCO X3 Pro

## Files/Tools Needed

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

Modified TWRP:

| File Name                                       | Android version |
|-------------------------------------------------|-----------------|
| [twrp-3.7.1_12-vayu.img](https://github.com/woa-vayu/POCOX3Pro-Guides/raw/main/Files/twrp-3.7.1_12-vayu.img) | Android 12/12.1/13/14 |

### Boot into TWRP
>
> If MIUI has replaced your recovery, boot to fastboot and run

```cmd
fastboot flash recovery path\to\twrp.img reboot recovery
```

#### Formatting the Windows partition

```cmd
adb shell format
```

## [Next step: Reinstalling Windows](/en/3-install.md)
