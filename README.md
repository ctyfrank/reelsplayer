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

```bash
git clone https://github.com/underwear/reelsplayer.git
cd reelsplayer
echo "sdk.dir=$ANDROID_HOME" > local.properties
./gradlew assembleDebug
```

APK will be at `app/build/outputs/apk/debug/app-debug.apk`

## License

MIT
