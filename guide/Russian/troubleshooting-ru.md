<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2PocoX3ProWindows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Запуск Windows на POCO X3 Pro

## Исправление проблем 

## Я не могу перемещать файлы в Windows из Android 

 Если вам не удается переместить файлы в папку Windows, это означает, что вы выключили Windows, а не перезапустили ее. Чтобы устранить эту проблему, загрузитесь обратно в Windows и выполните перезагрузку, затем, когда планшет перезагрузится, загрузитесь в fastboot и используйте его для возврата к Android

## Зарядка в Windows не работает 
> [!WARNING]
> Do not use a powered USB hub with host mode enabled, this can potentially break your device. If you use a powered USB hub, please use the [disable USB host mode guide](/guide/Russian/additional-materials-ru.md#disabling-usb-host-mode)

Charging in Windows only works on specific cables. Cables that have been known to work are the original Poco X3 Pro cable (identified by the additional orange/red pin in the USB-A port), and the Nimaso 100W USB-C to USB-C fast charging cable.


## Устройство может загрузиться в Android но не в fastboot 

### Требования: 

- [Android platform tools](https://developer.android.com/studio/releases/platform-tools)


This is caused by partitions with volume names the bootloader cannot handle, to fix this:

- Загрузитесь в recovery

- Подключите телефон к ПК

- Откройте терминал platform tools на ПК

- Выполните ```adb shell```

- Выполните ```parted```

- Выполните ```print``` to list all partitions

- Найдите разделы, в названиях которых есть пробелы, например "Basic Data Partition", и запомните их номера 

- Теперь выполните ```rm <номер раздела>``` e.g ```rm 36```


## Touchscreen touches are inaccurate/upside down

You picked the wrong definitions file while installing drivers.
