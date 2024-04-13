<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Running Windows on the POCO X3 Pro

## Optional post-install stuff

### Provisioning the modem

> [!WARNING]  
> You will need to do this every time before you boot Windows if you want LTE!

> [!NOTE]
> You don't have to do this if you're using WoA Helper

#### Provisioning the modem mostly automatically (faster/easier method)

#### Prerequisites
- Magisk or TWRP installed
- [Modem provisioning zip](https://github.com/woa-vayu/Port-Windows-11-POCO-X3-Pro/releases/tag/modemprov)

##### Flash the modem provisioning zip

> This is very self explanatory, open Magisk (or TWRP), install zip that does the hard work for you

- Open Magisk (or boot TWRP)
- Go to the Modules section ("Install" button in TWRP)
- Flash the zip
- Boot into Windows

## Finished!

#### Provisioning the modem manually (longer/harder method)

#### Prerequisites

- [Modified TWRP](../../../releases/Recoveries)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

##### Flash and boot modded recovery

> This is self explanatory, it flashes the recovery then reboots into the recovery

```fastboot flash recovery path\to\twrp.img reboot recovery```

##### Mounting partitions

> Also self explanatory, this will mount the windows partitions

- Go to the mount menu
- Mount the partition win

##### Start ADB Shell

> Starts a shell on your computer used to communicate with your phone over ADB

```adb shell```

##### Finding the modem folder

> Take note of the random data in that folder name (after qcremotefs8150)

> This looks for the Qualcomm remotefs driver folder

```ls /win/Windows/System32/DriverStore/FileRepository/ | grep qcremotefs8150```

##### Dump modem data

> Just like before, replace the random data with the one that you noted down before

> Make sure you do BOTH commands

> This dumps your modem data into the remote fs folder, ultimately fixing the modem

```dd if=/dev/block/by-name/modemst1 of=/win/Windows/System32/DriverStore/FileRepository/qcremotefs8150_[insert random data here]/bootmodem_fs1```

```dd if=/dev/block/by-name/modemst2 of=/win/Windows/System32/DriverStore/FileRepository/qcremotefs8150_[insert random data here]/bootmodem_fs2```

## Finished!




### Making the keyboard float

> [!WARNING]  
> Make sure these steps are done on the POCO X3 Pro running Windows!

##### Opening the command prompt as an administrator

> This is self explanatory, this opens the command prompt as administrator

- Go to the start menu
- Search command prompt
- Hold the command prompt application and run it as administrator
- Approve any UAC dialogs

##### Making the keyboard float

> This deletes the registry key that tells the keyboard the size of our screen and makes it float again

- In the command prompt put ```reg delete HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\Scaling /v MonitorSize```
- Press 'y' then enter
- Reboot your phone

## Finished!




### Disabling USB Host mode

> [!WARNING]
>  Any non powered hub will STOP working!
>
> Make sure these steps are done on the POCO X3 Pro running Windows

Run [USB Host Control script](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/download/USBHost/USB.Host.Mode.Control.V6.0.vbs) to enable/disable USB host mode and  confirm that you want to disable/enable USB host mode 

#### Finished!



### Hiding the D: drive (modem partition)
> [!NOTE]
> This is recommended because this drive should not be modified, while some applications may try to write to it

- Open a command prompt and run ```diskpart```
- Then run ```list volume``` to see all available volumes
- Select the disk that has letter D with ```select volume $```, replacing "$" with the volume number
- Remove the letter with ```remove letter d```
- Now exit diskpart with ```exit```

## Finished!



