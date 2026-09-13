# 🗑️ Default App Deleter

A simple guide to **remove pre-installed/default Android apps** (such as YouTube) from your device using **ADB (Android Debug Bridge)**.

> ⚠️ **Important:** This method removes the app for the current Android user (`--user 0`). It does **not** permanently delete the APK from the system partition, which is why the app can usually be restored later.

---

## 📋 What You Need

Before starting, make sure you have:

* 📱 An Android phone
* 💻 A Windows PC
* [Android Studio](https://developer.android.com/studio) installed
* 🔌 A USB cable
* 🛠️ USB Debugging enabled on your phone

---

# 🚀 Step-by-Step Guide

## 1. Enable Developer Options

On your Android phone:

1. Open **Settings**.
2. Go to **About phone**.
3. Find **Build number**.
4. Tap **Build number** **7 times** (the exact number may vary by device).
5. You should see a message indicating that **Developer Options** have been enabled.

> The location of **Build number** can vary between manufacturers.

---

## 2. Enable USB Debugging

1. Go back to **Settings**.
2. Open **Developer options**.
3. Find **USB debugging**.
4. Enable it.
5. Confirm the warning if your device asks for permission.

---

## 3. Connect Your Phone to Your PC

Connect your Android phone to your computer using a USB cable.

When prompted on your phone:

* Select **File Transfer / Android Auto** instead of **Charging only**.
* If you see **"Allow USB debugging?"**, tap **Allow**.

Your computer should now be able to communicate with your phone through ADB.

---

# 🔍 4. Check That ADB Detects Your Phone

Open **Android Studio** and open its built-in **Terminal**.

Run:

```powershell
& "$env:LOCALAPPDATA\Android\Sdk\platform-tools\adb.exe" devices
```

You should see something similar to:

```text
List of devices attached
XXXXXXXX    device
```

If your device appears with the status `device`, you're ready to continue. ✅

### If you see `unauthorized`

Look at your phone's screen.

You should see:

> Allow USB debugging?

Tap **Allow**, then run the `adb devices` command again.

---

# 🗑️ 5. Uninstall the Default App

ADB identifies Android apps using their **package name**.

For example, the package name for YouTube is:

```text
com.google.android.youtube
```

To remove YouTube for the current user, run:

```powershell
& "$env:LOCALAPPDATA\Android\Sdk\platform-tools\adb.exe" shell pm uninstall --user 0 com.google.android.youtube
```

If everything worked correctly, you should see:

```text
Success
```

🎉 **YouTube has now been removed from the current Android user.**

---

# ♻️ Restore the App

Because we used:

```text
--user 0
```

the system APK usually remains on the device. This means you can restore the app without downloading it again.

For YouTube, run:

```powershell
& "$env:LOCALAPPDATA\Android\Sdk\platform-tools\adb.exe" shell cmd package install-existing com.google.android.youtube
```

If successful, you should see:

```text
Package com.google.android.youtube installed for user: 0
```

The app should now be available again. ✅

### Alternative: Google Play Store

You can also reinstall/update the app through the **Google Play Store**, provided the app is available for your device.

---

# 🔎 Finding the Package Name of Another App

The command above works specifically for YouTube because:

```text
com.google.android.youtube
```

is YouTube's package name.

For other apps, you need their corresponding package name.

For example:

| App         | Package Name                   |
| ----------- | ------------------------------ |
| YouTube     | `com.google.android.youtube`   |
| Chrome      | `com.android.chrome`           |
| Google Maps | `com.google.android.apps.maps` |
| Gmail       | `com.google.android.gm`        |

> ⚠️ Package names can vary by device, Android version, region, or manufacturer. **Verify the package name before uninstalling anything.**

---

# ⚠️ Important Warning

**Do not randomly uninstall system packages.**

Some Android packages are required for:

* 📞 Phone calls
* 📶 Mobile network connectivity
* ⚙️ System settings
* 🏠 Home screen/launcher
* 🔐 Security features
* 🔄 System updates
* 📱 Device-specific functionality

Removing an essential package can cause unexpected behavior or, in extreme cases, make your device difficult to use.

### Recommended approach

Only remove apps that you are confident are safe to disable/remove, and **keep a record of the package names** so you can restore them if necessary.

---

# 🧰 Commands at a Glance

### Check connected devices

```powershell
& "$env:LOCALAPPDATA\Android\Sdk\platform-tools\adb.exe" devices
```

### Remove an app for User 0

```powershell
& "$env:LOCALAPPDATA\Android\Sdk\platform-tools\adb.exe" shell pm uninstall --user 0 PACKAGE_NAME
```

Example:

```powershell
& "$env:LOCALAPPDATA\Android\Sdk\platform-tools\adb.exe" shell pm uninstall --user 0 com.google.android.youtube
```

### Restore an app

```powershell
& "$env:LOCALAPPDATA\Android\Sdk\platform-tools\adb.exe" shell cmd package install-existing PACKAGE_NAME
```

Example:

```powershell
& "$env:LOCALAPPDATA\Android\Sdk\platform-tools\adb.exe" shell cmd package install-existing com.google.android.youtube
```

---

# 💡 How It Works

The important part of the uninstall command is:

```text
pm uninstall --user 0
```

`pm` → Android's **Package Manager**

`uninstall` → Removes the package for the specified user

`--user 0` → Applies the removal to **Android's primary user**

This is different from completely deleting the application's APK from the system.

That's why the app can generally be restored using:

```text
cmd package install-existing
```

---

# 🤝 Contributing

Found a mistake or want to improve this guide?

Feel free to:

1. Fork the repository.
2. Make your changes.
3. Commit your changes.
4. Open a Pull Request.

---

# ⭐ Support

If this guide helped you remove unwanted default apps from your Android device, consider giving the repository a ⭐.

**Happy debloating! 🧹📱**
