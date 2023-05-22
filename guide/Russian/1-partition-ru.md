# Установка Windows на POCO X3 Pro
## Создание разделов для Windows
### Заметки
> **Внимание!** Если вы удалили любой раздел используя diskpart, Windows рано или поздно отправит команду памяти, которая будет неверно распознана, отчего память будет стёрта.
- Все команды были протестированы.
- Все ваши данные в Android будут удалены.
- Игнорируйте предупреждения `udevadm`.
- Не запускайте одну и ту же команду дважды.
- НЕ ПЕРЕЗАГРУЖАЙТЕ ТЕЛЕФОН если думаете, что совершли ошибку - обратитесь в [Telegram-чат проекта](https://t.me/winonvayualt).

### Нужные файлы
- [Образ Windows 10/11 ARM (Windows 11 рекомендуется)](https://uupdump.net/)
- [platform-tools(ADB & Fastboot)](https://developer.android.com/studio/releases/platform-tools)
- [DriverUpdater для установки и обновления драйверов](https://github.com/WOA-Project/DriverUpdater/releases/)
- [UEFI образ](https://github.com/halal-beef/edk2-msm/releases/tag/latest)
- [Модифицированный TWRP или OrangeFox](https://github.com/woa-vayu/Port-Windows-11-Poco-X3-pro/releases/tag/Recoveries)

### Запустите TWRP через комьютер с помощью fastboot
```cmd
fastboot boot <twrp.img>
```
⚠️ Не запускайте все команды сразу, выполняйте их по порядку!

⚠️ НЕ ДЕЛАЙТЕ ОШИБОК!!! ВЫ МОЖЕТЕ СЛОМАТЬ ВАШЕ УСТРОЙСТВО КОМАНДАМИ НИЖЕ, ЕСЛИ ВЫ СДЕЛАЕТЕ ИХ НЕПРАВИЛЬНО!!!

### Размонтирование всех разделов
Перейдите в раздел "Монтирование" и размонтируйте все разделы.

## Запустите adb shell:
```cmd
adb shell
```

### Измените размер таблицы разделов
> Чтобы разделы Windows поместились в таблице разделов
```sh
sgdisk --resize-table 64 /dev/block/sda
```

### Запустите parted
```sh
parted /dev/block/sda
```

### Удалите раздел `userdata`
> Вы должны убедится что 32 это номер раздела `userdata` командой
>  `print all`
```sh
rm 32
```

### Создайте разделы
> Если вы получите какое либо сообщение, говоря вам либо игнорировать либо отменить, просто введите i и нажмите enter.

<details>
<summary><strong>Для моделей 6/128</strong></summary>
- Создайте раздел `userdata` для использования Android вместе с Windows
```sh
mkpart userdata ext4 11.8GB 68.6GB
```

- Создайте раздел, в который будет установлена Windows
```sh
mkpart win ntfs 68.6GB 126GB
```

- Создайте ESP раздел (будет содержать загрузчик Windows)
```sh
mkpart esp fat32 126.6GB 127GB
```
</details>

<details>
<summary><strong>Для моделей 8/256</strong></summary>
- Создайте раздел `userdata` для использования Android вместе с Windows
```sh
mkpart userdata ext4 11.8GB 134.6GB
```

- Создайте раздел на который будет установлена Windows
```sh
mkpart win ntfs 134.6GB 254GB
```

- Создайте ESP раздел (будет содержать загрузчик Windows)
```sh
mkpart esp fat32 254GB 255GB
```
</details>


### Сделайте раздел ESP загрузочным, чтобы образ EFI смог его обнаружить
```sh
set 34 esp on
```

### Закройте parted
```sh
quit
```

- Перезагрузитесь в TWRP

### Запустите adb shell снова
```cmd
adb shell
```

### Отформатируйте разделы
```sh
mkfs.fat -F32 -s1 /dev/block/by-name/esp -n ESPVAYU
mkfs.ntfs -f /dev/block/by-name/win -L WINVAYU
```

- Отформатируйте userdata: перейдите в меню "Очистка", выберите "Форматировать data", напишите `yes`, и нажмите "✓".

### Убедитесь что Android запускается
Перезагрузите телефон в систему и убедитесь, что Android запускается.

## [Следующий шаг: Установка Windows](/guide/Russian/2-install-ru.md)
