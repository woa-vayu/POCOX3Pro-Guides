<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Запуск Windows на POCO X3 PRO

## Установка

## Разметка телефона

### Необходимые файлы

- [Модифицированный TWRP](../../../releases/Recoveries)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

### 
> [!WARNING]
> Если вы попытаетесь удалить какой-либо раздел через diskpart, Windows отправит UFS команду, которая ОЧИСТИТ ВСЮ ПАМЯТЬ!!! Не делайте этого.
> 
> Все ваши данные будут удалены! Сохраните важную информацию.
> 
> Не запускайте команды дважды.
> 
> НЕ ПЕРЕЗАПУСКАЙТЕ ТЕЛЕФОН если думаете, что совершили ошибку. Обратитесь за помощью в наш [Telegram чат](https://t.me/winonvayualt).
> 
>
> Не запускайте команды вразброс, вводите их по очереди!!

##### Установите модифицированный TWRP
```cmd
fastboot flash recovery path\to\twrp.img
fastboot reboot recovery
```

##### Запустите скрипт разметки

> Если скрипт попросит запустить его еще раз, то так и сделайте

```cmd
adb shell partition
```

#### Проверьте, запускается ли Android
Просто перезапустите телефон. Если Android загружается и работает, то вы все сделали правильно.


## [Следующие этапы: Установка Windows](/guide/install-2-ru.md)
