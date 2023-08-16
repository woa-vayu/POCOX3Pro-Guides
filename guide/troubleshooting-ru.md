<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Запуск Windows на Poco X3 PRO

## Решение проблем


## Телефон не загружается в Bootloader, но Android работает корректно

### Необходимые файлы:

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

Это происходит из-за разделов с названиями, которые Bootloader не может обработать. Чтобы исправить это:

- Загрузитесь в Recovery

- Подключите телефон к ПК

- Откройте командную строку на ПК

- Введите ```adb shell```

- Введите ```parted```

- Введите ```print```, чтобы отобразить все разделы

- Обратите внимание на разделы с пробелами в названии (например "Basic Data Partition") и запомните их номер

- Теперь запустите```rm <число тома>``` (например ```rm 36```)



## Касания пальцем регистрируются неправильно

Вы выбрали неправильный файл definiton при установке драйверов.
