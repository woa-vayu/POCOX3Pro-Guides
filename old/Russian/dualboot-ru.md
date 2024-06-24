<img align="right" src="https://github.com/woa-vayu-archive/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">

# Запуск Windows на POCO X3 Pro

## Двойная загрузка Android и Windows

### Требования 
- Рутированный vayu с уже установленной Windows
- [Образ Secure Boot UEFI](https://github.com/woa-vayu-archive/msmnilePkg/releases/latest)
- [M3K WoA Helper](https://github.com/woa-vayu-archive/WoA-Helper-M3K/releases/latest)
- [StA Installer](https://github.com/woa-vayu-archive/Port-Windows-11-POCO-X3-Pro/releases/tag/dualboot)

## Настройка приложения dualboot
> В этом гайде предполагается, что у вас есть root, если это не так, пожалуйста, сделайте это в первую очередь

### Установка - Android
- Скачайте и установите приложение **M3K WoA Helper**, затем откройте его и предоставьте ему root-доступ.
- Скачайте **образ Secure Boot UEFI** для вашего дисплея и поместите его в папку `UEFI` в вашем внутреннем хранилище.
- Нажмите кнопку `MOUNT WINDOWS`, затем скачайте и переместите **StA_Installer_vayu.exe** в только что созданную папку `Windows` в вашем внутреннем хранилище.
- Вернитесь в приложение M3K WoA Helper и нажмите `QUICKBOOT TO WINDOWS`.
  
> [!NOTE]
> Первая загрузка в Windows может занять до 10 минут, не волнуйтесь и просто подождите

### Установка - Windows
- Перейдите к `C:\StA_Installer_vayu.exe` и запустите его. Если это не сработает, убедитесь, что все антивирусные программы отключены, так как они, вероятно, не позволят приложению запуститься

#### Загрузка в Android
- Запустите новый ярлык на своем рабочем столе (вы также можете прикрепить его к меню "Пуск" / панели задач для удобства доступа).

#### Загрузка в Windows
- Нажмите `QUICKBOOT TO WINDOWS` в приложении или воспользуйтесь недавно созданным переключателем на панели быстрых настроек
  
## Готово!

