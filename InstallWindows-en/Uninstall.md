# Uninstall Windows and revert your POCO X3 Pro to stock

## Files/Tools Needed 📃

TWRP image:

| File Name                                       | Android version |
|-------------------------------------------------|-----------------|
| [twrp-3.7.1_12-vayu.img](https://github.com/woa-vayu/POCOX3Pro-Guides/releases/download/Recoveries/twrp-3.7.1_12-vayu.img) | Android 12/12.1/13/14 |
| [twrp-3.7.0_11-vayu.img](https://github.com/woa-vayu/POCOX3Pro-Guides/releases/download/Recoveries/twrp-3.7.0_11-vayu.img) | Android 11 |

## Disclaimers

> [!IMPORTANT]
> **THIS WILL WIPE ALL YOUR ANDROID DATA**
>
> We don't take any responsibility for any damage done to your phone. By following this guide, you agree to take full responsibility of your actions. We have done some testing,
>
> but this is **STILL IN PREVIEW** and things can go wrong.

# Steps 🛠️

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

## Booting to TWRP

- Reboot your device into TWRP, assuming you have installed it previously

## Restoring the original partitions

- Once booted into TWRP run the following command:

```batch
adb shell restore
```

- If it asks you to run it once again, do so

- And leave the device shell

```bash
exit
```

- Once it is done, you can reboot your phone using ```adb reboot```. You will be able to boot to Android and your phone should work normally. In case it doesn't you likely messed up something above.

- You should now be seeing the Android Out of Box Experience (OOBE). Setup your phone to confirm it works correctly if you need it.

- Once your phone is confirmed working, congratulations, you successfully uninstalled Windows from your device.

You may however want to also relock the bootloader of the device, please note that you cannot relock the bootloader of your device if you flashed a custom rom as well as installed Windows without uninstalling it, or modified the boot partition for your own purposes.

🎉 Congratulations, your POCO X3 Pro is back to factory settings.

---

_**© 2020-2024 The Duo WOA Authors**_
