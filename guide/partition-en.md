<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Running Windows on the POCO X3 Pro

## Installation

## Partitioning your device

### Prerequisites

- [Modded TWRP/OFOX](../../../../releases/Recoveries)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

### Notes:
> **Warning** if you ever delete any partitions via diskpart, Windows will send a UFS command which would erase the entire UFS storage!
- All your data will be erased! Backup now if needed.
- These commands have been tested.
- Ignore `udevadm` warnings.
- Do not run the same command twice.
- DO NOT REBOOT YOUR PHONE if you think you made a mistake, ask for help in the [Telegram chat](https://t.me/winonvayualt).

#### ⚠️ Do not run all commands at once, execute them in order!

##### ⚠️ DO NOT MAKE ANY MISTAKE!!! YOU CAN BREAK YOUR DEVICE WITH THE COMMANDS BELOW IF YOU DO THEM WRONG!!!

##### Flash the modified TWRP recovery
```cmd
fastboot flash recovery <twrp.img>
fastboot reboot recovery
```

#### Unmount all partitions
Go to "Mount" section and unmount all partitions

#### Start ADB shell
```cmd
adb shell
```

#### Resize the partition table
> So that the Windows partitions can fit
```sh
sgdisk --resize-table 64 /dev/block/sda
```

#### Start parted
```sh
parted /dev/block/sda
```


#### Delete the `userdata` partition
> You can make sure that 32 is the userdata partition number by running
>  `print all`
```sh
rm 32
```

#### Create partitions
> If you get any warning message telling you to ignore or cancel, just type i and press Enter

<details>
<summary><b><strong>For 128GB Models</strong></b></summary>



- Create Android's data partition
```sh
mkpart userdata ext4 11.8GB 68.6GB
```

- Create the main partition where Windows will be installed to
```sh
mkpart win ntfs 68.6GB 126GB
```

- Create the ESP partition (stores Windows bootloader data and EFI files)
```sh
mkpart esp fat32 126GB 127GB 
```
  </summary>
</details>

<details>
<summary><b><strong>For 256GB Models</strong></b></summary>


- Create Android's data partition
```sh
mkpart userdata ext4 11.8GB 134.6GB
```

- Create the main partition where Windows will be installed to
```sh
mkpart win ntfs 134.6GB 254GB
```

- Create the ESP partition (stores Windows bootloader data and EFI files)
```sh
mkpart esp fat32 254GB 255GB
```
  </summary>
</details>

#### Make ESP partiton bootable so the UEFI image can detect it
```sh
set 34 esp on
```

#### Quit parted
```sh
quit
```

#### Reboot to TWRP again

#### Start the shell again on your PC
```cmd
adb shell
```

#### Format partitions
-  Format the ESP partiton as FAT32
```sh
mkfs.fat -F32 -s1 /dev/block/by-name/esp -n ESPVAYU
```

-  Format the Windows partition as NTFS
```sh
mkfs.ntfs -f /dev/block/by-name/win -L WINVAYU
```

- Format data
Go to "Wipe" menu and press "Format Data", 
then type `yes`.

#### Check if Android still starts
Just restart the phone, and see if Android still works


## [Next step: Installing Windows](/guide/install-en.md)
