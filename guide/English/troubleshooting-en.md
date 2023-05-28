<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Running Windows on the POCO X3 Pro

## Troubleshooting Issues


## Device can boot into android but not bootloader

### Prerequisites:

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

This is caused by partitions with volume names the bootloader cannot handle, to fix this:

- Boot to recovery

- Connect phone to PC

- Open cmd on PC

- Run ```adb shell```

- Run ```parted```

- Run ```print``` to list all partitions

- Look for partitions that have spaces in the names e.g "Basic Data Partition" and note their volume number

- Now run ```rm <vol number>``` e.g ```rm 36```



## Touchscreen touches are inaccurate/upside down

You picked the wrong definitions file while installing drivers.
