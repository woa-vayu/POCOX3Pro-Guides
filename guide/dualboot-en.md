<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Running Windows on the POCO X3 Pro

## Dualbooting Android and Windows seamlessly

### Prerequisites
- [Magisk](https://github.com/topjohnwu/Magisk/releases/latest)
- [UEFI](https://github.com/woa-vayu/msmnilePkg/releases/latest)
- [Windows on Android Helper APK](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/download/dualboot/woahelper.apk)
- [StA Installer](../../../releases/dualboot)

### Setup - Android
> [!NOTE]
> If you are unable to move files to the Windows folder, it means you shut down Windows instead of restarting it. To fix this issue, boot back to Windows and use restart, then as it restarts boot to fastboot and use it to return to Android

- Download and install the WOA Helper app, then open it and grant it root access.
- Download the UEFI image and place it inside the folder named `UEFI` in your internal storage, if this folder does not exist, create it.
- Return to the WOA Helper app and press the `Back up Android boot` button. Select both the `Windows` and `Android` options.
- Press the `Mount Windows` button, then download and move StA_Installer_vayu.exe to the newly created `Windows` folder in your internal storage.
- Return to the WOA Helper app and press `Quickboot to Windows`.

### Setup - Windows
- Navigate to `C:\StA_Installer_vayu.exe` and run it. If it doesn't work, make sure that any antivirus software is off, as it will probably not let the app run

##### Booting to Android
  - Run the new shortcut on your desktop (you can also pin it to your start menu / taskbar for ease of access)

##### Booting to Windows
  - Press `Quickboot to Windows` inside the app, or use the newly created toggle in your quick settings panel

  
## Finished!
