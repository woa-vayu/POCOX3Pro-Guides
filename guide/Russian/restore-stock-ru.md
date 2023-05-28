<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Запуск Windows на POCO X3 Pro

## Удаление

### Зачем это нужно?

Если вы использовали старую инструкцию, ваша разметка будет отличаться с нынешней, и могут быть плохие последствия, если вы не восстановите стандартную таблицу разделов. 

Если вы хотите удалить Windows, эта инструкция поможет легко вернуть таблицу стандартную разделов

Если вы хотите повторно заблокировать загрузчик, вам понадобится стандартная таблица разделов.

### Требовавния

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)
- [gpt_both0.bin](../../../../releases/tag/binaries)

### Возвращение таблицы разделов
> Замените  ```<gpt_both0.bin>``` на путь к файлу gpt_both0.bin.

```cmd
fastboot flash partition:0 <gpt_both0.bin>
```

### Очистка userdata, чтобы избежать bootloop и восстановить размер файловой системы
```cmd
fastboot -w
```