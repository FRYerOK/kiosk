# kiosk

[![Join the chat at https://gitter.im/VoidVolker/kiosk](https://badges.gitter.im/VoidVolker/kiosk.svg)](https://gitter.im/VoidVolker/kiosk?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

Few simple experimental scripts to make kiosk mode for Linux and Windows

# Linux

Linux kiosk mode need next steps:

* Simple window manager
* Configuration of this window manager to use your application as shell
* User for autologon
* _[Option]_ Reverse ssh tunnel (inside script is test example) with autorun and autoreconnect
* _[Option]_ VPN connection to own server

# Windows
Windows kiosk mode need next steps:
* Create user for kiosk mode
```
net user kiosk /ADD
```
* Set next registry key for this user as path to your application:

Windows XP/7/10:
```
Windows Registry Editor Version 5.00

[HKEY_CURRENT_USER\Software\Microsoft\Windows NT\CurrentVersion\Winlogon]
"Shell"="C:\\full\\path\\to\\your\\application.exe>"

``` 
Windows 8:
```
Windows Registry Editor Version 5.00

[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Policies\System]
"Shell"="C:\\full\\path\\to\\your\\application.exe>"

``` 
Autologin for kiosk user:
```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Winlogon] 
"AutoAdminLogon"="1"
"ForceAutoLogon"="1"
"DefaultUserName"="kiosk"
"DefaultDomainName"="<place here pc hostname>"
"DefaultPassword"=""
```

* _[Option]_ If you need to disable Ctrl+Alt+Del, then use this registry key value ("") or you can place there own application:

```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\taskmgr.exe]
"Debugger"="\"\""

```

