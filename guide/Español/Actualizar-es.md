<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Windows en el POCO X3 Pro

## Actualizar Drivers

### Requisitos Previos

- [UEFI](https://github.com/woa-vayu/edk2-msm/releases/latest)
- [TWRP/OFOX Modificado](../../../../releases/Recoveries)
- [DriverUpdater](https://github.com/WOA-Project/DriverUpdater/releases/latest)
- [Drivers](https://github.com/woa-vayu/Vayu-Drivers/releases/latest)

#### Iniciar TWRP desde el pc con el comando

```cmd
fastboot boot <twrp.img>
```

> Si ya tienes el TWRP instalado, solo presiona el botón de encendido y vol+ para iniciarlo


#### Ejecutar el script

```cmd
adb shell msc.sh
```

### Asignar Letras A Los Discos

#### Iniciar El Administrador De Discos De Windows

> Cuando el X3 Pro sea detectado como disco

```cmd
diskpart
```


### Asignar la letra `X` a la partición de Windows

#### Seleccione el volumen de Windows del teléfono
> Usa `list vol` para encontrarlo, es el que se llama "WINVAYU"

```diskpart
sel vol <number>
```

#### Asignar la letra X
```diskpart
assign letter=x
```

#### Salir de diskpart
```diskpart
exit
```


### Instalar Los Drivers

> Reemplaza `<vayudriversfolder>` por la localización de la carpeta de los drivers

> Abre un cmd como administrador


```cmd
DriverUpdater.exe -d <vayudriversfolder>\definitions\Desktop\ARM64\Internal\vayu.txt -r <vayudriversfolder> -p X:
```


### Arranca Windows con la UEFI

```
fastboot flash boot <uefi.img>
```

## ¡Terminado!
