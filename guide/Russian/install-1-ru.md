<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">

# Запуск Windows на POCO X3 Pro

## Разметка устройства 

### Требования 
- Разблокированный загрузчик 

- Мозг 
  
- [Образ recovery](https://github.com/woa-vayu-archive/Port-Windows-11-POCO-X3-Pro/releases/tag/Recoveries)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

### Примечание:
> [!Warning]
> Все пользовательские файлы будут удалены! Создайте резервную копию, если это необходимо.
> 
> НЕ ПЕРЕЗАГРУЖАЙТЕ ВАШ ТЕЛЕФОН! Если вы считаете, что совершили ошибку, обратитесь за помощью в [Telegram chat](https://t.me/winonvayualt).

> [!IMPORTANT]
> Убедитесь, что вы используете модифицированный TWRP на протяжении всего процесса установки, поскольку мы предоставляем инструменты, которые помогут облегчить процесс установки и максимально упростят его для вас.
> 
> Если вы не воспользуетесь им и столкнётесь с какими-либо ошибками, считайте, что это ваша вина, и считайте, что вы одиноки, если попытаетесь обратиться за поддержкой, поскольку вы отклонились от основного руководства.

> [!NOTE]
> Не знаете как начать? Просто извлеките загруженные [```Android platform tools```](https://developer.android.com/studio/releases/platform-tools), например  ```"C:\platform-tools"```, затем откройте ```командная строка``` или `powershell` от имени администратора и введите:
```cmd
cd "путь\к\platform-tools"
```
> Замените  `"путь\к\platform-tools"` действительным путём к папке platform tools
>
> Используйте это окно на протяжении всего процесса установки. Не закрывайте его.

### Прошейте модифицированный TWRP
> Замените `<recovery.img>` действительным путём к recovery.img
```cmd
fastboot flash recovery <recovery.img> reboot recovery
```

#### Запустите скрипт разметки 
> Замените **$** объёмом памяти, который вы хотите выделить для Windows (не добавляйте ГБ, просто введите число).
> 
> Если скрипт попросит запустить его ещё раз, то так и сделайте
```cmd
adb shell partition $
```

### Проверьте, запускается ли Андроид
Просто перезагрузите телефон и проверьте запускается ли Android 
```cmd
adb reboot
```
## [Следующий шаг: Установка Windows](install-2-ru.md)
