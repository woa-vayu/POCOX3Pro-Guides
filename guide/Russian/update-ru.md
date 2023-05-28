<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Запуск Windows на POCO X3 Pro

## Обновление драйверов в Windows

### Требования

- [UEFI](https://github.com/woa-vayu/edk2-msm/releases/latest)
- [Modded TWRP/OFOX](../../../../releases/Recoveries)
- [DriverUpdater](https://github.com/WOA-Project/DriverUpdater/releases/latest)
- [Drivers](https://github.com/woa-vayu/Vayu-Drivers/releases/latest)

#### Запустите TWRP с помощью fastboot используя комьютер

```
cmd
fastboot boot <twrp.img>
```

> Если у вас уже установлен TWRP, просто зажмите кнопки питания и громкости + при запуске телефона


#### Выполните скрипт

```cmd
adb shell msc.sh
```

### Назначение буквы диску

#### Запустите менеджер дисков Windows

> Когда X3 Pro определиться как диск

```cmd
diskpart
```


### Назначение буквы `x` разделу Windows

#### Выберите раздел Windows
> Используйте `list volume`, чтобы найти его, его имя "WINVAYU"

```diskpart
select volume <номер>
```

#### Назначение буквы `x`
```diskpart
assign letter=x
```

#### Выход из diskpart
```diskpart
exit
```


### Установка драйверов
> Замените `<vayudriversfolder>` на полный путь к папке с драйверами

> Откройте cmd от имени администратора


```cmd
DriverUpdater.exe -d <vayudriversfolder>\definitions\Desktop\ARM64\Internal\vayu.txt -r <vayudriversfolder> -p X:
```


### Загрузка с загрузочного образа UEFI

```
fastboot flash boot <uefi.img>
```

## Готово!