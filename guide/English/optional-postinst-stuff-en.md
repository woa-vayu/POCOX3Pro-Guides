<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Running Windows on the POCO X3 Pro

## Optional post-install stuff

### Provisioning sensors

#### Prerequisites

- [Modded TWRP/OFOX](../../../../releases/Recoveries)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

##### Flash and boot modded recovery

```fastboot flash <recovery.img> reboot recovery```

##### Mounting partitions

- Go to the mount menu
- Mount the partitions persist and win

##### Provision sensors

###### Start ADB Shell

```adb shell```

###### Remove any Qualcomm remnants

```rm -rf /win/Windows/System32/drivers/DriverData/QUALCOMM/fastRPC/persist/sensors```

###### Copy sensor data over

```cp -r /persist/sensors /win/Windows/System32/drivers/DriverData/QUALCOMM/fastRPC/persist/sensors```

## Finished!
