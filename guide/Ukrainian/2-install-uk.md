# Розгортання образу Windows
> Вам потрібно буде вимкнути MTP в розділі "Монтування"

### Запустіть скрипт msc.sh
```cmd
adb shell msc.sh
```

### Призначення літер розділам
> Коли ваш телефон визначився як диск запустіть diskpart
```diskpart
Використовуйте list vol для того, щоб знайти розділи Windows і ESP, вони називаються "WINVAYU" і "ESPVAYU".
# select volume <win-partition-number>
# assign letter=x
# select volume <esp-partition-number>
# assign letter=y
# exit
```

> Замініть `<path\to\install.wim>` дійсним шляхом до `install.wim`, він знаходиться у теці `sources` всередині вашого ISO. Ви можете отримати цей файл розпакувавши або смонтувавши його.
```cmd
dism /apply-image /ImageFile:<path/to/install.wim> /index:1 /ApplyDir:X:\
```

### Створіть файли завантажувача Windows
```cmd
bcdboot X:\Windows /s Y: /f UEFI
```

### Дозвольте непідписані драйвера
> Якщо ви цього не зробите, то отримаєте BSOD
```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" testsigning on
```

### Встановлення драйверів
#### Дізнайтесь, який у вас тип панелі
> Перейдіть у теку `platform-tools`
```cmd
adb shell cat /proc/cmdline
```
> Шукайте екран майже в самом низу
> Якщо ваш пристрій `Tianma`, то `msm_drm.dsi_display0` буде `dsi_j20s_36_02_0a_video_display`
> Якщо ваш пристрій `Huaxing`, то `msm_drm.dsi_display0` буде `dsi_j20s_42_02_0b_video_display`. Вам треба перейти до папки драйверів `Vayu-Drivers/components/QC8150/Device/DEVICE.SOC_QC8150.VAYU/Drivers/Touch/`, видалити j20s_novatek_ts_fw01.bin, і перейменувати j20s_novatek_ts_fw02.bin в j20s_novatek_ts_fw01.bin

> Замініть `<vayudriversfolder>` шляхом к теці с вашими драйверами
```cmd
driverupdater.exe -d <vayudriversfolder>\definitions\Desktop\ARM64\Internal\vayu.txt -r <vayudriversfolder> -p X:
```

### Завантаження Windows

<details> 
<summary><strong>Подвійне завантаження між Android та Windows</strong></summary>

- [Ви маєте переглянути цей посібник](dualboot-uk.md)
  
</details>

<details> 
<summary><strong>Ручне завантаження Windows кожного разу</strong></summary>
 
Перезавантажте телефон у fastboot, потім завантажте UEFI:
  
```fastboot
fastboot boot <uefi.img>
```
При перезавантаженні буде завантажуватись Android, для завантаження у Windows вам потрібно знов завантажити UEFI.
  
</details>  
  
- Якщо ви маєте BSOD з кодом помилки BOUND_IMAGE_UNSUPPORTED під час першого завантаження Windows, вам потрібно використовувати [старий UEFI](https://github.com/woa-vayu/Port-Windows-11-Poco-X3-pro/releases) для першого завантаження (тачскрін не працює у старій версії UEFI).

# Готово!
