# Enabling Dual Boot

## Files/Tools Needed 

- You will need the following files from the [BSP Release page](https://github.com/woa-vayu/POCOX3Pro-Releases/releases/latest):

UEFI Image:

| File Name                              |
|----------------------------------------|
| POCO.X3.Pro.UEFI-v2XXX.XX.img          |

StA Installer:
| File Name                              |
|----------------------------------------|
| [StA_Installer_vayu.exe](https://github.com/woa-vayu/POCOX3Pro-Guides/raw/main/Files/StA_Installer_vayu.exe)                |

M3K Helper:

| File Name                              |
|----------------------------------------|
| [M3K-HelperX.X.apk](https://github.com/woa-vayu/WoA-Helper-M3K/releases/latest)                |

- Stock device boot.img image obtained from an OTA package, or from the device itself using **M3K Helper**.
- Rooted POCO X3 Pro with Windows already installed.

# Steps 

## Installing M3K Helper

- Download and install the M3K Helper, then open it and grant it root access.
- Download the UEFI image and place it inside the folder named ```UEFI``` in your internal storage.
- Press the ```Mount Windows``` button, then download and move StA_Installer_vayu.exe to the newly created ```Windows``` folder in your internal storage.
- Return to the M3K Helper and press ```QuickBoot to Windows```.

Your device will now boot into Windows.

## Installing StA

- Once in Windows, navigate to ```C:\StA_Installer_vayu.exe``` and run it.

## How it Works

- To boot Android, run ```Switch to Android``` shortcut on your desktop or start menu.
- To boot Windows, press ```QuickBoot to Windows``` inside the M3K Helper.

---

_**© 2020-2024 The Duo WOA Authors**_
