# Useful apps and instructions for Windows on POCO X3 Pro

## List of supported apps/games

This is by no means a comprehensive list, it simply lists apps/games that have been tested by the community
[The link can be found here](https://docs.google.com/spreadsheets/d/1XYuoySgYQE0HL573sA-0RGMX7I4lt5rWJuQ8Z8yRJNY/edit?usp=drivesdk)

You can also find a list of dedicated ARM software [at this link](https://armrepo.ver.lt/)

##### Finished!

## Hide D drive (modem partition)
>
> [!NOTE]
> This is recommended because this drive should not be modified, while some applications may try to write to it.

- Open a command prompt window and run ```diskpart```
- Run ```list volume``` to see all available volumes
- Select the disk that has letter D with ```select volume $```, replacing "$" with the volume number
- Remove the letter with ```remove letter d```
- Exit diskpart with ```exit```

##### Finished!

## Install Microsoft Office / Microsoft 365

- Download this [ISO file](https://mega.nz/file/dnhQ3Q6b#X0o_B9eEPRa_IaPojQ-z1sLdqMgXkEQXqxfm2P0jL0I) to the tablet
- Right-click on the iso file and select Mount to open it in explorer
- Double-click on ```Office Tool Plus.exe``` to start the installation wizard
- Approve any UAC dialogs
- In the window that appears, click `Yes` to start installation
- Wait for the installation to complete

##### Finished!

## Activate Windows / Office

Follow the instructions by Massgravel [here](https://github.com/massgravel/Microsoft-Activation-Scripts)

##### Finished!

## Making the keyboard float
>
> [!WARNING]  
> Make sure these steps are done on the POCO X3 Pro running Windows!

- Open CMD as an admin and run ```reg delete HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\Scaling /v MonitorSize```
- Press 'y' then enter
- Reboot your phone

##### Finished!

## Disabling USB host mode
> [!Warning]
> Unpowered USB devices will stop working

> [!Important]
> The following steps must be done on your phone in Windows, not on your computer. 

> This edits the registry key to tell the USB Controller not to put the device into host mode
- In the command prompt put ```reg add "HKLM\SYSTEM\CurrentControlSet\Enum\ACPI\QCOM0597\0\Device Parameters" /v RoleSwitchMode /t REG_DWORD /d 3```
- Reboot your phone

##### Finished!
