# 📱 Default App Deleter (DADL)

A simple guide to remove pre-installed bloatware and default apps (like YouTube) from your Android device using ADB (Android Debug Bridge).

---

## 🎯 What is This?

This project helps you uninstall default/bloatware apps from your Android device using Android Studio's terminal and ADB commands. Perfect for cleaning up unnecessary pre-installed applications.

---

## 📋 Prerequisites

- **Android Studio** installed on your computer
- **USB Debugging enabled** on your Android device
- **Android device connected** via USB cable to your computer

---

## ⚙️ Setup Instructions

### Step 1: Open Android Studio
Launch Android Studio on your computer.

### Step 2: Open Terminal
Go to the bottom of Android Studio and click on the **Terminal** tab.

### Step 3: Check Connected Devices
Paste this command to verify your device is connected:

```powershell
& "$env:LOCALAPPDATA\Android\Sdk\platform-tools\adb.exe" devices
```

**Expected Output:**
```
List of attached devices
xxxxxxxxxxxx    device
```

---

## 🗑️ How to Delete Apps

### Step 1: Run the Uninstall Command
Execute this command in the terminal (example: removing YouTube):

```powershell
& "$env:LOCALAPPDATA\Android\Sdk\platform-tools\adb.exe" shell pm uninstall --user 0 com.google.android.youtube
```

### Step 2: Verify Success
You should see a success message confirming the app has been deleted:
```
Success
```

---

## 🔄 How to Restore Apps

### Option 1: Using ADB Command
If you want to restore the app using ADB:

```powershell
& "$env:LOCALAPPDATA\Android\Sdk\platform-tools\adb.exe" shell cmd package install-existing com.google.android.youtube
```

### Option 2: Using Google Play Store
Simply download the app again from the **Google Play Store** on your Android device.

---

## 📦 Common App Package Names

| App | Package Name |
|-----|--------------|
| YouTube | `com.google.android.youtube` |
| Chrome | `com.android.chrome` |
| Gmail | `com.google.android.gm` |
| Google Maps | `com.google.android.apps.maps` |
| Google Photos | `com.google.android.apps.photos` |

> 💡 **Tip:** To find other app package names, search online or use: `adb shell pm list packages`

---

## ⚠️ Important Notes

- **Backup First:** Always backup your device before making system changes
- **Be Careful:** Only uninstall apps you're sure about. Some system apps may affect device functionality
- **User 0:** The `--user 0` flag uninstalls for the primary user only, not affecting other users on the device
- **Reversible:** Most uninstalled apps can be restored using the methods above

---

## 🤔 Troubleshooting

**Device not showing in `adb devices`?**
- Ensure USB Debugging is enabled on your Android device
- Try disconnecting and reconnecting the USB cable
- Restart Android Studio

**Command not recognized?**
- Make sure you're in the correct Android Studio terminal
- Verify the ADB path is correct for your installation

**Permission Denied?**
- Check that USB Debugging is enabled
- Grant USB debugging permissions when prompted on your device

---

## 📝 License

This project is provided as-is for educational purposes.

---

## 💬 Questions or Issues?

Feel free to open an issue or reach out with any questions!

**Happy cleaning! 🚀**
