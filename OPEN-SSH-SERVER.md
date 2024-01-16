# Open SSH Server tutorial

## 1. Introduction

Target: **Windows**

## 2. Sources
[Get started with OpenSSH for Windows](https://learn.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse?tabs=gui)

[Key-based authentication in OpenSSH for Windows](https://learn.microsoft.com/en-us/windows-server/administration/openssh/openssh_keymanagement)

## 3. Installation

```
Get-WindowsCapability -Online | Where-Object Name -like 'OpenSSH*'
```