# Open SSH Server tutorial

## 1. Introduction

Target: **Windows**

## 2. Sources
[Get started with OpenSSH for Windows](https://learn.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse?tabs=gui)

[Key-based authentication in OpenSSH for Windows](https://learn.microsoft.com/en-us/windows-server/administration/openssh/openssh_keymanagement)

[sshd_config — OpenSSH daemon configuration file](https://man.openbsd.org/sshd_config)

## 3. Configuration file
**C:\ProgramData\ssh\sshd_config**

Every change on the configuration file require to restart the server before changes take effect.

## 4. Installation
### 4.1 Making sure OpenSSH is available
```
Get-WindowsCapability -Online | Where-Object Name -like 'OpenSSH*'
```

### 4.2 Installing client
```
Add-WindowsCapability -Online -Name OpenSSH.Client~~~~0.0.1.0
```

### 4.3 Installing server
```
Add-WindowsCapability -Online -Name OpenSSH.Server~~~~0.0.1.0
```

## 5 Configuring on startup
```
Set-Service -Name sshd -StartupType 'Automatic'
```

## 6 Checking firewall rule
Open *Windows Defender Firewall* on advanced mode and look for *OpenSSH SSH Server (sshd)* entry.

## 7 Key auhtentication
In order to profit from Key Authentication, first disable *Password Authentication*.

### 7.1 Modifying configuration file
*C:\ProgramData\ssh\sshd_config*
```
PasswordAuthentication no
PubkeyAuthentication yes
```

### 7.2 Enabling Key Authentication
Generate a key pair (on the client for security reasons).
```
ssh-keygen
```
Append the public key content into *C:\ProgramData\ssh\administrators_authorized_keys* (make sure this file doesn't have the *Authenticated Users* permissions).

## 8 Starting server
```
Start-Service sshd
```

## 9 Configuring client
Configuring *ssh-agent* service:
```
Get-Service ssh-agent | Set-Service -StartupType Automatic
Start-Service ssh-agent
Get-Service ssh-agent
```

Loading key into *ssh-agent*:
```
ssh-add <private_key>
```

## 10 Server Logging
[Logging Facilities](https://github.com/PowerShell/Win32-OpenSSH/wiki/Logging-Facilities)

[LogLevel](https://man.openbsd.org/sshd_config#LogLevel)
```
ssh user@host
```
*C:\ProgramData\ssh\sshd_config*
```
SyslogFacility LOCAL0
LogLevel DEBUG3
```
This will store debug logs into *C:\ProgramData\ssh\logs\sshd.log*.