# Подвійне завантаження Android та Windows

## Вимоги

- [Magisk](https://github.com/topjohnwu/Magisk/releases/latest)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

- [TWRP/OFOX](../../../../releases/Recoveries)

- [NTFS Android Magisk Module](../../../../releases/ntfsdroid)

- [UEFI](https://github.com/woa-vayu/edk2-msm/releases/latest)

- [UEFI & Android Boot Flashing App](../../../../releases/dualboot)

## Налаштування телефону

### Додати підтримку NTFS в Android

- Встановіть Magisk, якщо ще не встановили
- Встановіть модуль NTFS Android magisk через Magisk manager

### Встановлення застосунків

- Встановіть наданий АРК
- Створіть папку з назвою «vayu-uefi-2.1.0-release» у внутрішній пам'яті.
- Скопіюйте всі "образи uefi" в цю папку
- Відкрийте застосунок й надайте дозвіл, що вимагає Root

## Компьютерна частина

### Завантаження в рекавері

- Перезавантажте пристрій в завантажувач.

- Виконайте ```fastboot boot <recovery.img>``` (обраним вами  <recovery.img>)

### Переміщення деяких файлів в телефон

- Коли рекавері завантажиться, виконайте ```adb shell mount.ntfs /dev/block/by-name/win /win```
- Виконайте ```adb shell dd if=/dev/block/by-name/boot of=/win/boot.img```
- Виконайте ```adb push switchtoandroid.exe /win/Users/<username>/Desktop/switchtoandroid.exe``` (Змінивши <username> на назву користувача в вашому розділі Windows)
  
### Перезавантаження з Windows в Android
  
  - Виконайте (ЗАПУСТІТЬ) switchtoandroid.exe на телефоні з правами АДМІНІСТРАТОРА

### Перезавантаження з Android в Windows 
  
  - Виконайте (ЗАПУСТІТЬ) WOA Helper
  - Натисніть "Quickboot в windows"