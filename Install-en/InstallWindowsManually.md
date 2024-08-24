# Install Windows on POCO X3 Pro

![POCO X3 Pro Windows](https://github.com/user-attachments/assets/355e74cd-dea9-460f-8db4-87f766cd3223)

Table of Contents:

* [Install Windows on POCO X3 Pro](#install-windows-on-surface-duo-1st-gen)
   * [Files/Tools Needed](#filestools-needed-)
* [Steps](#steps-️)
   * [Unlocking the Bootloader](#unlocking-the-bootloader)
   * [Partitioning](#partitioning)
   * [Booting to TWRP](#booting-to-twrp)
   * [Entering Mass Storage Mode](#entering-mass-storage-mode)
   * [Installing Windows](#installing-windows)
   * [Installing the drivers](#installing-the-drivers)
   * [Boot Windows](#boot-windows-)
   * [Boot Windows again after initial installation](#boot-windows-again-after-initial-installation)

## Files/Tools Needed 

- You will need the following files from the [BSP Release page](https://github.com/woa-vayu/POCOX3Pro-Releases/releases/latest):

UEFI Image:

| File Name                              |
|----------------------------------------|
| POCO.X3.Pro.UEFI-v2XXX.XX.img          |

Windows Drivers:

| File Name                                       |
|-------------------------------------------------|
| POCOX3Pro-Drivers-v2XXX.XX-Desktop.7z           |

TWRP image:

| File Name                                       | Android version |
|-------------------------------------------------|-----------------|
| [twrp-3.7.1_12-vayu.img](https://github.com/woa-vayu/POCOX3Pro-Guides/raw/main/Files/twrp-3.7.1_12-vayu.img) | Android 12/12.1/13/14 |
| [twrp-3.7.0_11-vayu.img](https://github.com/woa-vayu/POCOX3Pro-Guides/raw/main/Files/twrp-3.7.0_11-vayu.img) | Android 11 |

- [Platform Tools from Google (ADB and Fastboot)](https://developer.android.com/studio/releases/platform-tools)
- An ARM64 Windows build of your choice that meets the minimum system requirements (specifically the install.wim file). You can create it using [this guide](/Install-en/ISO/CreateISO.md). Or you can download it from [WoR Project](https://www.worproject.com/esd).
- A Windows PC to build the Windows ISO, apply it onto the phone from mass storage, add drivers to the installation, configure ESP

## Disclaimers

> [!WARNING]
> - Don't create partitions from Mass Storage Mode on Windows (because ABL will break with blank/spaces in names), your phone may be irrecoverable otherwise
> - If you see a warning and/or error during the process, it is not normal. Contact us on telegram if you see anything odd, but do not continue or proceed on your own, you will break things further.
> - Don't rerun the commands if you interrupt the process. You may break your partition table.
> - Do not run all commands at once.
> - Do not commit *any* typo with *any* commands.
> - Be familiar with command line interfaces.

> [!IMPORTANT]
> **THIS WILL WIPE ALL YOUR ANDROID DATA**
>
> We don't take any responsibility for any damage done to your phone. By following this guide, you agree to take full responsibility of your actions. We have done some testing,
>
> but this is **STILL IN PREVIEW** and things can go wrong.

**PLEASE READ AND BE SURE TO UNDERSTAND THE ENTIRE GUIDE BEFORE STARTING**

# Steps 

## Acquiring all files

Here's how to acquire a Driver archive file and the matching UEFI image for POCO X3 Pro:

<table>
<tr>
<td>Drivers File</td>
<td>UEFI File</td>
<td>Target Device</td>
<td>OS Version</td>
<td>Notes</td>
</tr>
<tr>
<td>

[POCOX3Pro-Drivers-v2408.19-Desktop.7z](https://github.com/woa-vayu/POCOX3Pro-Releases/releases/download/2408.19/POCOX3Pro-Drivers-v2408.19-Desktop.7z)
</td>
<td>

[POCO.X3.Pro.UEFI-v2408.19.img](https://github.com/woa-vayu/POCOX3Pro-Releases/releases/download/2408.19/POCO.X3.Pro.UEFI-v2408.19.img)
</td>
<td>POCO X3 Pro</td>
<td>Windows 10 Version 2004 and higher</td>
<td><details>

N/A
</details></td>
</tr>
</table>

<details>
    <summary>Here's how to acquire the Android SDK Platform Tools: <b>Click to expand</b></summary>
    <p>


First, start by going to the [Android Platform SDK download page](https://developer.android.com/studio/releases/platform-tools) on your computer.

![SDK-1-Top](https://github.com/WOA-Project/SurfaceDuo-Guides/assets/3755345/4c1c3762-24d8-4150-ac69-670738eb62c1)

Once on the page, scroll a little bit down til you see the link to download the platform tools for Windows.

![SDK-2-Mid](https://github.com/WOA-Project/SurfaceDuo-Guides/assets/3755345/cd14a232-4995-480f-a061-54507e83cf41)

Click on it, an EULA will open like below:

![SDK-3-EULA](https://github.com/WOA-Project/SurfaceDuo-Guides/assets/3755345/16d6b7df-ab56-414c-b1a5-561ec6b3ae4e)

Scroll all the way down (after reading it if that's your thing)

![SDK-4-EULA-Bottom](https://github.com/WOA-Project/SurfaceDuo-Guides/assets/3755345/1368b2b0-74b8-4a7c-9aff-df2ca25c2f42)

Tick "I have read and agree to above terms conditions"

![SDK-5-EULA-TICK (alt)](https://github.com/WOA-Project/SurfaceDuo-Guides/assets/3755345/02905fa2-64b8-426b-b42f-c1bb88eaa88a)

And click download

![SDK-5-EULA-TICK](https://github.com/WOA-Project/SurfaceDuo-Guides/assets/3755345/0983f27a-76e7-4fda-ac4d-adaa56702e90)

Save the file on your computer, and extract the zip file by opening it, and selecting extract all.

![SDK-6-DL](https://github.com/WOA-Project/SurfaceDuo-Guides/assets/3755345/adc1bba0-6118-418e-9005-e2db12860893)

  </p>
</details>

## Unlocking the Bootloader

If not already done, please first unlock the bootloader. Come back once you're done. If you already did this, please skip this section.

## Partitioning

If not already done, please proceed with the [Partitioning](Partitioning.md) guide for POCO X3 Pro. Come back once you're done. If you already followed this guide, please instead follow the [Reinstall Windows](ReinstallWindows.md) guide, not this one.

## Booting to TWRP

- Assuming you're inside Android run this command:

```batch
adb reboot recovery
```

You will now boot to TWRP.

## Entering Mass Storage Mode

- Let's run the mass storage shell script in order to boot into Mass Storage from recovery. You must decrypt your data if it asks you to.

```batch
adb shell msc
```

- If it asks you to run it once again, do so

Your POCO X3 Pro should now be in USB Mass Storage Mode.

## Installing Windows

- Make sure you are in Mass Storage Mode, that your POCO X3 Pro is plugged into your PC
- Mount the partitions you have created using diskpart and assign them some letters:

```batch
 THESE ARE NOT ALL COMMANDS. DISKPART COMMANDS VARY A LOT, SO THESE ARE SOME ROUGH INSTRUCTIONS.
ACTUAL COMMANDS START WITH AN HASHTAG (which you will need to remove)
YOU DO NOT HAVE TO USE THE LETTERS WE USE AT ALL!!!, THEY ONLY NEED TO BE FREE LETTERS. IF LETTERS DON'T ASSIGN FINE, USE ANOTHER ONE.
IF ONE PARTITION IS ALREADY ASSIGNED, YOU ALSO DO NOT NEED TO ASSIGN IT AGAIN IF YOU DONT WANT TO.

# list volume
Find the WINVAYU and ESPVAYU you made earlier, and take note of the numbers. You will be able to recognize them by their size.
# select volume <esp-partition-number>
# assign letter=<THE LETTER YOU WANT AS LONG AS IT IS NOT CURRENTLY IN USE IN FILE EXPLORER FOR ANOTHER DRIVE! (Example: Y)>:
# select volume <windows-partition-number>
# assign letter=<ANOTHER LETTER YOU WANT AS LONG AS IT IS NOT CURRENTLY IN USE IN FILE EXPLORER FOR ANOTHER DRIVE! (Example: X)>:
# exit
```

- You will have two partitions loaded, one is the ESP partition, and the other is the Windows partition. Take note of the letters you've used.

> [!WARNING]
From now on we will assume X: is the Windows partition and that Y: is the ESP partition for all the commands. You very very likely used other letters, or have to use other letters. Replace them correctly with what you previously picked or you will lose data on your PC.

- We will need our install.wim file now. If you haven't it already, you can make it [using this guide](/Install-en/ISO/GetWindows.md), or download it from [WoR Project](https://www.worproject.com/esd). When you are ready, run these commands:

```batch
dism /apply-image /ImageFile:"<path to install.wim>" /index:1 /ApplyDir:X:\
```

This will take a bit of time. Go make some coffee ☕ or some tea 🍵.

- Once that is done:

```batch
bcdboot X:\Windows /s Y: /f UEFI
```


Windows is now installed but has no drivers.

## Installing the drivers

- Download the latest driver package from https://github.com/woa-vayu/POCOX3Pro-Releases/releases/latest

Note: Here's a table of what to download if you're a bit lost:

| File Name                                      | Target Device         |
|------------------------------------------------|-----------------------|
| POCOX3Pro-Drivers-XXXX.XX-Desktop.zip  | POCO X3 Pro           |

- Extract the driver package, and go to the folder where you extracted it.

- Double click the ```OfflineUpdater.cmd``` file.

- Accept the User Account Control warning when prompted

- If asked enter the drive letter of the connected phone in mass storage, as we previously mentioned, for us it's currently ```X:```, but it may very well be different for you. In our example, we enter ```X:``` and then press enter.

- The process may take a while, once it is done, you will be prompted to press any key, press enter when that's the case.

Congratulations, you just installed your drivers!

- You can now reboot your phone using ```adb reboot bootloader```. You will be able to boot to Android and your phone will work normally. Set it up if you need it.

You will be back into POCO X3 Pro bootloader.

## Boot Windows 

We are ready to boot for the first time!

Reboot your device to the Bootloader mode, using adb or the recovery.

Let's boot the UEFI, from a command prompt:

```batch
fastboot boot uefi.img
```

This step above will be needed every time you will want to boot Windows and needs to be done from the Bootloader mode.

If you did everything right, Windows will now boot! Enjoy!

**Note:** If the Touch keyboard won't show up in OOBE, touch somewhere else (to let the text box loose focus) and then touch into the text box again. As an alternative, you can use the On-Screen Keyboard.

Let Windows set itself up, and come back once you're on the Windows Desktop on your POCO X3 Pro

## Boot Windows again after initial installation

You'll have two methods of booting Windows.

- Manual booting with a PC
    - Pros: You can freely update Android
    - Cons: You will need a PC to boot to Windows

- Enabling Dual Boot
    - Pros: You'll be able to boot Windows directly from the device

In case you want the dual boot option, then follow [this guide](/Install-en/DualBoot.md)

---
<details>
  <summary>In case you want to manually boot each time: (<b>Click to expand</b>)</summary>
  <p>

Reboot your device to the Bootloader mode, using adb or the recovery.

Let's boot the UEFI, from a command prompt:

```batch
fastboot boot uefi.img
```

This step above will be needed every time you will want to boot Windows and needs to be done from the Bootloader mode.

If you did everything right, Windows will now boot! Enjoy!

**Note:** If the Touch keyboard won't show up in OOBE, touch somewhere else (to let the text box loose focus) and then touch into the text box again. As an alternative, you can use the On-Screen Keyboard.
  </p>
</details>
