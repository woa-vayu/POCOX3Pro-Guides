<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">

# Запуск Windows на POCO X3 Pro

## Установка 
> [!NOTE]
> It is recommended to open CMD or powershell as an admin now, if you haven't already on the last page, and then access the platform-tools folder using the `cd C:\path\to\platform-tools` command, replacing the path with the actual path of the folder.
> Use the same window in the entire guide, do not close it.

### Требования 
- [ARM Windows esd](https://worproject.com/esd) (Выберите - Version:  ```11``` Build:  ```22631.2861``` Architecture:  ```ARM64``` Edition:  ```CLIENT``` Language:  ```выберите ваш язык```)

- [Драйвера](https://github.com/woa-vayu/Vayu-Drivers/releases/latest)

- [Образ recovery](https://github.com/woa-vayu-archive/Port-Windows-11-POCO-X3-Pro/releases/tag/Recoveries) (should already be installed)

### Загрузитесь обратно в recovery что бы начать установку Windows
> Замените `<recovery.img>` действительным путём к recovery.img
> Если ваше recovery было заменено стоковым, прошейте его снова используя
```cmd
fastboot flash recovery <recovery.img> reboot recovery
```

#### Запустите msc 
> Если он попросит вас запустить его ещё раз, сделайте это
```cmd
adb shell msc
```

### Diskpart
> [!WARNING]
> НЕ УДАЛЯЙТЕ, НЕ СОЗДАВАЙТЕ И НЕ ИЗМЕНЯЙТЕ КАКИМ-ЛИБО ИНЫМ ОБРАЗОМ РАЗДЕЛЫ, НАХОДЯСЬ В DISKPART!!! ЭТО МОЖЕТ ПРИВЕСТИ К УДАЛЕНИЮ UFS ИЛИ НЕВОЗМОЖНОСТИ ЗАГРУЗКИ В FASTBOOT!!! ЭТО ОЗНАЧАЕТ, ЧТО ВАШЕ УСТРОЙСТВО БУДЕТ ОКИРПИЧЕНО БЕЗ КАКОГО-ЛИБО РЕШЕНИЯ! (за исключением доставки устройства в Xiaomi или его прошивки с помощью EDL, и то, и другое, скорее всего, будет стоить денег)

```cmd
diskpart
```

#### Выберите раздел Windows телефона
> Используйте `list volume` чтобы найти его, замените "$" номером раздела **WINVAYU**
```diskpart
select volume $
```

#### Привяжите букву X
```diskpart
assign letter x
```

#### Выберите раздел ESP телефона
> Используйте `list volume` чтобы найти его, замените "$" номером раздела **ESPVAYU**
```diskpart
select volume $
```

#### Привяжите букву Y
```diskpart
assign letter y
```

#### Выйдите из diskpart
```diskpart
exit
```

### Установка Windows
> Замените `<путь\к\install.esd>` путём к файлу install.esd (он также может называться install.wim)

```cmd
dism /apply-image /ImageFile:<путь\к\install.esd> /index:6 /ApplyDir:X:\
```

> Если вы получите `Error 87`, проверьте индекс вашего образа используя `dism /get-imageinfo /ImageFile:<путь\к\install.esd>`, затем замените `index:6` индексом Windows 11 Pro в вашем образе

### Установка драйверов 
Распакуйте архив драйверов который вы скачали ранее и запустите файл `OfflineUpdater.cmd` 
> Когда скрипт запросит у вас букву диска, введите X:
  
#### Создайте файлы загрузчика Windows 
> Если при копировании загрузочных файлов возникает ошибка, проверьте `diskpart`, чтобы узнать, имеет ли **ESPVAYU** букву Y. Если нет, добавьте любую другую букву (например, K) и замените Y в приведенной ниже команде на указанную букву 
```cmd
bcdboot X:\Windows /s Y: /f UEFI
```

#### Удалите букву диска ESPVAYU
> Если вы получите ошибку, проигнорируйте это и перейдите к следующей команде. Фантомный диск исчезнет при следующей перезагрузке компьютера.
```cmd
mountvol y: /d
```

### Перезагрузитесь в Android
```cmd
adb reboot
```

> Настройте своё устройство, затем перейдите к последнему шагу

## [Последний шаг: Настройка Dualboot](/guide/Russian/dualboot-ru.md)
