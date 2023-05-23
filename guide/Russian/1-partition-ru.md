<img align="right" src="https://github.com/wormstest/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Запуск Windows на POCO X3 Pro

## Установка

## Переразметка вашего устройства

### Предпосылки

- [Модифицированный TWRP или OrangeFox](../../../../releases/Recoveries)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

### Notes:
> **Warning** Если вы удалили любой раздел используя diskpart, Windows отправит команду памяти, которая сотрет все данные на чипе памяти!
- Все ваши данные в Android будут стерты! Сделайте резервную копию ваших данных, если она понадобится вам.
- Все команды были протестированы.
- Игнорируйте предупреждения `udevadm`.
- Не запускайте одну и ту же команду дважды.
- НЕ ПЕРЕЗАГРУЖАЙТЕ ТЕЛЕФОН если думаете, что совершли ошибку - обратитесь в [Telegram-чат проекта](https://t.me/winonvayualt).

#### ⚠️ Не запускайте все команды сразу, выполняйте их по порядку!

##### ⚠️ НЕ ДЕЛАЙТЕ ОШИБОК!!! ВЫ МОЖЕТЕ УБИТЬ ВАШЕ УСТРОЙСТВО КОМАНДАМИ НИЖЕ, ЕСЛИ ВЫ ВЫПОЛНИТЕ ИХ НЕПРАВИЛЬНО!!!

##### Установите модифицированное TWRP рекавери
```cmd
fastboot flash recovery <twrp.img>
fastboot reboot recovery
```

#### Размонтируйте все разделы
Зайдите в вкладку "монтирование" ("mount" на английском) и уберите галочки со всех разделов

#### Запустите ADB shell
```cmd
adb shell
```

#### Измените размер таблицы разделов
> Чтобы разделы Windows поместились в таблице разделов
```sh
sgdisk --resize-table 64 /dev/block/sda
```

#### Запустите parted
```sh
parted /dev/block/sda
```


#### Удалите раздел `userdata`
> Вы должны убедится что 32 это номер раздела `userdata` командой
>  `print all`
```sh
rm 32
```

#### Создайте разделы
> Если вы получите какое либо сообщение, говоря вам либо игнорировать либо отменить, просто введите i и нажмите enter.

<details>
<summary><b><strong>Для моделей на 128GB</strong></b></summary>



- Создайте раздел для данных Android
```sh
mkpart userdata ext4 11.8GB 68.6GB
```

- Создайте раздел, в который будет установлена Windows
```sh
mkpart win ntfs 68.6GB 126GB
```

- Создайте ESP раздел (будет содержать загрузчик Windows)
```sh
mkpart esp fat32 126GB 127GB 
```
  </summary>
</details>

<details>
<summary><b><strong>Для моделей на 256GB</strong></b></summary>


- Создайте раздел для данных Android
```sh
mkpart userdata ext4 11.8GB 134.6GB
```

- Создайте раздел, в который будет установлена Windows
```sh
mkpart win ntfs 134.6GB 254GB
```

- Создайте ESP раздел (будет содержать загрузчик Windows)
```sh
mkpart esp fat32 254GB 255GB
```
  </summary>
</details>

#### Сделайте раздел ESP загрузочным, чтобы образ UEFI смог его обнаружить
```sh
set 34 esp on
```

#### Выйдите из parted
```sh
quit
```

#### Перезагрузитесь в TWRP снова

#### Запустите adb shell ещё раз
```cmd
adb shell
```

#### Отформатируйте разделы
-  Отформатируйте ESP раздел в файловой системе FAT32
```sh
mkfs.fat -F32 -s1 /dev/block/by-name/esp -n ESPVAYU
```

-  Отформатируйте раздел Windows в файловой системе NTFS
```sh
mkfs.ntfs -f /dev/block/by-name/win -L WINVAYU
```

- Отформатируйте data
перейдите в меню "Очистка", выберите "Форматировать data" (Wipe > Format Data если установлен ангйлиский язык)
затем напишите `yes`.

#### Убедитесь что Android запускается
Перезагрузите телефон в систему и убедитесь, что Android запускается.


## [Следующий шаг: Установка Windows](/guide/Russian/2-install-ru.md)
