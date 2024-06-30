<img align="right" src="https://github.com/woa-vayu-archive/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Запуск Windows на POCO X3 Pro

## Переустановка 
Если вам не нравится ваша версия Windows, или вы совершили ошибку при установке, или что-то ещё, вам нужно просто переустановить Windows. К счастью, этот процесс очень прост.

> [!IMPORTANT]
> Совершенно очевидно, что это приведет к удалению всех ваших файлов в Windows. Если вы хотите создать резервную копию, вы можете сделать это, смонтировав Windows с помощью приложения [WOA Helper](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/download/dualboot/woahelper.apk) и вручную скопировав любые файлы, которые вы хотите сохранить


### Требования 

- ```Существующие разделы Windows и ESP``` (*If not met, [go back and just pretend this guide never existed](/guide/English/install-1-en.md)*)

- [```Образ recovery```](https://github.com/woa-vayu-archive/POCOX3Pro-Guides/releases/tag/Recoveries)

- [```Android platform tools```](https://developer.android.com/studio/releases/platform-tools)

#### Загрузитесь в TWRP
> Замените `<recovery.img>` действительным путём к recovery.img
> Если ваше recovery было заменено стоковым, прошейте его снова используя
```cmd
fastboot flash recovery <recovery.img> reboot recovery
```

### Отформатируйте разделы
> Если он попросит вас запустить его ещё раз, сделайте это
```cmd
adb shell format
```

## [Следующий шаг: Переустановка Windows](/guide/English/install-2-en.md)
  
