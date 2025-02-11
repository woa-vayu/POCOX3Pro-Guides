# Installing Windows on your POCO X3 Pro without a PC

### Prerequisites
- A rooted POCO X3 Pro

- Modified TWRP:

| File Name                                       | Android version |
|-------------------------------------------------|-----------------|
| [twrp-3.7.1_12-vayu.img](https://github.com/woa-vayu/POCOX3Pro-Guides/raw/main/Files/twrp-3.7.1_12-vayu.img) | Android 12/12.1/13/14 |
| [twrp-3.7.0_11-vayu.img](https://github.com/woa-vayu/POCOX3Pro-Guides/raw/main/Files/twrp-3.7.0_11-vayu.img) | Android 11 |

- [Termux](https://play.google.com/store/apps/details?id=com.termux) (only if you do not have any custom recovery installed)

- [Latest Vayu firmware](https://xmfirmwareupdater.com/firmware/vayu/)

- [Vayu WinInstaller](https://github.com/Kumar-Jy/WinInstaller/releases/tag/Vayu_WinInstaller)

- [Windows on ARM image](https://arkt-7.github.io/woawin/)

- [WOA Helper app](https://github.com/n00b69/woa-helper/releases/tag/APK)

### Notes
> [!WARNING]  
> All your data will be erased! Back up now if needed.
> 
> DO NOT REBOOT YOUR PHONE if you think you made a mistake, ask for help in the [Telegram chat](https://t.me/winonvayualt).

### Flash the modified TWRP
> If you have a custom recovery installed, you can install the modified TWRP through there instead
- Download the modified TWRP, rename it to **TWRP.img**, and leave in the `Download` folder **of your internal storage**.
- Download **Termux**, open it, and grant it root access.
- Run the below command in Termux to flash TWRP:
```cmd
su -c dd if=/sdcard/Download/TWRP.img of=/dev/block/by-name/recovery
```
- Run the below command in Termux to reboot into TWRP:
```cmd
su -c reboot recovery
```

#### Opening TWRP terminal
- Once booted into TWRP, decrypt data by entering your password if it asks you to.
- Press the **Advanced** button on the bottom right of the screen, then press **Terminal**

### Run the partitioning script
> Replace **$** with the amount of storage you want Windows to have (do not add GB, just write the number)
> 
> If it asks you to run it once again, do so
```cmd
partition $
```

### Check if Android still starts
- Just restart the phone, and see if Android still works

### Preparing necessary files
- Download the Windows image and make sure it remains in the `Download` folder **of your internal storage**, NOT SD card.
> [!Important]
> For performance reasons, it is recommended to use Windows 11 24H2 (builds that start with 261XX, such as 26100.2454)

- Download **WinInstaller** and leave it in your internal storage.
- Download the **vayu firmware.zip** and leave it in your internal storage.
- Download and install the [WOA Helper app](https://github.com/n00b69/woa-helper/releases/tag/APK), then open it and grant it root access. Do not do anything else inside the app yet.
- Reboot to the modified TWRP. Flash it again if it has been replaced by MIUI recovery.

### Flashing WinInstaller
- In TWRP, select **Install** and then locate **vayu firmware.zil** and flash it.
- After it flashed the firmware, do not reboot. Instead, also flash **WinInstaller.zip**.
- Wait until all processes complete and your device boots into Windows. This will take around 15-20 minutes.

> [!Tip]
> If you wish to skip the Microsoft Account login, press the **I don't have internet** button in the WiFi page, then when prompted, press the **Continue with limited setup** button.
>
> If there is no such button, press the **SIM card** button at the top of the screen (the one that says **Connected**), and press **Disconnect**.

#### Booting to Android
- Run the **Android** shortcut on your desktop (you can also pin it to your start menu / taskbar for ease of access).

#### Booting to Windows
- Press **QUICKBOOT TO WINDOWS** inside the WOA Helper app, or use the newly created toggle in your quick settings panel.

## Finished!















