<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Запуск Windows на POCO X3 Pro

## Устранение проблем

### Устройство может загружаться в Android, но не в загрузчик


### Необходимые файлы: 

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

>Необходимые файлы: [platform-tools](https://developer.android.com/studio/releases/platform-tools)

Это вызвано разделами с именами томов, которые загрузчик не может обработать, чтобы исправить это:

- Загрузитесь в загрузчик

- Подключите телефон к ПК

- Откройте cmd на ПК

- Запустите ```adb shell```

- Запустите ```parted```

- Запустите ```print```, чтобы вывести список всех разделов.

- Найдите разделы с пробелами в именах, например «Basic Data Partition», и запишите их номер тома.

- Теперь запустите ```rm <номер тома>``` например, ```rm 36```


### Касания сенсорного экрана неточны/перевернуты

Вы выбрали не тот файл definitions при установке драйверов.
