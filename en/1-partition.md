# Partitioning your POCO X3 Pro

## Files/Tools Needed

Modified TWRP:

| File Name                                       | Android version |
|-------------------------------------------------|-----------------|
| [twrp-3.7.1_vap.img](https://github.com/woa-vayu/POCOX3Pro-Guides/releases/download/twrp/twrp-3.7.1_vap.img) | Android 12/12.1/13/14/15 |
- Unlocked bootloader

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

- [Latest POCO X3 Pro firmware](https://github.com/woa-vayu/POCOX3Pro-Guides/raw/main/Files/fw_vayu_miui_VAYUGlobal_V14.0.3.0.TJUMIXM_6be397120d_13.0.zip)

### Notes
>
> [!WARNING]  
> All your data will be erased! Back up now if needed.
>
> Do not run the same command twice.
>
> DO NOT REBOOT YOUR PHONE if you think you made a mistake, ask for help in the [Telegram chat](https://t.me/winonvayualt).
>
> Do not run all commands at once, execute them in order!

> [!IMPORTANT]
> Make sure you use the MODDED Recovery throughout this whole tutorial as we provide tools to help aid this installation process and make it as easy as possible for you.
>
> If you don't use it and you face any errors, consider it your fault and consider yourself alone if you try asking for support as you have deferred from the main guide.

### Opening CMD as an admin
>
> Download **platform-tools** and extract the folder somewhere, then open CMD as an **administrator**.
>
> It is recommended to keep this window open and use it throughout the entire guide.
>
> Replace `path\to\platform-tools` with the actual path to the platform-tools folder, for example **C:\platform-tools**.

```cmd
cd path\to\platform-tools
```

#### Flash the modded recovery
>
> While in fastboot mode, replace `path\to\moddedtwrp.img` with the actual path to the modded recovery image

```cmd
fastboot flash recovery path\to\moddedtwrp.img reboot recovery
```

#### Backing up your boot image
>
> This will back up your boot image in the current directory

```cmd
adb pull /dev/block/by-name/boot boot.img
```

### Flashing latest firmware
>
> [!Important]
> It is mandatory to flash the latest firmware (this does not affect your current ROM).

- Download the **fw_vayu_miui_VAYUGlobal_V14.0.3.0.TJUMIXM_6be397120d_13.0.zip** and put it somewhere on your phone.
- Select the **Install** button in TWRP, locate the firmware file, then install it.
- There is no need to reboot yet, stay in TWRP for the next few steps.

#### Unmount data
>
> Ignore any possible errors and continue

```cmd
adb shell umount /dev/block/by-name/userdata
```

#### Resizing partition table

``` cmd
adb shell sgdisk --resize-table 64 /dev/block/sda
```

#### Preparing for partitioning

```cmd
adb shell parted /dev/block/sda
```

#### Printing the current partition table
>
> Parted will print the list of partitions, userdata should be the last partition in the list.

```cmd
print
```

#### Removing userdata
>
> Replace **$** with the number of the **userdata** partition, which should be **32**

```cmd
rm $
```

#### Recreating userdata
>
> Replace **11.7GB** with the former start value of **userdata** which we just deleted
>
> Replace **70GB** with the end value you want **userdata** to have. In this example Android will have 70-11.7 = **58.3GB** of usable space

```cmd
mkpart userdata ext4 11.7GB 70GB
```

#### Creating ESP partition
>
> Replace **70GB** with the end value of **userdata**
>
> Replace **70.4GB** with the value you used before, adding **0.4GB** to it

```cmd
mkpart esp fat32 70GB 70.4GB
```

#### Creating Windows partition
>
> Replace **70.4GB** with the end value of **esp**

```cmd
mkpart win ntfs 70.4GB 100%
```

#### Making ESP bootable
>
> Use `print` to see all partitions. Replace "$" with your ESP partition number, which should be **33**

```cmd
set $ esp on
```

#### Exit parted

```cmd
quit
```

### Formatting Windows and ESP partitions

```cmd
adb shell mkfs.ntfs -f /dev/block/sda34 -L WINVAYU
```

```cmd
adb shell mkfs.fat -F32 -s1 /dev/block/sda33 -n ESPVAYU
```

### Formatting data

- Format all data in TWRP, or Android will not boot.
- ( Go to Wipe > Format data > type yes )

#### Check if Android still starts

- Just restart the phone, and see if Android still works

## [Next step: Rooting your phone](2-install.md)
