# Windows Commands Tutorial

## 1. Introduction

Most of the command are for **Powershell** and will not work with **CMD**

## 2. General commands

#### 2.1.   [Stop-Computer](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/stop-computer?view=powershell-7.4) - Shuts down the computer.
```
Stop-Computer -Force
```

#### 2.2.   [Restart-Computer](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/restart-computer?view=powershell-7.4) - Restart the computer.
```
Restart-Computer -Force
```

#### 2.3.    Hostname:
```
hostname
```

#### 2.4.   [Start-Service](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/start-service?view=powershell-7.4) - Starts service.
```
Start-Service <service_name>
```

#### 2.5.   [Stop-Service](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/stop-service?view=powershell-7.4) - Stops service.
```
Stop-Service <service_name>
```

#### 2.6.   [Set-Service](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/set-service?view=powershell-7.4) - Change service properties.
```
Set-Service -Name <service_name> -StartupType 'Automatic'
```

#### 2.7.   [Get-Content](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/get-content?view=powershell-7.4) - Prints file content.
```
Get-Content <file>
```

## 3. Other commands

#### 3.1.   Change monitors brightness.

[Use PowerShell to Report and Set Monitor Brightness](https://devblogs.microsoft.com/scripting/use-powershell-to-report-and-set-monitor-brightness/)

[Trying to change brightness on my desktop screens via powershell and encountered an error](https://learn.microsoft.com/en-us/answers/questions/1190063/trying-to-change-brightness-on-my-desktop-screens)


[Get-WmiObject](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/get-wmiobject?view=powershell-5.1)

[WmiMonitorBrightnessMethods class](https://learn.microsoft.com/en-us/windows/win32/wmicoreprov/wmimonitorbrightnessmethods)


[WmiSetBrightness method of the WmiMonitorBrightnessMethods class](https://learn.microsoft.com/en-us/windows/win32/wmicoreprov/wmisetbrightness-method-in-class-wmimonitorbrightnessmethods)

```
Get-WmiObject -namespace root/wmi -class WmiMonitorBrightnessMethods | foreach {
    $_.wmisetbrightness(80,20)
}
```