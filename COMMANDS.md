# Windows Commands Tutorial

## 1. Introduction

Most of the command are for **Powershell** and will not work with **CMD**

## 2. General commands

1.  [Stop-Computer](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/stop-computer?view=powershell-7.4) - Shuts down the computer.
```
Stop-Computer -Force
```

2.  [Restart-Computer](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/restart-computer?view=powershell-7.4) - Restart the computer.
```
Restart-Computer -Force
```

3.  Hostname:
```
hostname
```

4.  [Start-Service](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/start-service?view=powershell-7.4) - Starts service.
```
Start-Service <service_name>
```

5.  [Stop-Service](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/stop-service?view=powershell-7.4) - Stops service.
```
Stop-Service <service_name>
```

6.  [Set-Service](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/set-service?view=powershell-7.4) - Change service properties.
```
Set-Service -Name <service_name> -StartupType 'Automatic'
```

7.  [Get-Content](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/get-content?view=powershell-7.4) - Prints file content.
```
Get-Content <file>
```