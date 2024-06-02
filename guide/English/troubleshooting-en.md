<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2PocoX3ProWindows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Running Windows on the POCO X3 Pro

## Troubleshooting Issues

## I can't move files to the Windows folder from Android 

 If you are unable to move files to the Windows folder, it means you shut down Windows instead of restarting it. To fix this issue, boot back to Windows and use restart, then as it restarts boot to fastboot and use it to return to Android

## Charging in Windows does not work
> [!WARNING]
> Do not use a powered USB hub with host mode enabled, this can potentially break your device. If you use a powered USB hub, please use the [disable USB host mode guide](/guide/English/additional-materials-en.md#disabling-usb-host-mode)

Charging in Windows only works on specific cables. Cables that have been known to work are the original Poco X3 Pro cable (identified by the additional orange/red pin in the USB-A port), and the Nimaso 100W USB-C to USB-C fast charging cable.


## Device can boot into Android but not bootloader

### Prerequisites:

- [Android platform tools](https://developer.android.com/studio/releases/platform-tools)


This is caused by partitions with volume names the bootloader cannot handle, to fix this:

- Boot to recovery

- Connect tablet to PC

- Open platform tools cmd on PC

- Run ```adb shell```

- Run ```parted```

- Run ```print``` to list all partitions

- Look for partitions that have spaces in the names e.g "Basic Data Partition" and note their volume number

- Now run ```rm <vol number>``` e.g ```rm 36```


## Touchscreen touches are inaccurate/upside down

You picked the wrong definitions file while installing drivers.
