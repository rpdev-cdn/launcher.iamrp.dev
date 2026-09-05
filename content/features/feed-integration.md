---
title: "Feed Integration & Overlay Bridge"
description: "Seamless integration between RPDev Launcher and RPDev Feed or Google Discover via Android Launcher Overlay API."
---

# Feed Integration & Overlay Bridge

RPDev Launcher features an extensible, zero-latency Feed Bridge that connects the leftmost desktop page (`-1` screen) with sovereign feed providers.

---

## 1. Supported Providers

RPDev Launcher supports seamless switching between feed backends:

1. **[RPDev Feed](https://feed.launcher.iamrp.dev)** (`iamrp.dev.feed`): The sovereign, modular, privacy-first feed displaying customized cards, system telemetry, news, and weather.
2. **Google Discover** (`com.google.android.googlequicksearchbox`): Standard Google Feed via the official Pixel Bridge.
3. **None**: Disables the overlay page completely, saving RAM and eliminating horizontal overshoot.

---

## 2. Zero-Duplicate Selection Protocol

In previous versions, legacy development packages (`com.saulhdev.neofeed.dev`) and production packages could both advertise the same feed service intent, leading to confusing duplicate items in the feed selection dialog.

RPDev Launcher hardens feed discovery inside `PrefUtils.kt`:

```kotlin
fun Context.getFeedProviders(): Map<String, String> {
    val providers = mutableMapOf<String, String>()
    // 1. None Option
    providers[""] = getString(R.string.feed_provider_none)
    
    // 2. Discover Google if present
    if (isPackageInstalled(GOOGLE_FEED_PACKAGE)) {
        providers[GOOGLE_FEED_PACKAGE] = "Google"
    }
    
    // 3. Resolve Feed Services & filter obsolete dev signatures
    val intent = Intent("com.android.launcher3.WINDOW_OVERLAY")
    val matches = packageManager.queryIntentServices(intent, 0)
    
    val hasOfficialFeed = matches.any { it.serviceInfo.packageName == "iamrp.dev.feed" }
    for (match in matches) {
        val pkg = match.serviceInfo.packageName
        if (hasOfficialFeed && pkg.startsWith("com.saulhdev.neofeed")) {
            continue // Silently prune legacy duplicate signatures
        }
        val label = match.loadLabel(packageManager).toString()
        providers[pkg] = label
    }
    return providers
}
```

This guarantees an uncluttered, single selection experience.
