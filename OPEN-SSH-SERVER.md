# Open SSH Server tutorial

## 1. Introduction

Target: **Windows**

## 2. Sources
[Get started with OpenSSH for Windows](https://learn.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse?tabs=gui)

[Key-based authentication in OpenSSH for Windows](https://learn.microsoft.com/en-us/windows-server/administration/openssh/openssh_keymanagement)

## 3. Installation
### 3.1 Making sure OpenSSH is available
```
Get-WindowsCapability -Online | Where-Object Name -like 'OpenSSH*'
```

### 3.2 Installing client
```
Add-WindowsCapability -Online -Name OpenSSH.Client~~~~0.0.1.0
```

### 3.3 Installing server
```
Add-WindowsCapability -Online -Name OpenSSH.Server~~~~0.0.1.0
```

## 4 Configuring on startup
```
Set-Service -Name sshd -StartupType 'Automatic'
```

## 5 Checking firewall rule
Open *Windows Defender Firewall* on advanced mode and look for *OpenSSH SSH Server (sshd)* entry.

## 6 Key auhtentication
In order to profit from Key Authentication, first disable *Password Authentication*.

### 6.1 Modifying configuration file
Service configuration file is *C:\ProgramData\ssh\sshd_config*
```
PasswordAuthentication no
PubkeyAuthentication yes
```

### 6.2 Enabling Key Authentication
Generate a key pair (on the client for security reasons).
```
ssh-keygen
```
Append the public key content into *C:\ProgramData\ssh\administrators_authorized_keys* (make sure this file doesn't have the *Authenticated Users* permissions).

## 7 Starting server
```
Start-Service sshd
```

## 8 Configuring client
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

## 9 Connecting from client
```
ssh user@host
```
