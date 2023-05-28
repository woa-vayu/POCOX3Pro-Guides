# Instalar Windows
> Necesitas tener el  MTP desactivado en Mount

### Requisitos Previos

- [Windows para ARM (Windows 11 es el recomendado)](https://uupdump.net/)
- [UEFI](https://github.com/woa-vayu/edk2-msm/releases/latest)
- [DriverUpdater](https://github.com/WOA-Project/DriverUpdater/releases/latest)
- [Drivers](https://github.com/woa-vayu/Vayu-Drivers/releases/latest)

## Pasar las herramientas necesarias:
```cmd
adb push msc.sh /sbin
```

### Ejecutar el script

```cmd
adb shell sh /sbin/msc.sh
```

  

## Asignar letras a los discos
  

#### Arranca el administrador de discos de Windows

> Cuando el X3 Pro sea detectado como un disco

```cmd
diskpart
```


### Asignar letra `x` al volumen de Windows

#### Selecciona el volumen de Windows del Teléfono
> usa `list volume` para encontrarlo, normalmente es el penúltimo

```diskpart
select volume <number>
```

#### Assign the letter x
```diskpart
assign letter=x
```

### Asinar `y` al volumen de esp 

#### Selecciona el volumen de esp del teléfono
> usa `list volume` para encontrarlo, normalmente es el último

```diskpart
select volume <number>
```

#### Asignar letra y

```diskpart
assign letter=y
```

### Salir de diskpart:
```diskpart
exit
```

  
  

## Instalar

> reemplaza `<path/to/Install.wim>` por la ruta del archivo install.wim

> `install.wim` está en la carpeta sources de la ISO
> lo puedes obtener tras montar o extraer la ISO

```cmd
dism /apply-image /ImageFile:<path/to/install.wim> /index:1 /ApplyDir:X:\
```

  
  
  
  # Comprueba que tipo de panel tienes

> En TWRP ve a Advanced, Terminal

 ```cmd
 cat /proc/cmdline
```
> Mira el panel en `msm_drm.dsi_display0` casi abajo del todo

> si tu dispositivo es `<tianma>``msm_drm.dsi_display0` será `dsi_j20s_36_02_0a_video_display`

> si tu dispositivo es `<huaxing>`: `msm_drm.dsi_display0` será `dsi_j20s_42_02_0b_video_display` y tendrás que ir a la carpeta de drivers (Vayu-Drivers/components/QC8150/Device/DEVICE.SOC_QC8150.VAYU/Drivers/Touch/) y borra j20s_novatek_ts_fw01.bin, por último renombra j20s_novatek_ts_fw02.bin a j20s_novatek_ts_fw01.bin

# Instalar los Drivers

> reemplaza `<vayudriversfolder>` por la localización de la carpeta de drivers

> abre un cmd como Administrador

```cmd
driverupdater.exe -d <vayudriversfolder>\definitions\Desktop\ARM64\Internal\vayu.txt -r <vayudriversfolder> -p X:
```

  

# Crear los archivos del bootloader de Windows 

```cmd
bcdboot X:\Windows /s Y: /f UEFI
```

  
  

# Permite los drivers no firmados

> si no haces esto obtendrás un BSOD

```cmd
bcdedit /store Y:\EFI\Microsoft\BOOT\BCD /set "{default}" testsigning on
```

# Arrancar en Windows
> Recomiendo tener una microSD en la que almacene las imágenes de arranque

> para que no necesites una pc para pasar los archivos.

### Mueve `<uefi.img>` al dispositivo

```cmd
adb push <uefi.img> /sdcard
```

##### si tienes una micro sd usa este

```cmd
adb push <uefi.img> /external_sd
```


### haz un backup de tu imagen de arranque actual
> solo tienes que hacer esto una vez

> ponla en tu micro sd si es posible


### Flashea la imagen uefi desde twrp.
ve hasta la `uefi.img` y flashea en boot.

# volver a Android
> usa tu backup de boot image desde twrp.

# ¡Terminado!
