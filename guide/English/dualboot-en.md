<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">

# Running Windows on the POCO X3 Pro

## Dualbooting Android and Windows seamlessly

### Prerequisites
- ```Brain```
- ```A rooted phone```
- ```Windows installed on the phone```
- [```NTFS Android Magisk Module```](https://github.com/woa-vayu-archive/Port-Windows-11-POCO-X3-Pro/releases/tag/ntfsdroid)
- [```UEFI image```](https://github.com/woa-vayu/msmnilePkg/releases/latest)
- [```Windows on Android Helper APK```](https://github.com/woa-vayu/WoA-Helper-M3K/releases/latest)
- [```StA Installer```](https://github.com/woa-vayu-archive/Port-Windows-11-POCO-X3-Pro/releases/tag/dualboot)

## Setting up the dualboot app
> This guide assumes you are rooted, if you aren't, please install Magisk

### Setup - Android
- Download and install the WoA Helper app, then open it and grant it root access.
- Download the **UEFI image** and place it inside the folder named `UEFI` in your internal storage.
- Press the `Mount Windows` button, then download and move **StA_Installer_vayu.exe** to the newly created `Windows` folder in your internal storage.
- Return to the WoA Helper app and press `QuickBoot to Windows`.
  
> [!NOTE]
> The first Windows boot can take up to 10 minutes, don't worry and just wait

### Setup - Windows
- Navigate to `C:\StA_Installer_vayu.exe` and run it. If it doesn't work, make sure that any antivirus software is off, as it will probably not let the app run

#### Booting to Android
- Run the new shortcut on your desktop (you can also pin it to your start menu / taskbar for ease of access)

#### Booting to Windows
- Press `QuickBoot to Windows` inside the app, or use the newly created toggle in your quick settings panel
  
## Finished!
