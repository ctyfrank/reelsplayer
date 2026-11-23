# ReelsPlayer

[English](README.md) | 简体中文

使用DeepSeek Harness构建。AI牛逼。
原版只扫描当前目录下的视频文件。修改后遍历选择目录下所有目录的视频。用的话小心卡死。

一款离线 Android 视频播放器，用来刷你已经下载到本地的 Reels、Shorts 和 TikTok 视频 —— 竖向滑动，就像还停留在信息流里一样。

选一个文件夹，立刻进入全屏竖向滑动的播放体验。

<p float="left">
  <img src="demo/landing.jpg" width="250" />
  <img src="demo/player.jpg" width="250" />
</p>

## 功能

- **选择文件夹** —— 递归扫描该文件夹及其所有子文件夹，播放找到的全部视频
- **扫描进度** —— 大目录扫描时显示「已找到 N 个视频」
- **竖向滑动** —— 交互与 Reels / Shorts / TikTok 一致
- **点击暂停 / 播放**
- **长按右侧 → 2 倍速** —— 按住右侧约三分之一的区域 0.3 秒后生效，松手立刻恢复 1 倍速
- **单个视频循环播放**
- **全程离线** —— 不联网、不上传任何内容
- **多语言界面** —— 中文、英文、俄语，跟随系统语言

界面上的细节：顶部显示当前视频相对路径与「当前 / 总数」，屏幕底部有一条细进度条。

## 下载

从 [Releases](../../releases) 获取最新 APK。

## 环境要求

- Android 8.0 及以上（API 26）
- 视频格式取决于 ExoPlayer 的支持范围（常见如 MP4/H.264、WebM、MKV 等）
- 递归遍历所有子文件夹；播放顺序按相对路径排序，同一目录的视频相邻

## 从源码构建

需要 **JDK 17**（AGP 8.2 强制要求），以及包含 `platforms;android-34`、`build-tools;34.0.0` 的 Android SDK。

macOS / Linux（`$ANDROID_HOME` 本身是正斜杠路径）：

```bash
git clone https://github.com/ctyfrank/reelsplayer.git
cd reelsplayer
printf 'sdk.dir=%s\n' "$ANDROID_HOME" > local.properties
./gradlew assembleDebug
```

已经导出 `ANDROID_HOME` 时可以省掉 `local.properties`，Gradle 会回退到该环境变量。

Windows（PowerShell）—— `.properties` 里 `\` 是**转义符**，`sdk.dir=E:\Android\Sdk` 会被读成 `E:AndroidSdk`，所以务必用正斜杠：

```powershell
git clone https://github.com/ctyfrank/reelsplayer.git
cd reelsplayer
Set-Content local.properties "sdk.dir=E:/Android/Sdk"
.\gradlew.bat assembleDebug
```

生成的 APK 位于 `app/build/outputs/apk/debug/app-debug.apk`。直接用 Android Studio 打开工程也可以，它自带 JDK 17。

技术栈：Kotlin + AndroidX ViewPager2 + Media3 ExoPlayer 1.2.0，compileSdk 34、minSdk 26、targetSdk 34，JDK 17。

## 签名发布版

在仓库根目录放入 `reelsplayer-release.jks`，并设置环境变量 `KEYSTORE_PASSWORD`、`KEY_ALIAS`、`KEY_PASSWORD`，然后执行：

```bash
./gradlew assembleRelease
```

未放签名文件时，release 构建不会签名。

## 持续集成

推送到 `main` 分支或打 `v*` 标签会触发 GitHub Actions：构建 debug 与 release APK 并作为 artifact 上传，打标签时自动创建 GitHub Release。相关配置见 [.github/workflows/build.yml](.github/workflows/build.yml)。

## 开源协议

MIT
