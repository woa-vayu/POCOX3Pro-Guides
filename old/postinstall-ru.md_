<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Запуск Windows на Poco X3 PRO

## Опциональные вещи для установки


### Настройка модема вручную

> [ПРЕДУПРЕЖДЕНИЕ]  
> Вам НАДО делать это каждый раз как вы запускаете Windows если вы хотите LTE (4G) соединение!

#### Файлы

- [Модифицированный TWRP](../../../releases/Recoveries)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

##### Установите и запуститесь в модифицированное рекавери

```fastboot flash recovery путь\до\twrp.img reboot recovery```

##### Распределение раздела

- Зайдите в mount меню
- Монтируйте раздел с Windows

##### Настройка модема

###### Запустите ADB Shell

```adb shell```

###### Найдите папку модема

> Запомните случайное инфо в названии папки (после qcremotefs8150)

```ls /win/Windows/System32/DriverStore/FileRepository/ | grep qcremotefs8150```

###### Сделайте дамп инфо о модеме

> Как до этого, замените случайное инфо этим что вы запомнили ранее

> Проверьте ВВЕЛИ ЛИ ВЫ обе команды

```dd if=/dev/block/by-name/modemst1 of=/win/Windows/System32/DriverStore/FileRepository/qcremotefs8150_[вставьте случайное инфо сюда]/bootmodem_fs1```

```dd if=/dev/block/by-name/modemst2 of=/win/Windows/System32/DriverStore/FileRepository/qcremotefs8150_[вставьте случайное инфо сюда]/bootmodem_fs2```

## Готово!




### Делаем клавиатуру отцепляемой и двигаемой

> [ПРЕДУПРЕЖДЕНИЕ]  
> Делайте эти действия на POCO X3 Pro с запущенной Windows!!!

##### Открытие командной строки

- Откройте пуск
- Напишите в поиск cmd/командная строка
- Зажмите кнопку на командной строке и нажмите "ЗАПУСТИТЬ ОТ ИМЕНИ АДМИНИСТРАТОРА"
- Подтвердите диалоги UAC о открытии от имени администратора

##### Делаем клавиатуру двигаемой

- В командной строке напишите ```reg delete HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\Scaling /v MonitorSize```
- Нажмите 'y' и потом Enter
- Перезапустите телефон (В Windows!)

## Готово!




### Отключение режима хоста USB

> [ПРЕДУПРЕЖДЕНИЕ]
>  Любые не запитанные USB разветлители/hub'ы не будут работать!
>
> Все действия делаются на POCO X3 Pro с запущенной Windows!

##### Открытие командной строки

- Откройте пуск
- Напишите в поиск cmd/командная строка
- Зажмите кнопку на командной строке и нажмите "ЗАПУСТИТЬ ОТ ИМЕНИ АДМИНИСТРАТОРА"
- Подтвердите диалоги UAC о открытии от имени администратора

##### Отключение режима хоста USB

- В командную строку напишите ```reg add "HKLM\SYSTEM\CurrentControlSet\Enum\ACPI\QCOM0597\0\Device Parameters" /v RoleSwitchMode /t REG_DWORD /d 3```
- Перезапустите телефон (В Windows!)

## Готово!
