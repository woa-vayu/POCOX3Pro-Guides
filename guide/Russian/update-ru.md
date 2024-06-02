<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2PocoX3ProWindows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Запуск Windows на POCO X3 Pro

## Обновление драйверов 

### Требования 
- [Образ recovery](https://github.com/woa-vayu-archive/Port-Windows-11-POCO-X3-Pro/releases/tag/Recoveries)

- [Образ UEFI](https://github.com/woa-vayu/msmnilePkg/releases/latest)

- [Драйвера](https://github.com/woa-vayu/Vayu-Drivers/releases/latest)

### Загрузитесь в TWRP
> Замените `<recovery.img>` действительным путём к recovery.img
> Если ваше recovery было заменено стоковым, прошейте его снова используя
```cmd
fastboot flash recovery <recovery.img> reboot recovery
```

#### Активируйте режим mass storage 
> Если он попросит вас запустить его ещё раз, сделайте это
```cmd
adb shell msc
```

### Diskpart
```cmd
diskpart
```

#### Выберите раздел Windows телефона
> Используйте `list volume` чтобы найти его, он называется **WINVAYU**
```diskpart
select volume <number>
```

#### Привяжите букву X
```diskpart
assign letter x
```

#### Выйдите из diskpart
```diskpart
exit
```

### Установка драйверов 
Распакуйте архив драйверов который вы скачали ранее и запустите файл `OfflineUpdater.cmd` 
> Когда скрипт запросит у вас букву диска, введите **X:**
  
### Перезагрузитесь в fastboot чтобы прошить UEFI
> Вы также можете использовать приложение WOA Helper, в этом случае вы можете перезагрузиться с помощью ``adb reboot``.
>
> Убедитесь, что вы используете последнюю версию UEFI, поскольку Windows может не загрузиться, если вы обновите драйверы без обновления UEFI
```cmd
adb reboot bootloader
```

#### Загрузитесь в Windows
> Замените <uefi.img> путём к образу UEFI 
```cmd
fastboot flash boot <uefi.img>
```
## Готово!
