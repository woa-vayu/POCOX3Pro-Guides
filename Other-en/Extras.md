# Additional materials

## List of supported apps/games
This is by no means a comprehensive list, it simply lists apps/games that have been tested by the community
[The link can be found here](https://docs.google.com/spreadsheets/d/1XYuoySgYQE0HL573sA-0RGMX7I4lt5rWJuQ8Z8yRJNY/edit?usp=drivesdk)

You can also find a list of dedicated ARM software [here](https://armrepo.ver.lt/)

## Enabling/Disabling USB Host mode

> [!WARNING]
>  Unpowered USB devices will stop working with USB host mode disabled
>
> Make sure these steps are done on the POCO X3 Pro running Windows!

#### Disabling USB Host mode
- In the command prompt put ```reg add "HKLM\SYSTEM\CurrentControlSet\Enum\ACPI\QCOM0597\0\Device Parameters" /v RoleSwitchMode /t REG_DWORD /d 3```
- Reboot your phone

#### Enabling USB Host mode
- In the command prompt put ```reg add "HKLM\SYSTEM\CurrentControlSet\Enum\ACPI\QCOM0597\0\Device Parameters" /v RoleSwitchMode /t REG_DWORD /d 1```
- Reboot your phone

---

_**© 2020-2024 The Duo WOA Authors**_
