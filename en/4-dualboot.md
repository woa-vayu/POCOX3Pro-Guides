# Dualboot guide

## Prerequisites

- [UEFI image](https://github.com/woa-vayu/POCOX3Pro-Releases/releases/latest)

- [M3K Helper](https://github.com/woa-vayu/WoA-Helper-M3K/releases/latest)

- [StA Installer](https://github.com/woa-vayu/POCOX3Pro-Guides/raw/main/Files/StA_Installer_vayu.exe)

## Dualboot guide

This guide assumes you are rooted, if you aren't, please follow [this guide](root.md) first.

## Setup - Android

- Download and install the M3K Helper, then open it and grant it root access.
- Download the UEFI image and place it inside the folder named ```UEFI``` in your internal storage.
- Press the ```Mount Windows``` button, then download and move StA_Installer_vayu.exe to the newly created ```Windows``` folder in your internal storage.
- Return to the M3K Helper and press ```QuickBoot to Windows```.

Your device will now boot into Windows.

### Setup - Windows
>
> [!Tip]
> If this is your first time booting Windows and you wish to skip the Microsoft Account login, press the **I don't have internet** button in the WiFi page, then when prompted, press the **Continue with limited setup** button.

- Once in Windows, navigate to ```C:\StA_Installer_vayu.exe``` and run it.

#### Booting to Android

- Run the new shortcut on your desktop (you can also pin it to your start menu / taskbar for ease of access)

#### Booting to Windows

- Press **QUICKBOOT TO WINDOWS** inside the app, or use the newly created toggle in your quick settings panel

> [!Important]
> If you ever update or change your Android ROM, make sure to create a new **boot.img** backup (after rooting your phone!) and place it inside the **C:\folder** in Windows, overwriting the old file.
>
> You can use the **BACK UP BOOT IMAGE** feature in the WOA Helper app to do so.

## Finished
