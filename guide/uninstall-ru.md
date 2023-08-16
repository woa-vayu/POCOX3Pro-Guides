<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Запуск Windows на Poco X3 PRO

## Удаление

### Для чего это пригодится?

Если вы следовали старой инструкции, ваша таблица разделов будет отличаться. Сперва ее нужно восстановить (только по старому методу).

Если вы хотите удалить Windows, то можно использовать оба метода.

### Необходимые файлы

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)
- [gpt_both0.bin](../../../releases/tag/binaries) (старый метод)
- [Модифицированный TWRP](../../../releases/Recoveries) (новый метод)

#### Новый метод

##### Установите и запустите модифицированный TWRP

```cmd
fastboot flash recovery path\to\twrp.img 
fastboot reboot recovery
```

##### Запустите скрипт восстановления

```cmd
adb shell restore
```

##### Готово!

#### Старый метод (если новый не сработал)

##### Восстановите GPT 
> Замените ```path\to\gpt_both0.bin``` действительным путем до gpt_both0.bin

```cmd
fastboot flash partition:0 path\to\gpt_both0.bin
```

##### Отформатируйте userdata
```cmd
fastboot -w
```
