# Extract the boot partition or other partitions

## Files/Tools Needed 📃

Recovery image:

11 image supports Android™ 11 encryption
12 image supports Android™ 12/12.1/13/14 encryption

| File Name                                       | Target Device         |
|-------------------------------------------------|-----------------------|
| [shrp-3.2_12-vayu.img](https://github.com/woa-vayu-archive/Port-Windows-11-POCO-X3-Pro/releases/download/Recoveries/shrp-3.2_12-vayu.img) | POCO X3 Pro |
| [twrp-3.7.0_11-vayu-mod4epsilon.img](https://github.com/woa-vayu-archive/Port-Windows-11-POCO-X3-Pro/releases/download/Recoveries/twrp-3.7.0_11-vayu-mod4epsilon.img) | POCO X3 Pro |

- [Platform Tools from Google (ADB and Fastboot)](https://developer.android.com/studio/releases/platform-tools)
- A Windows PC

## Disclaimers

> [!WARNING]
> - Read the entire guide before starting. Make sure you understand all of what you're going to do!
> - If you see a warning and/or error during the process, it is not normal. Contact us on telegram if you see anything odd, but do not continue or proceed on your own, you will break things further.
> - Don't rerun the commands if you interrupt the process. You may break things.
> - Do not run all commands at once.
> - Do not commit *any* typo with *any* commands.
> - Be familiar with command line interfaces.

## Acquiring all files

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

## Boot into recovery

- If not already done, please proceed with the installing recovery as told in [Getting to Mass Storage Mode] section in [Main guide](/InstallWindows-en/InstallWindowsManually.md) for POCO X3 Pro. Come back once you're done.

- Reboot into recovery

Your POCO X3 Pro will boot into TWRP, touch will not work and the device will say it is locked. This is completely normal and expected.

## Retrieve the location of our boot partition

- We need to open a shell to issue commands directly to the phone. To do so, run the following command on your PC:

```batch
adb shell "setenforce 0"
adb shell
```

You are now able to issue commands directly to your phone via your PC.

- Now, we need to find the location of our boot partition, as it is different for each device. To do so, run the following command on your PC:

```bash
ls /dev/block/by-name/
```

- This is going to output a lot of lines, with each partition name having its mount point. Look for the line that says `boot`

Let's make an image of the partition:

```bash
dd if=/dev/block/by-name/boot of=/tmp/boot.img
```

- Now let's exit the shell and pull the boot.img from the device, to do so, run the following command on your PC:

```bash
exit
```

```batch
adb pull /tmp/boot.img
```

If you did everything correctly, you will now have your `boot.img`. Enjoy! 🥳

---

_**© 2020-2024 The Duo WOA Authors**_

_Snapdragon is a registered trademark of Qualcomm Incorporated. Microsoft, the Microsoft Corporate Logo, Windows, Surface, Surface Duo, Windows Hello, Continuum, Hyper-V, and DirectX are registered trademarks of Microsoft Corporation in the United States. Android is a registered trademark of Google LLC. Miracast is a registered trademark of the Wi-Fi Alliance. Other binaries may be copyright Qualcomm Incorporated, Microsoft Surface and Xiaomi Inc._

_**Limited emergency calling**_

_Running Windows on your POCO X3 Pro is not a replacement for a proper phone operating system and does not have emergency calling capabilities._

_**Hello from Seattle (US), France, Italy.**_