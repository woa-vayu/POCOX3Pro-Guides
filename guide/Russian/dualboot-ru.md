# Двойная загрузка Android и Windows

## Требования

- [Magisk](https://github.com/topjohnwu/Magisk/releases/latest)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

- [TWRP/OFOX](../../../../releases/Recoveries)

- [NTFS Android Magisk Module](../../../../releases/ntfsdroid)

- [UEFI](https://github.com/woa-vayu/edk2-msm/releases/latest)

- [UEFI & Android Boot Flashing App](../../../../releases/dualboot)

## Настройка телефона

### Добавление поддержки NTFS в Android

- Установите Magisk, если еще не установили
- Установите модуль NTFS Android magisk через Magisk manager

### Установка приложений

- Установите предоставленный APK
- Создайте папку с именем «vayu-uefi-2.1.0-release» во внутренней памяти.
- Скопируйте все образы uefi в эту папку
- Откройте приложение и разрешите требуемый Root доступ

## Компьютерная часть

### Загрузка в рекавери

- Перезагрузитесь в загрузчик

- Выполните ```fastboot boot <recovery.img>``` (заменив <recovery.img> выбранным вами рекавери)

### Перенос некоторых файлов на телефон

- Когда рекавери загрузится, выполните ```adb shell mount.ntfs /dev/block/by-name/win /win```
- Выполните ```adb shell dd if=/dev/block/by-name/boot of=/win/boot.img```
- Выполните ```adb push switchtoandroid.exe /win/Users/<username>/Desktop/switchtoandroid.exe``` (Заменив <username> на имя пользователя в вашем разделе Windows)
  
###  Перезагрузка из Windows в Android
  
  - Запустите switchtoandroid.exe на телефоне от имени **АДМИНИСТРАТОРА**

### Перезагрузка из Android в Windows 
  
  - Запустите WOA Helper
  - Нажмите "Quickboot в windows"