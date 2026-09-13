# Follow These step to Delete Default apps (Like YouTube)
- first open android studio
- then go to the terminal (in the bottom)
- then paste this command into it
```bash
& "$env:LOCALAPPDATA\Android\Sdk\platform-tools\adb.exe" devices
```
- now it will show the device that you have just connected
- now run this
```bash
& "$env:LOCALAPPDATA\Android\Sdk\platform-tools\adb.exe" shell pm uninstall --user 0 com.google.android.youtube
```
- Now will you will see success messages, which means it is now deleted the selected app
## If you want to restore it back the
- run this command into android studio terminal (in this example, it is YouTube)
```bash
& "$env:LOCALAPPDATA\Android\Sdk\platform-tools\adb.exe" shell cmd package install-existing com.google.android.youtube
```
### or you can download it from playstore.
