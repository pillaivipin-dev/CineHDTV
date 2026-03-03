# CineHD TV — Android TV App

A full-screen Android TV app that loads **https://cinehd.cc/home** in a WebView, optimised for remote/D-pad navigation.

---

## Features
- 🎬 Full-screen WebView — no chrome, no title bar
- 📺 Android TV Leanback launcher integration
- 🕹️ D-pad / remote navigation forwarded to the page
- ▶️ Full-screen HTML5 video playback
- ⬅️ Back button navigates browser history
- 🔄 Menu button reloads the page
- 🖥️ Desktop user-agent so the site renders its full layout
- 💾 WebView state saved on rotation / app resume

---

## Requirements
| Tool | Version |
|------|---------|
| Android Studio | Hedgehog (2023.1) or newer |
| JDK | 8+ |
| Android SDK | API 34 (compileSdk) |
| Min device API | 21 (Android 5.0) |

---

## Build in Android Studio
1. Open Android Studio → **File → Open** → select the `CineHDTV` folder.
2. Wait for Gradle sync to finish.
3. **Build → Build Bundle(s) / APK(s) → Build APK(s)**.
4. APK output: `app/build/outputs/apk/debug/app-debug.apk`

## Build via Command Line
```bash
cd CineHDTV
./gradlew assembleDebug
```

---

## Sideload onto Android TV

### Option A — ADB over Wi-Fi (recommended)
1. On the TV: **Settings → Device Preferences → About → Build** (click 7× to enable Developer Options).
2. **Settings → Device Preferences → Developer Options → USB Debugging → ON**.
3. **Settings → Device Preferences → Developer Options → Network Debugging → ON** (note the IP address shown).
4. On your PC:
```bash
adb connect <TV_IP_ADDRESS>:5555
adb install app/build/outputs/apk/debug/app-debug.apk
```

### Option B — USB
Connect the TV via USB-A → USB-A cable and run the same `adb install` command.

### Option C — File Manager
Copy the APK to a USB drive, plug into the TV, open a file manager app, and tap the APK to install (allow "Unknown Sources" if prompted).

---

## Remote Control Shortcuts
| Button | Action |
|--------|--------|
| D-pad / arrows | Navigate the page |
| Select / OK / Enter | Click focused element |
| Back | Go back in browser history / exit app |
| Menu | Reload the page |

---

## Customisation
- **Change URL:** Edit `TARGET_URL` in `MainActivity.java`.
- **App name:** Edit `app_name` in `res/values/strings.xml`.
- **Icon / banner:** Replace drawables in `res/drawable/` and `res/mipmap-hdpi/`.
