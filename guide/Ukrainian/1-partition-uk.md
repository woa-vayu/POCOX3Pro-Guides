# Встановлення Windows на POCO X3 PRO

## Створення розділів для Windows

### Нотатки
> **Увага!** Якщо ви видалили будь-який розділ використовуючи diskpart, Windows рано или пізно відправить команду пам'яти, яка буде неправильно розпізнана, і тому пам'ять буде стерта.
- Всі команди були перевірені.
- Всі ваші дані в Android будуть видалені.
- Ігноруйте попередження `udevadm`.
- Не запускайте ту саму команду двічі.
- НЕ ПЕРЕЗАВАНТАЖУЙТЕ ТЕЛЕФОН якщо думаєте, що зробили помилку - зверніться в [Telegram-чат проекту](https://t.me/winonvayualt).

### Необхідні файли
- [Образ Windows 10/11 ARM(11 рекомендується)](https://uupdump.net/)
- [platform-tools(ADB & Fastboot)](https://developer.android.com/studio/releases/platform-tools)
- [DriverUpdater для встановлення та оновлення драйверів](https://github.com/WOA-Project/DriverUpdater/releases/)
- [UEFI образ](https://github.com/woa-vayu/edk2-msm/releases/tag/latest)
- [Модифікований TWRP чи OrangeFox](https://github.com/woa-vayu/Port-Windows-11-Poco-X3-pro/releases/tag/Recoveries)

### Завантажте TWRP чи OrangeFox через комп'ютер за допомогою fastboot
```cmd
fastboot boot <recovery.img>
```

### Розмонтування всіх розділів
Перейдіть до розділу "Монтування" та розмонтуйте всі розділи.
### Запустіть adb shell:
```cmd
adb shell
```

⚠️ Не запускайте всі команди одночасно, виконуйте їх по порядку!                                                                                           

⚠️ НЕ РОБІТЬ ЖОДНОЇ ПОМИЛКИ!!! ВИ МОЖЕТЕ ЗЛАМАТИ ВАШ ПРИСТРОЙ ЗА ДОПОМОГОЮ КОМАНД НИЖЧЕ, ЯКЩО ВИКОНАЄТЕ ЇХ НЕПРАВИЛЬНО!!!

### Змініть розмір таблиці розділів
> Щоб розділи Windows помістились в таблиці розділів
```sh
sgdisk --resize-table 64 /dev/block/sda
```

### Завантажте parted
```sh
parted /dev/block/sda
```

### Видаліть розділ `userdata`
> Ви повинні впевнитися що 32 это номер розділа `userdata`. Перевірте це командою `print all`.
```sh
rm 32
```

### Створення розділів `win, esp і userdata`
> Якщо ви отримаете повідомлення "Ignore or cancel?" просто введіть i и натісніть enter.
<details> 
<summary><strong>Для моделей 6/128</strong></summary>

- Створіть розділ `userdata` для використання Android поряд з Windows
```sh
mkpart userdata ext4 11.8GB 68.6GB
```
- Створіть розділ, до якого буде встановлена Windows
```sh
mkpart win ntfs 68.6GB 126GB
```
- Створіть ESP розділ (буде містити завантажувач Windows)
```sh
mkpart esp fat32 126.6GB 127GB
```
</details>
<details> 
<summary><strong>Для моделей 8/256</strong></summary>

- Створіть розділ `userdata` для використання Android поряд з Windows
```sh
mkpart userdata ext4 11.8GB 134.6GB
```
- Створіть розділ, до якого буде встановлена Windows
```sh
mkpart win ntfs 134.6GB 254GB
```
- Створіть ESP розділ (буде містити завантажувач Windows)
```sh
mkpart esp fat32 254GB 255GB
```
</details> 

### Зробіть розділ ESP завантажувальним, щоб образ EFI міг його виявити
```sh
set 34 esp on
```

### Закрийте parted
```sh
quit
```
- Перезавантажтеся у TWRP

### Запустіть adb shell знову
```cmd
adb shell
```
### Відформатуйте розділи для їх подальшого використання
```sh
mkfs.fat -F32 -s1 /dev/block/by-name/esp -n ESPVAYU
mkfs.ntfs -f /dev/block/by-name/win -L WINVAYU
```
- Відформатуйте /userdata для використання Android: перейдіть в меню "Очищення", виберіть "Форматувати data", напишіть `yes` та натисніть "✓".

### Переконайтеся, що Android запускається
Перезавантажте телефон в систему и переконайтесь, що Android запускається.


## [Наступний крок: Встановлення Windows](/guide/Ukrainian/2-install-uk.md)
