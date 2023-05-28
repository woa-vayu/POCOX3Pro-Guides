<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Windows en el POCO X3 Pro

## Dualboot entre Android y Windows

### Requisitos previos

- [Magisk](https://github.com/topjohnwu/Magisk/releases/latest)

- [ADB & Fastboot](https://developer.android.com/studio/releases/platform-tools)

- [TWRP/OFOX](../../../../releases/Recoveries)

- [NTFS Android Magisk Module](../../../../releases/ntfsdroid)

- [UEFI](https://github.com/woa-vayu/edk2-msm/releases/latest)

- [UEFI & Android Boot Flashing App](../../../../releases/dualboot)

### Preparar el teléfono

#### Añadir soporte a NTFS en android

- Installa Magisk si no lo tenías ya
- Installa el módulo de NTFS Android en Magisk manager

#### Preparar la aplicación

- Instala el APK proporcionado
- Crea una carpeta llamada "UEFI" en tu almacenamiento interno
- Copie todas las imágenes uefi en esa carpeta con el esquema de nombres vayu-(panel)-(version).img
- Abre la aplicación y dale todos los permisos de root que pida

### Parte en el Pc

#### Arrancar el recovery

- Reinicia al bootloader

- Pon ```fastboot boot <recovery.img>``` (Sustituye <recovery.img> por el recovery que elegiste)

#### Transfiere algunos archivos al teléfono

- Cuando el recovery inicie pon ```adb shell mount.ntfs /dev/block/by-name/win /win```
- Pon ```adb shell dd if=/dev/block/by-name/boot of=/win/boot.img```
- Pon ```adb push switchtoandroid.exe /win/Users/<username>/Desktop/switchtoandroid.exe``` (Sustituye <username> por el nombre de usuario de tu partición de windows)
  
#### Arrancar android
  
  - Abre switchtoandroid.exe en el teléfono como **ADMINISTRADOR**

#### Arrancar windows
  
  - Abre la app
  - Presisona "Quickboot to windows"
