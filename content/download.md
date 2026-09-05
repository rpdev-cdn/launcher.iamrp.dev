---
title: "Download RPDev Launcher"
description: "Download the latest stable and preview APK builds for RPDev Launcher."
---

# Download RPDev Launcher

All official builds are signed with our sovereign release key and hosted on our distributed CDN.

---

## Latest Releases

| Channel | Version | Architecture | Minimum Android | Download |
|---|---|---|---|---|
| **Stable** | `v1.0.0` | `arm64-v8a, armeabi-v7a, x86_64` | Android 9.0 (API 28) | [Download APK](https://repo.launcher.iamrp.dev/apks/RPDevLauncher-v1.0.0.apk) |
| **Alpha / Nightly** | `v1.1.0-alpha02` | `arm64-v8a, x86_64` | Android 12.0 (API 31) | [Download APK](https://repo.launcher.iamrp.dev/apks/RPDevLauncher-v1.1.0-alpha02.apk) |

---

## Verifying Checksums

Verify your download integrity using SHA-256:

```bash
sha256sum RPDevLauncher-v1.0.0.apk
# Expected: 7c5d9e83a4f61b0c9e8d4a3b2c1e0f9a8b7c6d5e4f3a2b1c0d9e8f7a6b5c4d3e
```

---

## Package Details

- **Package Identifier**: `iamrp.dev.launcher`
- **Main Component**: `iamrp.dev.launcher.RPDevLauncher`
- **Required Permissions**:
  - `READ_EXTERNAL_STORAGE` / `READ_MEDIA_IMAGES`: Wallpaper & custom icons
  - `REQUEST_DELETE_PACKAGES`: Drag-to-uninstall
  - `QUERY_ALL_PACKAGES`: App drawer indexing
  - `SET_WALLPAPER`: Wallpaper switching
