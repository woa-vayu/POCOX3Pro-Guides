<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Полезные приложения и инструкции для Windows на POCO X3 Pro

### Список поддерживаемых приложений/игр
Это ни в коем случае не полный список, в нём просто перечислены приложения/игры, которые были протестированы сообществом
[The link can be found here](https://docs.google.com/spreadsheets/d/1XYuoySgYQE0HL573sA-0RGMX7I4lt5rWJuQ8Z8yRJNY/edit?usp=drivesdk)

Вы также можете ознакомиться со списком специализированного программного обеспечения ARM [по этой ссылке](https://armrepo.ver.lt/)

#### Готово!

## Скрыть диск D (раздел modem)
> [!NOTE]
> Это рекомендуется, поскольку этот диск не следует модифицировать, а некоторые приложения могут попытаться выполнить запись на него

- Откройте окно командной строки и введите ```diskpart```
- Выполните ```list volume``` чтобы отобразить доступные диски 
- Выберите диск который имеет букву D используя команду ```select volume $```, заменяя "$" номером диска 
- Удалите букву используя ```remove letter d```
- Выйдите из diskpart при помощи ```exit```

#### Finished!


## Выключение режима USB host 
> [!Warning]
> USB устройства без дополнительного питания перестанут работать 

Запустите [USB Host Mode Control](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/download/USBHost/USB.Host.Mode.Control.V6.0.vbs) чтобы включить/отключить режим USB-хоста, а затем подтвердите, что вы хотите включить/отключить режим USB-хоста

#### Готово!


## Установка Microsoft Office / Microsoft 365
- Скачайте этот [ISO файл](https://mega.nz/file/hjAiSL4T#G7kOKpsUFpyL2UW9RQmY2e96urcQW5xZKdc7ciaNOy8) на телефон 
- Щёлкните правой кнопкой мыши по iso и выберите `Смонтировать`, чтобы открыть его в проводнике
- Дважды щёлкните по `Office Tool Plus.exe`, чтобы запустить мастер установки
- В появившемся окне нажмите `Да`
- Дождитесь завершения установки
- Наслаждайтесь Office и не забудьте активировать его 
#### Готово!


## Активация Windows / Office
Следуйте инструкциям от Massgravel [сдесь](https://github.com/massgravel/Microsoft-Activation-Scripts)

#### Готово!


### Настройка модема 

> [!WARNING]  
> Вам нужно будет делать это каждый раз перед загрузкой Windows, если вы хотите использовать LTE!

> [!NOTE]
> Вам не нужно этого делать, если вы используете WoA Helper

#### Настройка модема автоматически (более быстрый и простой способ)

#### Требования 
- Установленный Magisk или TWRP
- [Zip-файл для настройки модема](https://github.com/woa-vayu/Port-Windows-11-POCO-X3-Pro/releases/tag/modemprov)

##### Прошейте zip-файл для настройки модема

> Это очень просто, откройте Magisk (или загрузитесь в TWRP), установите zip, который сделает всю тяжёлую работу за вас

- Откройте Magisk (или загрузитесь в TWRP)
- Перейдите к выбору модуля (кнопка "Install" в TWRP)
- Прошейте zip
- Загрузитесь в Windows

## Готово!

#### Настройка модема вручную (более длительный/сложный метод)

#### Требования 

- [Модифицированное TWRP](../../../releases/Recoveries)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

##### Прошейте и загрузитесь в модифицированное recovery

> This is self explanatory, it flashes the recovery then reboots into the recovery

```fastboot flash recovery путь\к\twrp.img reboot recovery```

##### Монтирование разделов 

> Also self explanatory, this will mount the windows partitions

- Перейдите в меню монтирования
- Смонтируйте раздел **win**

##### Start ADB Shell

> Starts a shell on your computer used to communicate with your phone over ADB

```adb shell```

##### Finding the modem folder

> Take note of the random data in that folder name (after qcremotefs8150)

> This looks for the Qualcomm remotefs driver folder

```ls /win/Windows/System32/DriverStore/FileRepository/ | grep qcremotefs8150```

##### Дамп данных модема

> Как и раньше, replace the random data with the one that you noted down before

> Убедитесь, что вы выполняете **ОБЕ** команды

> Это выполнит дамп данных модема в папку remote fs, окончательно починив модем

```dd if=/dev/block/by-name/modemst1 of=/win/Windows/System32/DriverStore/FileRepository/qcremotefs8150_[insert random data here]/bootmodem_fs1```

```dd if=/dev/block/by-name/modemst2 of=/win/Windows/System32/DriverStore/FileRepository/qcremotefs8150_[insert random data here]/bootmodem_fs2```

## Готово!

### Сделать клавиатуру плавающей 

> [!WARNING]  
> Убедитесь, что эти действия выполнены на POCO X3 Pro под управлением Windows!

##### Открытие командной строки от имени администратора

> Это говорит само за себя, при этом открывается командная строка от имени администратора

- Перейдите в меню "Пуск"
- Веедите в поиск "командная строка"
- Удерживайте приложение командной строки и запустите его от имени администратора.
- Одобряйте любые диалоги контроля учетных записей

##### Сделайте клавиатуру плавающей 

> При этом удаляется параметр реестра, который сообщает клавиатуре размер нашего экрана, и она снова становится плавающей

- В командной строке вставьте команду ```reg delete HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\Scaling /v MonitorSize```
- Введите 'y', а затем нажмите enter
- Перезагрузите ваш телефон 

## Готово!
