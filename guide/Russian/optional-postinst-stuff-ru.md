<img align="right" src="https://github.com/wormstest/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Запуск Windows на POCO X3 Pro

## Необязательный пост-установочный материал

### Запуск датчиков

#### Предпосылки

- [Модифицированный TWRP или OrangeFox](../../../../releases/Recoveries)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

##### Установите и загрузите модифицированное рекавери

```fastboot flash <recovery.img> reboot recovery```

##### Монтирование разделов

- Зайдите в вкладку "монтирование" ("mount" на английском)
- Смонтируйте persist и win разделы

##### Запуск сенсоров

###### Запустите ADB shell

```adb shell```

###### Удалите все остаточные файлы от Qualcomm

```rm -rf /win/Windows/System32/drivers/DriverData/QUALCOMM/fastRPC/persist/sensors```

###### Скопируйте данные датчиков

```cp -r /persist/sensors /win/Windows/System32/drivers/DriverData/QUALCOMM/fastRPC/persist/sensors```

## Готово!
