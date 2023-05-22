# Развёртывание образа Windows
### Назначение букв разделам

> Вам нужно будет отключить MTP в разделе "Монтирование"
### Запустите скрипт msc.sh
```cmd
adb shell msc.sh
```

> Когда ваш телефон определился как диск запустите diskpart
```diskpart
Используйте `list volume` для того, чтобы найти разделы Windows и ESP, они называются "WINVAYU" и "ESPVAYU"
# select volume <win-partition-number>
# assign letter=x
# select volume <esp-partition-number>
# assign letter=y
# exit
```

> Замените `<path/to/install.wim>` действительным путём к install.wim, `install.wim` находится в папке sources внутри вашего ISO. Вы можете получить этот файл распаковав или смонтировав его
```cmd
dism /apply-image /ImageFile:<path/to/install.wim> /index:1 /ApplyDir:X:\
```

### Создайте файлы загрузчика Windows
```cmd
bcdboot X:\Windows /s Y: /f UEFI
```

### Разрешите неподписанные драйвера
> Если вы этого не сделаете, то получите BSOD.
```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" testsigning on
```
### Установка драйверов
#### Узнайте ваш тип панели
> Перейдите в папку platform-tools
```cmd
adb shell cat /proc/cmdline
```
> Ищите экран почти в самом внизу
> Если ваше устройство `Tianma`, то `msm_drm.dsi_display0` будет `dsi_j20s_36_02_0a_video_display`.
> Если ваше устройство `Huaxing`, то `msm_drm.dsi_display0` будет `dsi_j20s_42_02_0b_video_display`: перейдите в папку драйверов (Vayu-Drivers/components/QC8150/Device/DEVICE.SOC_QC8150.VAYU/Drivers/Touch/) и удалите j20s_novatek_ts_fw01.bin, наконец, переименуйте j20s_novatek_ts_fw02.bin в j20s_novatek_ts_fw01.bin

> Замените `<vayudriversfolder>` путём к папке с вашими драйверами
```cmd
driverupdater.exe -d <vayudriversfolder>\definitions\Desktop\ARM64\Internal\vayu.txt -r <vayudriversfolder> -p X:
```

### Загрузка в Windows

<details>
<summary><strong>Двойная загрузка между Android и Windows</strong></summary>

- [Вы должны следовать этой инструкции](dualboot-ru.md)
</details>

<details>
<summary><strong>Загрузка Windows вручную каждый раз</strong></summary>

Перезагрузите телефон в fastboot и загрузитесь с UEFI:
```fastboot
fastboot boot <uefi.img>
```

Android загрузится при следующей перезагрузке, для загрузки Windows вы должны вновь загрузится с UEFI.
</details>

- Если у вас BSOD с кодом ошибки BOUND_IMAGE_UNSUPPORTED при первой загрзке Windows, вы должны использовать [старое UEFI](https://github.com/woa-vayu/Port-Windows-11-Poco-X3-pro/releases) для первой загрузки (тачскрин не работает в старой версии UEFI).

# Готово!
