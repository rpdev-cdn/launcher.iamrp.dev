---
title: "Nested Folders Architecture"
description: "Deep dive into Recursive Folder-in-Folder architecture, cycle detection, and high-res preview rendering."
---

# Nested Folders Architecture

One of RPDev Launcher's flagship capabilities is native support for **folders inside folders** on both the home screen desktop and within the application drawer.

---

## 1. Cycle Detection & Safety Guard

Arbitrary folder nesting presents the classic graph theory challenge: preventing circular references (e.g. Folder A containing Folder B, which is then dropped into Folder A).

RPDev Launcher implements deterministic cycle detection directly inside `FolderInfo.java`:

```java
public boolean wouldCreateCycle(FolderInfo child) {
    if (child == null || child == this || child.id == this.id) return true;
    for (ItemInfo item : child.contents) {
        if (item instanceof FolderInfo sub) {
            if (sub == this || sub.id == this.id || wouldCreateCycle(sub)) {
                return true;
            }
        }
    }
    return false;
}
```

### Safety Rules:
1. **Self-Reference Guard**: An item can never accept itself (`child == this || child.id == this.id`).
2. **Recursive Traversal**: The detection engine walks the entire subtree of the target child.
3. **Database Integrity**: `LoaderCursor.java` validates container IDs at boot time to heal orphaned or corrupted nodes.

---

## 2. High-Resolution Preview Item Rendering

Standard AOSP folder previews only expect simple application icons (`WorkspaceItemInfo`). RPDev Launcher extends `PreviewItemManager.java` and `FolderPagedView.java` to support recursive folder preview rendering:

- If a preview slot contains a subfolder, `FolderIcon` dynamically retrieves high-resolution cached icons for up to 4 children of the subfolder.
- Micro-grid compositing renders a miniature 2x2 grid inside the preview dot, providing visual depth.
- Hardware-accelerated canvas clipping ensures crisp rounded geometry across all display densities (mdpi through xxxhdpi).

---

## 3. Database Schema Persistence

Subfolders are persisted in SQLite using the standard `favorites` table with relational hierarchy:

| Column | Description |
|---|---|
| `_id` | Unique item identifier |
| `container` | ID of the parent `FolderInfo` (or `CONTAINER_DESKTOP` / `CONTAINER_HOTSEAT`) |
| `itemType` | `ITEM_TYPE_FOLDER` (value: 2) |
| `rank` | Position index within the parent folder's paged collection |
| `title` | User-assigned folder label |

Nested subfolder loading is resolved via topological ordering in `WorkspaceItemProcessor.kt`, ensuring parent containers are instantiated before children are attached.
