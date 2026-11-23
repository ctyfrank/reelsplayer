# ReelsPlayer

English | [简体中文](README.zh-CN.md)

Offline Android video player for your downloaded Reels, Shorts, and TikToks — swipe through them like you're still on the feed.

Pick a folder, get the full-screen vertical swipe experience.

<p float="left">
  <img src="demo/landing.jpg" width="250" />
  <img src="demo/player.jpg" width="250" />
</p>

## Features

- **Pick a folder** — recursively plays every video in it and its subfolders
- **Scan progress** — shows how many videos were found while scanning
- **Vertical swipe** — exactly like Reels/Shorts/TikTok
- **Tap to pause/play**
- **Long press right side → 2x speed**
- **Fully offline**
- **Localized UI** — Chinese, English, Russian; follows the system language

## Download

Grab the latest APK from [Releases](../../releases).

## Requirements

- Android 8.0+ (API 26)
- Scans every subfolder; swipe order follows the relative path, so videos from the same folder stay together

## Building from source

Requires **JDK 17** (AGP 8.2 enforces it) and an Android SDK with `platforms;android-34` and `build-tools;34.0.0`.

macOS / Linux (`$ANDROID_HOME` already uses forward slashes):

```bash
git clone https://github.com/ctyfrank/reelsplayer.git
cd reelsplayer
printf 'sdk.dir=%s\n' "$ANDROID_HOME" > local.properties
./gradlew assembleDebug
```

If `ANDROID_HOME` is exported you can skip `local.properties` — Gradle falls back to the env var.

Windows — `\` is an **escape character** inside `.properties`, so `sdk.dir=E:\Android\Sdk` would be read as `E:AndroidSdk`. Use forward slashes:

```powershell
git clone https://github.com/ctyfrank/reelsplayer.git
cd reelsplayer
Set-Content local.properties "sdk.dir=E:/Android/Sdk"
.\gradlew.bat assembleDebug
```

APK will be at `app/build/outputs/apk/debug/app-debug.apk`. Opening the folder in Android Studio works too — it ships its own JDK 17.

## License

MIT
