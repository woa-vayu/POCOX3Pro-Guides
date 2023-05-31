<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Running Windows on the POCO X3 Pro

## Optional post-install stuff

### Provisioning the sensors

#### Prerequisites

- [Modded TWRP/OFOX](../../../../releases/Recoveries)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

##### Flash and boot modded recovery

```fastboot flash recovery <recovery.img> reboot recovery```

##### Mounting partitions

- Go to the mount menu
- Mount the partitions persist and win

##### Provisioning the sensors

###### Start ADB Shell

```adb shell```

###### Remove any Qualcomm remnants

```rm -rf /win/Windows/System32/drivers/DriverData/QUALCOMM/fastRPC/persist/sensors```

###### Copy sensor data over

```cp -r /persist/sensors /win/Windows/System32/drivers/DriverData/QUALCOMM/fastRPC/persist/sensors```

## Finished!


### Provisioning the modem manually

> **Warning** You will need to do this every time before you boot windows if you want LTE!

#### Prerequisites

- [Modded TWRP/OFOX](../../../../releases/Recoveries)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

##### Flash and boot modded recovery

```fastboot flash recovery <recovery.img> reboot recovery```

##### Mounting partitions

- Go to the mount menu
- Mount the partition win

##### Provisioning the modem

###### Start ADB Shell

```adb shell```

###### Finding the modem folder

> Take note of the random data in that folder name (after qcremotefs8150)

```ls /win/Windows/System32/DriverStore/FileRepository/ | grep qcremotefs8150```

###### Delete any previous modem files if they exist

> If you get any error about the files not existing, it's fine

> Make sure you replace the random data with the data you notes down at the previous step

```rm -rf /win/Windows/System32/DriverStore/FileRepository/qcremotefs8150_[insert random data here]/boot*```

###### Dump modem data

> Just like before, replace the random data with the one that you noted down before

> Make sure you do BOTH commands

```dd if=/dev/block/by-name/modemst1 of=/win/Windows/System32/DriverStore/FileRepository/qcremotefs8150_[insert random data here]/bootmodem_fs1```

```dd if=/dev/block/by-name/modemst2 of=/win/Windows/System32/DriverStore/FileRepository/qcremotefs8150_[insert random data here]/bootmodem_fs2```

## Finished!


### Making the keyboard float

> **Warning** Make sure these steps are done on the POCO X3 Pro running windows!

##### Opening the command prompt

- Go to the start menu
- Search command prompt
- Hold the command prompt application and run it as administrator
- Approve any UAC dialogs

##### Making the keyboard float

- In the command prompt put ```reg delete HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\Scaling /v MonitorSize```
- Press 'y' then enter
- Reboot your phone

## Finished!


### Disabling USB Host mode

> **Warning** Any non powered hub will STOP working!

> **Warning** Make sure these steps are done on the POCO X3 Pro running windows!

##### Opening the command prompt

- Go to the start menu
- Search command prompt
- Hold the command prompt application and run it as administrator
- Approve any UAC dialogs

##### Disabling USB host mode

- In the command prompt put ```reg add "HKLM\SYSTEM\CurrentControlSet\Enum\ACPI\QCOM0597\0\Device Parameters" /v RoleSwitchMode /t REG_DWORD /d 3```
- Reboot your phone

## Finished!
