---
title: "RPDev Launcher"
description: "High-performance, privacy-first Android home screen experience built on modern AOSP foundations with Android 16 parity."
---

# 🚀 RPDev Launcher

> **The Sovereign, Lean Android Home Screen Engineered for Absolute Fluidity and Zero Bloat.**

```
  ██████╗ ██████╗ ██████╗ ███████╗██╗   ██╗
  ██╔══██╗██╔══██╗██╔══██╗██╔════╝██║   ██║
  ██████╔╝██████╔╝██║  ██║█████╗  ██║   ██║
  ██╔══██╗██╔═══╝ ██║  ██║██╔══╝  ╚██╗ ██╔╝
  ██║  ██║██║     ██████╔╝███████╗ ╚████╔╝ 
  ╚═╝  ╚═╝╚═╝     ╚═════╝ ╚══════╝  ╚═══╝  
               L A U N C H E R             
```

---

## 🏛️ Corporate Identity & The Lean Philosophy

Modern mobile operating systems increasingly force monolithic launchers onto users—bloated with cloud search indexing, aggressive ad placements, telemetry background services, and slow webviews.

**RPDev Launcher stands in stark contrast.** Engineered as a lean, independent desktop orchestrator, it adheres to strict architectural purity:

1. **Razor-Lean Core**: The core launcher has an idle footprint of **<35MB RAM**, achieving zero background CPU wakeups and consistent **120Hz frame render times (<8ms)**.
2. **Separation of Concerns**: News, contextual feeds, and telemetry are intentionally decoupled into **[RPDev Feed](https://feed.launcher.iamrp.dev)** via Android's high-speed AIDL IPC bridge (`WINDOW_OVERLAY`). The launcher stays blisteringly fast because it does not run heavy background web scrapers.
3. **Decompiled Android 16 Pixel Parity**: Built on modern AOSP foundations, matching Google's Android 16 Pixel Launcher (`NexusLauncherRelease.apk`) in gesture predictive back navigation, system taskbar integration, and Material You dynamic color palette generation.
4. **Absolute Privacy**: Zero analytics, zero ad SDKs, zero phone-home pings. All layout configurations, drawer groupings, and folder geometries reside securely on-device in Jetpack DataStore.

---

## 🌟 Flagship Innovations

| Feature | Description | Deep Dive |
| :--- | :--- | :--- |
| 📁 **Recursive Nested Folders** | Unlimited folders-inside-folders with cycle detection, multi-tier preview rendering, and DataStore persistence. | [Nested Folders Guide](features/nested-folders.md) |
| 🎨 **Custom Icon & Drawer Theming** | Independent per-folder custom icons, dynamic drawer bottom-sheet editors, and full icon pack support. | [Custom Icons Guide](features/custom-icons.md) |
| 📰 **Modular Feed Bridge** | Native AIDL docking with **[RPDev Feed](https://feed.launcher.iamrp.dev)** and Google Discover via the standard Android Launcher Overlay protocol. | [Feed Integration](features/feed-integration.md) |
| ⚡ **Pixel 16 Parity** | Architectural deep dive comparing AOSP and NexusLauncher system shortcut hooks and taskbar integration. | [Pixel Parity](architecture/decompiled-pixel-parity.md) |
| 🏗️ **Lean Architecture** | Architectural rationale explaining why keeping the launcher lean and modular creates a superior experience. | [Lean Philosophy](architecture/lean-philosophy.md) |

---

## 📸 Android 16 Showcase (DevPixel16)

| Workspace Desktop | App Drawer & Search | Desktop Context Popup |
|:---:|:---:|:---:|
| <img src="/static/images/launcher_home_devpixel16.png" width="260" alt="Workspace Desktop"/> | <img src="/static/images/launcher_drawer_devpixel16.png" width="260" alt="App Drawer"/> | <img src="/static/images/launcher_home_popup_devpixel16.png" width="260" alt="Desktop Popup"/> |

| Folder Customization | Search & Feed Settings | Widget Picker Dialog |
|:---:|:---:|:---:|
| <img src="/static/images/launcher_folder_settings_devpixel16.png" width="260" alt="Folder Geometry"/> | <img src="/static/images/launcher_search_feed_settings_devpixel16.png" width="260" alt="Search & Feed Settings"/> | <img src="/static/images/launcher_widgets_picker_devpixel16.png" width="260" alt="Widget Picker"/> |

---

## ⚡ Quick Navigation

| Resource | Description | Link |
|---|---|---|
| **Getting Started** | Setup instructions, default launcher selection, permissions | [Getting Started](guides/getting-started.md) |
| **Download APK** | Official signed builds for Android 14+ (API 34-37) | [Download v1.2.0](download.md) |
| **RPDev Feed Portal** | Companion minus-one feed engine | [feed.launcher.iamrp.dev](https://feed.launcher.iamrp.dev) |
| **Module Catalog** | Extend your minus-one screen with community modules | [launcher.repo.iamrp.dev](https://launcher.repo.iamrp.dev) |
| **Sovereign CDN** | Fast edge assets, OTA manifests, and logos | [cdn.iamrp.dev](https://cdn.iamrp.dev) |
