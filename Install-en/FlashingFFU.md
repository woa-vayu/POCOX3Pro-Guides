# Flashing a Full Flash Update Image (.FFU) on POCO X3 Pro

This guide will help you flash a FFU file containing Windows on your POCO X3 Pro.

You will end up with both Android and Windows on your POCO X3 Pro.

Android and Windows will both split the internal storage according to the configuration contained within the FFU file.

Android will boot normally, and you will have to use a PC to boot Windows when needed, unless you create a follow a dualboot guide (explained later).

Table of Contents:

* [Flashing a Full Flash Update Image (.FFU) on POCO X3 Pro](#flashing-a-full-flash-update-image-ffu-on-poco-x3-pro)
   * [Files/Tools Needed](#filestools-needed-)
* [Steps](#steps-️)
   * [Unlocking the Bootloader](#unlocking-the-bootloader)
   * [Acquiring all files](#acquiring-all-files)
   * [Install WOA Device Manager](#install-woa-device-manager)
   * [Getting to FFU Loader](#getting-to-ffu-loader)
   * [Flashing the Windows FFU Image](#flashing-the-windows-ffu-image)
   * [Boot Windows](#boot-windows-)
   * [Boot Windows again after initial installation](#boot-windows-again-after-initial-installation)

## Files/Tools Needed 

- [WOA Device Manager](https://github.com/woa-vayu/POCOX3Pro-Guides/releases/download/WDM/WOA_Device_Manager.zip)
- An FFU file for POCO X3 Pro
- A Windows PC to flash the device

## Disclaimers

> [!WARNING]
> - If you see a warning and/or error during the process, it is not normal. Contact us on telegram if you see anything odd, but do not continue or proceed on your own, you will break things further.

> [!IMPORTANT]
> **THIS WILL WIPE ALL YOUR ANDROID DATA AND WINDOWS DATA!**
>
> We don't take any responsibility for any damage done to your phone. By following this guide, you agree to take full responsibility of your actions. We have done some testing,
>
> but this is **STILL IN PREVIEW** and things can go wrong.

**PLEASE READ AND BE SURE TO UNDERSTAND THE ENTIRE GUIDE BEFORE STARTING**

# Steps 

## Unlocking the Bootloader

If not already done, please first unlock the bootloader. Come back once you're done. If you already did this, please skip this section.

## Acquiring all files

UEFI:
- [UEFI Image](https://github.com/woa-vayu/POCOX3Pro-Releases/releases/download/2408.19/POCO.X3.Pro.UEFI-v2408.19.img)

[FFU Files](https://t.me/woavayuffu)

## Install WOA Device Manager

| Steps | Illustration |
|-|-|
| Download [WOA Device Manager](https://github.com/woa-vayu/POCOX3Pro-Guides/releases/download/WDM/WOA_Device_Manager.zip) | |
| Extract it | |
| Double tap the ```Install.cmd``` file | |
| Follow the on screen instructions. | |
| Open WOA Device Manager. | <img align="right" width="425" alt="Screenshot 2024-06-22 183133" src="https://github.com/woa-vayu/POCOX3Pro-Guides/assets/69907487/42be9ce4-2f28-4a36-af40-8ce57243aebc">

Congratulations, you successfully installed WOA Device Manager.

## Getting to FFU Loader

| Steps | Illustration |
|-|-|
| Plug your device into your computer inside Android | <img align="right" width="425" alt="Screenshot 2024-06-22 183159" src="https://github.com/woa-vayu/POCOX3Pro-Guides/assets/69907487/9c610f45-4df3-463b-8aae-efde82a4108a"> |
| Go into the Manual Mode Section of WOA Device Manager | <img align="right" width="425" alt="Screenshot 2024-06-22 183227" src="https://github.com/woa-vayu/POCOX3Pro-Guides/assets/69907487/90ea2b5c-c996-4e28-a3c5-3a343c8fbf82"> |
| Click "Switch to Windows-mode" | <img align="right" width="425" alt="Screenshot 2024-06-22 183235" src="https://github.com/woa-vayu/POCOX3Pro-Guides/assets/69907487/f4c6ed5f-572f-4a36-8fcd-0bfae2dd8af6"> |
| When the device shows the "FASTBOOT" text on its screen, Press the Volume Up Key on the side of your device til you see something like shown below on screen: | <img align="right" width="425" alt="Screenshot 2024-06-22 183302" src="https://github.com/woa-vayu/POCOX3Pro-Guides/assets/69907487/8b8d8598-1164-4f07-b421-88e147dbd4e8"> |
| WOA Device Manager will detect your device in UFP mode | <img align="right" width="425" alt="Screenshot 2024-06-22 183302" src="https://github.com/woa-vayu/POCOX3Pro-Guides/assets/69907487/21d3cf3c-1090-491b-9ba4-97a79156591f"> |

> [!TIP]
> In case the PC complains the device was not found, try using an USB-2 port there are known issues with the UEFI that prevent device from being recognized via USB-3 port.

Congratulations, you're now in FFU Loader.

## Flashing the Windows FFU Image

| Steps | Illustration |
|-|-|
| Go to the Flash Section of WOA Device Manager | <img align="right" width="425" alt="Screenshot 2024-06-22 183326" src="https://github.com/woa-vayu/POCOX3Pro-Guides/assets/69907487/f4c0f9fb-8ce7-408e-82ec-570860bf8be7"> |
| Pick your FFU File, and click "Flash FFU Image" | <img align="right" width="425" alt="Screenshot 2024-06-22 183344" src="https://github.com/woa-vayu/POCOX3Pro-Guides/assets/69907487/9f200e51-00bf-4950-a998-4343f68fdb75"> |
| You should now see the device flashing on both your computer | <img align="right" width="425" alt="Screenshot 2024-06-22 183429" src="https://github.com/woa-vayu/POCOX3Pro-Guides/assets/69907487/3a643ab4-680f-4a8e-ac55-2d80de357b51"> |
| and on the device, wait til the process is complete. | <img align="right" width="425" alt="POCO X3 Pro in FFU Loader mode, flashing" src="https://github.com/woa-vayu/POCOX3Pro-Guides/assets/69907487/37ab28cd-4f69-4288-bfc7-a6a7f476aa9b"> |
| Wait til the process is finished, and you should be back into Android or Recovery. | |

> [!IMPORTANT]
> **DO THIS ONLY IF IT'S YOUR FIRST TIME INSTALLING FFU**
>
> If this is your first time flashing this FFU file, or you're flashing a different storage or layout configuration image, you will lose all of your Android data. Further more, you will also not have Android boot successfully.
If this isn't your case, feel free to ignore this section, Android should still boot fine.
If this is your case, then please boot into stock recovery and do a "Factory Reset" or boot into TWRP and format Data.
>

## Boot Windows 

| Steps | Illustration |
|-|-|
| Inside WOA Device Manager, go to switch mode | <img align="right" width="425" alt="Screenshot 2024-06-22 183227" src="https://github.com/WOA-Project/SurfaceDuo-Guides/assets/3755345/a5fb15b1-6a43-45b5-b440-df243b076b9c"> |
| and select "Switch to Windows-mode". | <img align="right" width="425" alt="Screenshot 2024-06-22 183235" src="https://github.com/WOA-Project/SurfaceDuo-Guides/assets/3755345/bb4f618a-fa7c-4874-8dd6-f87181753be6"> | 

This step above will be needed every time you will want to boot Windows and needs to be done from the Bootloader mode.

If you did everything right, Windows will now boot! Enjoy!

Let Windows set itself up, and come back once you're on the Windows Desktop on your POCO X3 Pro

> [!NOTE]
> If the Touch keyboard won't show up in OOBE, touch somewhere else (to let the text box loose focus) and then touch into the text box again. As an alternative, you can use the On-Screen Keyboard.

> [!NOTE]
> If you get a BSOD (bugcheck screen) during initial setup, you can try erasing both the esp and win partitions using "fastboot erase esp" and "fastboot erase win", and reflash the FFU file, then it should work. This issue will get fixed in later FFU revisions.

## Boot Windows again after initial installation

You'll have two methods of booting Windows.

- Manual booting with a PC
    - Pros: You can freely update Android
    - Cons: You will need a PC to boot to Windows

- Enabling Dual Boot
    - Pros: You'll be able to boot Windows directly from the device

In case you want the dual boot option, then follow [this guide](/Install-en/DualBoot.md)
