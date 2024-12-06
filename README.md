# unattended-computing
Repository with instructions for setting up Windows 11 for unattended computing

## Installing Windows 11

To setup Windows 11 without Microsoft account press shift + F10 to spawn a console window. In the consle type:
```OOBE\BYPASSNRO```, the installer will boot into a version that allows skipping over the Microsoft account registration.

References:
 * https://www.tomshardware.com/how-to/install-windows-11-without-microsoft-account

## Set up unattended login

* Start `regedit`
* Find the key `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\PasswordLess\Device`
* Set `DevicePasswordLessBuildVersion` to `0` (default is `2`)
* Restart the machine
* Run `netplwiz`
* Uncheck the "Users must enter a username and password to use this computer" box

References:
 * https://answers.microsoft.com/en-us/windows/forum/all/windows-11-22h2-auto-login-no-option-for-disabling/5016049f-cf8a-4087-af42-b1048a8d8de2

## Disable the widgets service

* Run PowerShell as administrator
* Run `Get-AppxPackage *WebExperience* | Remove-AppxPackage`
* Run `winget uninstall –id 9MSSGKG348SPC`

References:
 * https://answers.microsoft.com/en-us/windows/forum/all/how-to-permanently-stop-the-widgets-service-from/de082ed2-81db-4074-a334-0c9ca13f15c4
 * https://www.thurrott.com/forums/microsoft/windows/thread/uninstall-widgets-completely
