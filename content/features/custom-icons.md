---
title: "Custom Icons & Drawer Theming"
description: "Drawer folder custom icons, bottom sheet customization, and JSON persistence engine."
---

# Custom Icons & Drawer Theming

RPDev Launcher provides deep visual customization, enabling users to apply custom icons, colors, and layouts to any folder or application shortcut.

---

## 1. Drawer Folder Customization

While standard launchers restrict custom icons to home screen items, RPDev Launcher enables full drawer folder theming:

- **Interactive Sheet**: Long-pressing any drawer folder opens `CustomizeFolderSheet.kt`.
- **Icon Pack Bridge**: Select icons from any installed third-party icon pack (Nova, Lawnchair, LineX, etc.) or local gallery images.
- **Color Accent Picker**: Override default Material You dynamic palette with custom HEX tinting.

---

## 2. JSON Persistence Engine

To ensure fast serialization without altering core AOSP SQLite table constraints, drawer folder customizations are persisted in JSON format:

```json
{
  "folder_id": 142,
  "custom_title": "Developer Tools",
  "icon_source": "icon_pack",
  "icon_package": "com.theme.minimalist",
  "icon_drawable": "ic_terminal",
  "tint_color": "#4ddad7"
}
```

- Handled by `CustomizeFolderSheet.kt` and `EditGroupBottomSheet.kt`.
- Instant backup and restore across device migrations.
- Zero latency impact on cold launcher startup.
