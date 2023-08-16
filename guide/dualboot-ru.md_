<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Запуск Windows на Poco X3 PRO

## Двойной запуск Android и Windows (Метод №1)

> [Напоминание] 
> Работает на любом Android устройстве и ядре, но важно что запуск в Windows из Android занимает чуть больше времени чем обычно

### Файлы для установки

- [Magisk](https://github.com/topjohnwu/Magisk/releases/latest)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

- [Модицированный TWRP (Другие не подойдут!!!)](../../../releases/Recoveries)

- [NTFS Android Magisk модуль](../../../releases/ntfsdroid)

- [UEFI](https://github.com/woa-vayu/edk2-msm/releases/latest)

- [UEFI & Android приложение для установки](../../../releases/dualboot)

### Настройка телефона

#### Добавление поддержки NTFS в Android (Magisk)

- Установите Magisk если это не сделали
- Установите модуль поддержки NTFS в Magisk

#### Настройка приложения

- Установите .apk файл который был ранее
- Создайте папку "UEFI" в основное хранилище устройства (Не карта памяти)
- Скопируйте все uefi образы в папку с названием ```vayu-<panel>-<version>.img```
- Откройте приложение и дайте доступ к Root правам

### Действия для ADB (Пк)

#### Установка рекавери, и запуск

- Перезагрузитесь в Bootloader

- Запустите команду ```fastboot flash recovery <recovery.img> reboot recovery```

#### Перенос файлов на телефон

- Когда рекавери запустилось, введите команду ```adb shell mount.ntfs /dev/block/by-name/win /win```
- Запустите команду ```adb shell dd if=/dev/block/by-name/boot of=/win/boot.img```
- После, запустите команду ```adb push switchtoandroid.exe /win/Users/<username>/Desktop/switchtoandroid.exe```
  
#### Запуск в Android
  
  - Запустите switchtoandroid.exe на телефоне от имени **АДМИНИСТРАТОРА**

#### Запуск в Windows
  
  - Запустите приложение
  - Нажмите "Quickboot to windows"
  
## Вы успешно сделали это!
  
  

  
## Двойной запуск Android и Windows (Метод №2)
  
> [Напоминание] 
> Может не работать на некоторых Android устройствах и ядрах, вам надо делать это каждый раз как выходит обновление или установка прошивки и иногда оно может сломать это, означает вам надо переустановить это легче и быстрее для запуска в Android
  
### Prerequisites

- [Последний ZIP установщик](https://github.com/woa-vayu/edk2-msm/releases/latest)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

- [Модифицированный TWRP](../../../releases/Recoveries)
  
  
#### Установка рекавери и запуск

- Перезапуститесь в Bootloader

- Запустите команду ```fastboot flash recovery <recovery.img> reboot recovery```

  
#### Перезагрузка телефона в режим установки через ADB
  
- Зайдите в дополнительную вкладку на вашем телефоне
- Нажмите ADB Sideload
- Свайпните чтобы включить режим ADB Sideload
  
#### Установка UEFI с поддержкой двойного запуска
  
- Откройте ADB в командной строке на вашем компьютере
- и введите команду ```adb sideload <путь до zip файла>```
