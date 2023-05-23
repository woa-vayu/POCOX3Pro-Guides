<img align="right" src="https://github.com/wormstest/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Запуск Windows на POCO X3 Pro

## Установка

## Развёртывание образа Windows
> Вам нужно будет отключить MTP в разделе "Монтирование"

### Предпосылки

- [Образ Windows 10/11 ARM (Windows 11 рекомендуется)](https://uupdump.net/)
- [UEFI образ](https://github.com/halal-beef/edk2-msm/releases/latest)
- [DriverUpdater](https://github.com/WOA-Project/DriverUpdater/releases/latest)
- [Драйвера](https://github.com/halal-beef/Vayu-Drivers/releases/latest)

#### Загрузитесь в TWRP 

#### Запустите скрипт msc.sh

```cmd
adb shell msc.sh
```

  

### Дайте буквы дискам
  

#### Откройте диспетчер дисков

> Когда ваш телефон определился как диск

```cmd
diskpart
```


### Присвойте букву `X` разделу для Windows

#### Выберите раздел Windows находящийся на телефоне
> Используйте `list volume` чтобы найти его, его имя "WINVAYU"

```diskpart
select volume <number>
```

#### Присвойте букву X
```diskpart
assign letter=x
```

### Присвойте букву `Y` разделу esp

#### Выберите раздел ESP находящийся на телефоне
> Используйте `list volume` чтобы найти его, его имя "ESPVAYU"

```diskpart
select volume <number>
```

#### Присвойте букву Y

```diskpart
assign letter=y
```

#### Выйдите из diskpart
```diskpart
exit
```

  
  

### Установка

> Замените `<path/to/install.wim>` действительным путём к install.wim,

> `install.wim` находится в папке sources внутри вашего ISO
> (он также может иметь имя `install.esd`)
> Вы можете получить его файл распаковав или смонтировав ISO

```cmd
dism /apply-image /ImageFile:<path/to/install.wim> /index:1 /ApplyDir:X:\
```

### Узнайте, какой у вас тип панели

> Запустите cmd

```cmd
adb shell cat /proc/cmdline
```
> Ищите `msm_drm.dsi_display0` почти внизу

> Если ваша панель `Tianma`, то `msm_drm.dsi_display0` будет равно  `dsi_j20s_36_02_0a_video_display`

> Если ваша панель `Huaxing`, то `msm_drm.dsi_display0` будет равно  `dsi_j20s_42_02_0b_video_display`, если это так, перейдите в папку с драйверами `Vayu-Drivers/components/QC8150/Device/DEVICE.SOC_QC8150.VAYU/Drivers/Touch/` удалите `j20s_novatek_ts_fw01.bin`, и переименуйте `j20s_novatek_ts_fw02.bin` в `j20s_novatek_ts_fw01.bin`

### Установка драйверов

> Замените `<vayudriversfolder>` путём к папке с вашими драйверами

```cmd
.\driverupdater.exe -d <vayudriversfolder>\definitions\Desktop\ARM64\Internal\vayu.txt -r <vayudriversfolder> -p X:
```

  

### Создайте файлы загрузчика Windows

```cmd
bcdboot X:\Windows /s Y: /f UEFI
```

  
  

## Разрешите неподписанные драйвера

> Если вы этого не сделаете, то получите BSOD.

```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" testsigning on
```

### Уберите метки дисков
  
> Чтобы они не остались после отключения устройства

```cmd
diskpart
```


#### Выберите раздел Windows находящийся на телефоне
> Используйте `list volume` чтобы найти его, его имя "WINVAYU"

```diskpart
select volume <number>
```

#### Уберите букву X у диска
```diskpart
remove letter x
```

#### Выберите раздел ESP находящийся на телефоне
> Используйте `list volume` чтобы найти его, его имя "ESPVAYU"

```diskpart
select volume <number>
```

#### Уберите букву Y у диска

```diskpart
remove letter y
```

#### Выйдите из diskpart
```diskpart
exit
```

## Загрузка в Windows

### Переместите `<uefi.img>` файл на ваше устройство

```cmd
adb push <uefi.img> /sdcard
```

#### если у вас имеется карта памяти, вы можете использовать это

```cmd
adb push <uefi.img> /external_sd
```


### Сделайте бэкап нынешнего загрузчика
> Вам нужно это сделать единожды

> Оставьте его на карте памяти, если это возможно


### Прошейте uefi образ импользуя TWRP
Перейдите к `uefi.img` образу и прошейте его в boot раздел

## Загрузка обратно в Android
> Восстановите ваш бэкап используя TWRP

## Готово!
