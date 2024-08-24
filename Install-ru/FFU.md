# Установка образа Full Flash Update (.FFU) на POCO X3 Pro

Данное руководство поможет вам установить FFU содержащий Windows на ваш POCO X3 Pro.

По окончанию на вашем POCO X3 Pro будут установлены и Android, и Windows.

И Android, и Windows разделят внутреннее хранилище в соответствии с конфигурацией, содержащейся в образе FFU.

Android будет загружаться нормально, а для загрузки Windows вам придется использовать ПК, если вы не воспользуетесь руководством по двойной загрузке (об этом позже).

Содержание:

* [Установка образа Full Flash Update (.FFU) на POCO X3 Pro](#установка-образа-full-flash-update-ffu-на-poco-x3-pro)
   * [Необходимые файлы](#необходимые-файлы)
* [Шаги](#шаги)
   * [Разблокировка загрузчика](#разблокировка-загрузчика)
   * [Получение всех файлов](#получение-всех-файлов)
   * [Установка WOA Device Manager](#установка-woa-device-manager)
   * [Переход к загрузчику FFU](#переход-к-загрузчику-ffu)
   * [Установка образа FFU с Windows](#установка-образа-ffu-с-windows)
   * [Запуск Windows](#запуск-windows)
   * [Повторная загрузка Windows после первоначальной установки](#повторная-загрузка-windows-после-первоначальной-установки)

## Необходимые файлы

- [WOA Device Manager](https://github.com/woa-vayu/POCOX3Pro-Guides/releases/download/WDM/WOA_Device_Manager.zip)
- Образ FFU для POCO X3 Pro
- Комьютер на Windows

## Отказ от ответственности

> [!WARNING]
> - Если во время процесса вы видите предупреждение и/или ошибку, это ненормально. Свяжитесь с нами в telegram, если увидите что-то странное, но не действуйте самостоятельно, вы еще больше все испортите.

> [!IMPORTANT]
> **ЭТО СОТРЕТ ВСЕ ДАННЫЕ ANDROID И WINDOWS!**
>
> Мы не несем ответственности за любой ущерб, нанесенный вашему телефону. Следуя данному руководству, вы соглашаетесь нести полную ответственность за свои действия. Мы провели некоторые испытания,
>
> но это **ВСЕ ЕЩЕ НА ЭТАПЕ РАЗРАБОТКИ** и всё может пойти не так.

**ПОЖАЛУЙСТА, ПРОЧИТАЙТЕ И УБЕДИТЕСЬ, ЧТО ПОНЯЛИ ВСЁ РУКОВОДСТВО ПЕРЕД НАЧАЛОМ**

# Шаги 

## Разблокировка загрузчика

Если это еще не сделано, сначала разблокируйте загрузчик. Вернитесь, как только закончите. Если вы уже сделали это, пропустите этот раздел.

## Получение всех файлов

UEFI:
- [Образ UEFI](https://github.com/woa-vayu/POCOX3Pro-Releases/releases/download/2408.19/POCO.X3.Pro.UEFI-v2408.19.img)

[Образ FFU](https://t.me/woavayuffu)

## Установка WOA Device Manager

| Шаги | Примеры |
|-|-|
| Скачайте [WOA Device Manager](https://github.com/woa-vayu/POCOX3Pro-Guides/releases/download/WDM/WOA_Device_Manager.zip) | |
| Распакуйте архив | |
| Откройте ```Install.cmd``` | |
| Следуйте инструкциям на экране. | |
| Откройте WOA Device Manager. | <img align="right" width="425" alt="Screenshot 2024-06-22 183133" src="https://github.com/woa-vayu/POCOX3Pro-Guides/assets/69907487/42be9ce4-2f28-4a36-af40-8ce57243aebc">

Поздравляем, вы успешно установили WOA Device Manager.

## Переход к загрузчику FFU

| Шаги | Примеры |
|-|-|
| Подключите устройство под управлением Android к комьютеру | <img align="right" width="425" alt="Screenshot 2024-06-22 183159" src="https://github.com/woa-vayu/POCOX3Pro-Guides/assets/69907487/9c610f45-4df3-463b-8aae-efde82a4108a"> |
| Перейдите в раздел «Manual Mode» в WOA Device Manager. | <img align="right" width="425" alt="Screenshot 2024-06-22 183227" src="https://github.com/woa-vayu/POCOX3Pro-Guides/assets/69907487/90ea2b5c-c996-4e28-a3c5-3a343c8fbf82"> |
| Нажмите "Switch to Windows-mode" | <img align="right" width="425" alt="Screenshot 2024-06-22 183235" src="https://github.com/woa-vayu/POCOX3Pro-Guides/assets/69907487/f4c6ed5f-572f-4a36-8fcd-0bfae2dd8af6"> |
| Когда на экране устройства появится текст "FASTBOOT", Зажмите громкость вверх пока не увидите такое на экране: | <img align="right" width="425" alt="Screenshot 2024-06-22 183302" src="https://github.com/woa-vayu/POCOX3Pro-Guides/assets/69907487/8b8d8598-1164-4f07-b421-88e147dbd4e8"> |
| WOA Device Manager обнаружит ваше устройство в режиме UFP | <img align="right" width="425" alt="Screenshot 2024-06-22 183302" src="https://github.com/woa-vayu/POCOX3Pro-Guides/assets/69907487/21d3cf3c-1090-491b-9ba4-97a79156591f"> |

> [!TIP]
> Если компьютер не находит ваше устройство, попробуйте использовать порт USB-2. Известны проблемы с UEFI, из-за которых устройство не распознается через порт USB-3.

Поздравляем, теперь вы находитесь в FFU Loader.

## Установка образа FFU с Windows

| Шаги | Примеры |
|-|-|
| Перейдите в раздел "Flash" в WOA Device Manager | <img align="right" width="425" alt="Screenshot 2024-06-22 183326" src="https://github.com/woa-vayu/POCOX3Pro-Guides/assets/69907487/f4c0f9fb-8ce7-408e-82ec-570860bf8be7"> |
| Выберите образ FFU и нажмите "Flash FFU Image" | <img align="right" width="425" alt="Screenshot 2024-06-22 183344" src="https://github.com/woa-vayu/POCOX3Pro-Guides/assets/69907487/9f200e51-00bf-4950-a998-4343f68fdb75"> |
| Теперь вы должны видеть процесс установки и на компьютере | <img align="right" width="425" alt="Screenshot 2024-06-22 183429" src="https://github.com/woa-vayu/POCOX3Pro-Guides/assets/69907487/3a643ab4-680f-4a8e-ac55-2d80de357b51"> |
| и на телефоне, дождитесь завершения установки. | <img align="right" width="425" alt="POCO X3 Pro in FFU Loader mode, flashing" src="https://github.com/woa-vayu/POCOX3Pro-Guides/assets/69907487/37ab28cd-4f69-4288-bfc7-a6a7f476aa9b"> |
| Дождитесь окончания процесса, и вы вернетесь в Android или Recovery. | |

> [!IMPORTANT]
> **ДЕЛАЙТЕ ЭТО ТОЛЬКО В ТОМ СЛУЧАЕ, ЕСЛИ ВЫ ВПЕРВЫЕ УСТАНАВЛИВАЕТЕ FFU**
>
> Если вы впервые прошиваете этот образ FFU, вы потеряете все свои данные Android. Кроме того, Android не сможет успешно загрузиться.
Если это не ваш случай, проигнорируйте этот раздел, Android все равно должен загрузиться нормально.
Если это ваш случай, загрузитесь в стоковый Recovery и сделайте «Сброс к заводским настройкам» или загрузитесь в TWRP и отформатируйте данные.
>

## Запуск Windows 

| Шаги | Примеры |
|-|-|
| Перейдите в раздел «Manual Mode» в WOA Device Manager | <img align="right" width="425" alt="Screenshot 2024-06-22 183227" src="https://github.com/WOA-Project/SurfaceDuo-Guides/assets/3755345/a5fb15b1-6a43-45b5-b440-df243b076b9c"> |
| и нажмите "Switch to Windows-mode". | <img align="right" width="425" alt="Screenshot 2024-06-22 183235" src="https://github.com/WOA-Project/SurfaceDuo-Guides/assets/3755345/bb4f618a-fa7c-4874-8dd6-f87181753be6"> | 

Это нужно будет выполнять каждый раз, когда вы захотите загрузить Windows, и делать это нужно будет из режима загрузчика.

Если вы все сделали правильно, Windows загрузится! Наслаждайтесь!

Позвольте Windows пройти начальную настройку и вернитесь, когда вы окажетесь на рабочем столе Windows на POCO X3 Pro.

> [!NOTE]
> Если сенсорная клавиатура не отображается в OOBE, нажмите в другом месте (чтобы текстовое поле потеряло фокус), а затем снова коснитесь текстового поля. В качестве альтернативы можно использовать экранную клавиатуру.

> [!NOTE]
> Если при начальной настройке вы получаете BSOD (экран проверки ошибок), попробуйте стереть разделы esp и win с помощью «fastboot erase esp» и «fastboot erase win» и перепрошить образ FFU, после чего все должно заработать. Эта проблема будет исправлена в последующих ревизиях FFU.

## Повторная загрузка Windows после первоначальной установки

У вас есть два способа загрузки Windows.

- Ручная загрузка с помощью PC
    - Плюсы: Вы можете свободно обновлять Android
    - Минусы: Вам понадобится ПК для загрузки в Windows

- Установка Dual Boot
    - Плюсы: Вы сможете загружать Windows прямо с устройства.

Если вам нужен Dual Boot, следуйте [этому руководству](/Install-ru/DualBoot.md)
