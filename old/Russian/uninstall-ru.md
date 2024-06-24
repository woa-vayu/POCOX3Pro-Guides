<img align="right" src="https://github.com/woa-vayu-archive/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">

# Запуск Windows на POCO X3 Pro

## Удаление 

### Зачем это нужно?
Если вы хотите удалить Windows, этот гайд используется вместо удаления разделов вручную, а также чтобы избежать ошибки.

Если вы хотите заблокировать загрузчик, вам потребуется, чтобы таблица разделов была стоковой
### Prerequisites
- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)
  
- [Образ recovery](https://github.com/woa-vayu-archive/Port-Windows-11-POCO-X3-Pro/releases/tag/Recoveries)

### Прошейте и загрузите модифицированное recovery
> Замените `<recovery.img>` путём к образу recovery
```cmd
fastboot flash recovery <recovery.img> reboot recovery
```

#### Восстановите таблицу разделов 
> [!Warning]
> Это приведет к удалению файлов Android. При необходимости сначала создайте резервную копию.
```cmd
adb shell restore
```

### Перезагрузитесь в Android 
```cmd
adb reboot 
```

## Готово!
