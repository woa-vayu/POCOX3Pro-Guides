<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Запуск Windows на Poco X3 PRO

## Установка

## Установка Windows

### Файлы

- [Образ Windows для ARM (рекомендуется Windows 11)](https://uupdump.net/)
- [Образ UEFI](https://github.com/woa-vayu/edk2-msm/releases/latest)
- [DriverUpdater](https://github.com/WOA-Project/DriverUpdater/releases/latest)
- [Драйверы](https://github.com/woa-vayu/Vayu-Drivers/releases/latest)
- [Модифицированный TWRP](../../../releases/Recoveries) (должно быть уже установлено)

#### Загрузитесь в TWRP

#### Запустите скрипт MSC

> Если скрипт попросит запустить его еще раз, то так и сделайте

```cmd
adb shell msc
```

  

### Привяжите букву к тому
  

#### Запустите diskpart

> После того, как телефон определится как диск
> (если не определяется, переподключите его)

```cmd
diskpart
```


### Присвойте букву `X` тому Windows

#### Выберите том Windows на телефоне
> Используйте `list volume` чтобы найти его, он называется "WINVAYU"

```diskpart
select volume <number>
```

#### Присвойте "X" тому
```diskpart
assign letter x
```

### Присвойте букву "Y" загрузочному тому

#### Выберите загрузочный том телефона
> Используйте `list volume` чтобы найти его, он называется "ESPVAYU"

```diskpart
select volume <number>
```

#### Присвойте букву "Y"

```diskpart
assign letter y
```

#### Выйдите из diskpart
```diskpart
exit
```

  
  

### Установка

> Замените `path\to\install.wim` на действительный путь до install.wim,

> `install.wim` находится в папке `sources` внутри вашего ISO
> (также он может называться `install.esd`)
> Его можно получить смонтировав или распаковав ISO образ

```cmd
dism /apply-image /ImageFile:path\to\install.wim /index:1 /ApplyDir:X:\
```

### Узнайте тип установленного экрана

```cmd
adb shell "dmesg | grep dsi_display_bind"
```
> Если ваша экран `Tianma`, то будет написано `dsi_j20s_36_02_0a_video_display`

> Если ваша экран `Huaxing`, то будет написано `dsi_j20s_42_02_0b_video_display`

### Установите драйверы

> Замените `path\to\drivers` на действительный путь к папке с драйверами
> Замените `paneltype` на тип вашего экрана (tianma/huaxing)

```cmd
.\driverupdater.exe -d path\to\drivers\definitions\Desktop\ARM64\Internal\vayu_paneltype.txt -r path\to\drivers -p X:
```

  

### Создайте файлы загрузчика Windows

```cmd
bcdboot X:\Windows /s Y: /f UEFI
```

  
  

## Разрешение неподписанных драйверов

> Если вы этого не сделайте, то система не загрузится

```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" testsigning on
```

### Отвяжите буквы от томов
  
> Чтобы они не остались после отключения телефона

```cmd
diskpart
```


#### Выберите том Windows на телефоне
> Используйте `list volume` чтобы найти его, он называется "WINVAYU"

```diskpart
select volume <number>
```

#### Отвяжите букву "X"
```diskpart
remove letter x
```

#### Выберите загрузочный том телефона
> Используйте `list volume` чтобы найти его, он называется "ESPVAYU"

```diskpart
select volume <number>
```

#### Отвяжите букву "Y"
```diskpart
remove letter y
```

#### Выйдите из diskpart
```diskpart
exit
```

## Запуск Windows

### Переместите файл `<uefi.img>` на телефон

```cmd
adb push <uefi.img> /sdcard
```

#### Если у вас есть карта памяти, то используйте

```cmd
adb push <uefi.img> /external_sd
```


### Сделайте бекап основного образа boot

> Переместите его на карту памяти, если это возможно


### Установите образ uefi через TWRP
Откройте файл `uefi.img` файл в TWRP и прошейте его в раздел boot

## Запуск Android
> Используйте ранее сохраненный образ (прошейте его обратно)

## Готово!
