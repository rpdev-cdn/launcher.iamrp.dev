---
title: "Getting Started with RPDev Launcher"
description: "Step-by-step setup guide, permissions, gesture configuration, and default launcher setup."
---

# Getting Started with RPDev Launcher

Welcome to RPDev Launcher! Follow this guide to install, configure, and customize your home screen.

---

## 1. Installation

1. Download the latest APK from the [Downloads Page](../download.md) or via the [RPDev Repository](https://repo.launcher.iamrp.dev).
2. On your Android device, enable **Install unknown apps** for your browser or file manager.
3. Open the downloaded `.apk` and tap **Install**.

```bash
# Alternative: Install via ADB
adb install -r -d RPDevLauncher-v1.0.0-release.apk
```

---

## 2. Set as Default Home App

To ensure gestures, swipe-up app drawer, and system buttons route to RPDev Launcher:

1. Open Android **Settings** → **Apps** → **Default apps**.
2. Tap **Home app**.
3. Select **RPDev Launcher**.

---

## 3. Recommended Initial Settings

Open **Launcher Settings** by long-pressing any empty space on the home screen and tapping **Settings**:

- **Feed Provider**: Set to **RPDev Feed** to enable the modular smartspace overlay.
- **Icon Pack**: Select your preferred adaptive icon shape (Circle, Squircle, Rounded Square).
- **Desktop Grid**: We recommend `5x5` for standard smartphones and `6x6` for foldables/tablets.
- **Nested Folders**: Enabled by default. Simply drag any folder onto another folder to nest!
