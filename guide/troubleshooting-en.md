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

## Cannot mount the win partition in Android or WoA Helper doesn't work

- You may encounter an error when trying to mount the win partition
- "The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Falling back to read-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully (no hibernation or fast restarting.)
Could not mount read-write, trying read-only"

- If you have windows installed you have an "unclean file system"
- An unclean file system happens when windows is put in a hibernation state or you've done a force reboot
- To fix this simply reboot into windows and **REBOOT** from windows **NOT SHUTDOWN**
