<img align="right" src="https://github.com/woa-vayu/src_vayu_windows/blob/main/2Poco X3 Pro Windows.png" width="350" alt="Windows 11 Running On A Poco X3 Pro">


# Useful apps and instructions for Windows on POCO X3 Pro

### List of supported apps/games
This is by no means a comprehensive list, it simply lists apps/games that have been tested by the community
[The link can be found here](https://docs.google.com/spreadsheets/d/1XYuoySgYQE0HL573sA-0RGMX7I4lt5rWJuQ8Z8yRJNY/edit?usp=drivesdk)

You can also find a list of dedicated ARM software [at this link](https://armrepo.ver.lt/)

#### Finished!

## Hide D drive (modem partition)
> [!NOTE]
> This is recommended because this drive should not be modified, while some applications may try to write to it

- Open a command prompt window and run ```diskpart```
- Run ```list volume``` to see all available volumes
- Select the disk that has letter D with ```select volume $```, replacing "$" with the volume number
- Remove the letter with ```remove letter d```
- Exit diskpart with ```exit```

#### Finished!


## Enabling/Disabling USB host mode
> [!Warning]
> Unpowered USB devices will stop working with USB host mode disabled

Run [USB Host Control](https://github.com/erdilS/Port-Windows-11-Xiaomi-Pad-5/releases/tag/USBHost) to enable/disable USB host mode and then confirm that you want to disable/enable USB host mode 

#### Finished!


## Install Microsoft Office / Microsoft 365
- Download this [ISO file](https://mega.nz/file/hjAiSL4T#G7kOKpsUFpyL2UW9RQmY2e96urcQW5xZKdc7ciaNOy8) to the phone 
- Right-click on the iso file and select Mount to open it in explorer
- Double-click on ```Office Tool Plus.exe``` to start the installation wizard
- In the window that appears, click `Yes`
- Wait for the installation to complete

#### Finished!


## Activate Windows / Office
Follow the instructions by Massgravel [here](https://github.com/massgravel/Microsoft-Activation-Scripts)

#### Finished!


### Making the keyboard float

> [!WARNING]  
> Make sure these steps are done on the POCO X3 Pro running Windows!

##### Opening the command prompt as an administrator

> This is self explanatory, this opens the command prompt as administrator

- Go to the start menu
- Search command prompt
- Hold the command prompt application and run it as administrator
- Approve any UAC dialogs

##### Making the keyboard float

> This deletes the registry key that tells the keyboard the size of our screen and makes it float again

- In the command prompt put ```reg delete HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\Scaling /v MonitorSize```
- Press 'y' then enter
- Reboot your phone

## Finished!



















