# Making Cellular work on POCO X3 Pro

## Files/Tools Needed 📃

Recovery image:

11 image supports Android™ 11 encryption

12 image supports Android™ 12/12.1/13/14 encryption

| File Name                                       | Target Device         |
|-------------------------------------------------|-----------------------|
| [shrp-3.2_12-vayu.img](https://github.com/woa-vayu-archive/Port-Windows-11-POCO-X3-Pro/releases/download/Recoveries/shrp-3.2_12-vayu.img) | POCO X3 Pro |
| [twrp-3.7.0_11-vayu.img](https://github.com/woa-vayu-archive/Port-Windows-11-POCO-X3-Pro/releases/download/Recoveries/twrp-3.7.0_11-vayu.img) | POCO X3 Pro |

Cellular provisioning script:

| File Name                                       | Target Device         |
|-------------------------------------------------|-----------------------|
| [modemprov.zip](https://github.com/woa-vayu-archive/Port-Windows-11-POCO-X3-Pro/releases/download/modemprov/modemprov.zip) | POCO X3 Pro |

- Windows Command Prompt, Linux is not required

## Disclaimers

> [!WARNING]
> - Don't create partitions from Mass Storage Mode on Windows (because ABL will break with blank/spaces in names), your phone may be irrecoverable otherwise
> - If you see a warning and/or error during the process, it is not normal. Contact us on telegram if you see anything odd, but do not continue or proceed on your own, you will break things further.
> - Do not run all commands at once.
> - Do not commit *any* typo with *any* commands.
> - Be familiar with command line interfaces.

# Steps 🛠️

## Booting to recovery

- Reboot your device into recovery

## Dumping Modem partitions using automated script

- Go into the Install page

- Navigate to the folder where you placed ```modemprov.zip```


- Flash it

- Now you can boot into Windows

## Dumping Modem partitions manually

Using [the following guide](/Other-en/ExtractingPartitions.md), extract the following partitions:

- ```modemst1```
- ```modemst2```

once done, you should have obtained the ```modemst1.img``` and ```modemst2.img``` files on your computer.

Please note that your device is already in recovery, there's no need to put it back again into recovery. (So jump directly to the adb shell section of the above's guide).

### Entering Mass Storage Mode

- Run the mass storage shell script in order to boot into Mass Storage from recovery. You must decrypt your data if it asks you to.

```batch
adb shell msc
```

- If it asks you to run it once again, do so

Your POCO X3 Pro should now be in USB Mass Storage Mode.

### Copying files over

Assuming the Windows partition is available under X: (may be different for you), do the following:

- Copy the ```modemst1.img``` file to ```X:\Windows\System32\DriverStore\FileRepository\qcremotefs8150_<random data here>\bootmodem_fs1```
- Copy the ```modemst2.img``` file to ```X:\Windows\System32\DriverStore\FileRepository\qcremotefs8150_<random data here>\bootmodem_fs2```

Please note bootmodem_fs1 is the name of the file, and not a folder (same for bootmodem_fs2).
You may have to adjust permissions on the ```X:\Windows\System32\DriverStore\FileRepository\qcremotefs8150_<random data here>``` folder in order to copy paste the above's files.

- Now you can boot into Windows

---

_**© 2020-2024 The Duo WOA Authors**_

_Snapdragon is a registered trademark of Qualcomm Incorporated. Microsoft, the Microsoft Corporate Logo, Windows, Surface, Surface Duo, Windows Hello, Continuum, Hyper-V, and DirectX are registered trademarks of Microsoft Corporation in the United States. Android is a registered trademark of Google LLC. Miracast is a registered trademark of the Wi-Fi Alliance. Other binaries may be copyright Qualcomm Incorporated, Microsoft Surface and Xiaomi Inc._

_**Limited emergency calling**_

_Running Windows on your POCO X3 Pro is not a replacement for a proper phone operating system and does not have emergency calling capabilities._

_**Hello from Seattle (US), France, Italy.**_
