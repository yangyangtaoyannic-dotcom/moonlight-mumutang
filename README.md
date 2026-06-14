# 月光·木木糖

Moonlight Mumutang首先是基于阿西西的的一个改版增加了界面的记忆功能,原始是基于 [Moonlight Android](https://github.com/moonlight-stream/moonlight-android) 的安卓串流客户端定制版本，面向 Sunshine、Apollo 以及兼容 NVIDIA GameStream 协议的主机使用。它保留 Moonlight 的低延迟串流能力，并在移动端操作、快捷菜单、虚拟按键和日常串流体验上做了更适合手机使用的调整。

本仓库主要用于保存木木糖定制版源码、构建脚本和本地修改记录，方便后续继续维护、打包和同步。

## 直接下载

- Android 客户端 APK：[moonlight-mumutang-android.apk](dist/moonlight-mumutang-android.apk)
- Windows 串流服务端安装包：[apollo-windows-0.4.7-alpha.1.exe](dist/apollo-windows-0.4.7-alpha.1.exe)

文件校验：

```text
moonlight-mumutang-android.apk
SHA256: E68F2CDAA0BF001976F702F0F6AE84CA826D9FED4B69DD5ADAC7C984A8D1FD19

apollo-windows-0.4.7-alpha.1.exe
SHA256: 66BA98DE16AF71EF8EEC379EC35263235FB67119CCBFC33B61119D592F5B5CF6
```

## 主要特性

- 支持从 Windows 主机串流游戏或桌面到 Android 手机、平板、电视盒子等设备。
- 适配 Sunshine / Apollo 等开源串流服务端。
- 全新的串流快捷菜单 UI，常用操作更集中。
- 快捷菜单中的稳定设置支持全局记忆，重新连接串流后自动沿用上次配置。
- 支持多种鼠标和触控模式，包括普通鼠标、多点触控、触控板、禁用触控、本地鼠标光标等。
- 支持性能信息显示、大/小性能信息样式切换，并可记住用户选择。
- 支持自定义虚拟手柄、虚拟特殊键盘、快捷键和触控灵敏度。
- 支持自定义分辨率、码率、帧率、显示设备和横竖屏切换。

## 木木糖定制改动

相比原始 Moonlight Android，本版本目前重点调整了以下体验：

1. 串流快捷设置全局记忆  
   性能信息、鼠标/触控模式、本地鼠标光标、远程桌面鼠标模式、触控灵敏度、虚拟手柄、虚拟键盘、横竖屏等设置会写入全局偏好，下次连接自动恢复。

2. Apollo / Sunshine 使用适配  
   已在本地测试过 Apollo 权限配置、APK 安装、手机连接和串流启动流程。

## 构建环境

本项目是 Android / Gradle 工程，主要环境如下：

- Android Gradle Plugin 项目
- Android SDK
- Android NDK `27.0.12077973`
- JDK 11 或兼容版本
- Windows PowerShell 构建脚本

本地已提供辅助脚本：

```powershell
powershell -ExecutionPolicy Bypass -File "C:\Users\yangyang\Desktop\月光\build-moonlight-debug.ps1"
```

构建完成后，debug APK 通常位于：

```text
C:\Users\yangyang\moonlight-android-build\app\build\outputs\apk\nonRoot\debug\app-nonRoot-debug.apk
```

## 安装与使用

1. 在电脑端安装并配置 Sunshine 或 Apollo。
2. 确认电脑和手机处于同一局域网，或正确配置公网访问和端口转发。
3. 在 Android 设备上安装 `月光·木木糖` APK。
4. 打开应用，添加或发现电脑主机。
5. 完成配对后即可启动桌面或游戏串流。

常见需要放行的端口包括：

```text
TCP 47984
TCP 47989
```

实际端口要求可能随 Sunshine / Apollo 配置变化，请以服务端设置为准。

## 注意事项

- 本项目是 Moonlight Android 的定制版本，不是官方 Moonlight 发布版。
- 如果同一台手机上同时安装了旧包和新包，桌面上可能会出现两个应用图标。旧包名的数据不会自动迁移到新包名。
- 如果服务端使用 Apollo，需要确保对应客户端证书或权限已被允许，否则可能出现启动失败或端口检查提示。
- 本仓库包含本地构建产物时，上传前建议清理 `app/build`、`.gradle` 等临时目录，避免仓库过大。

## 上游项目

本项目基于 Moonlight Android：

- 官网：[https://moonlight-stream.org](https://moonlight-stream.org)
- 上游仓库：[moonlight-stream/moonlight-android](https://github.com/moonlight-stream/moonlight-android)
- Sunshine：[LizardByte/Sunshine](https://github.com/LizardByte/Sunshine)

Moonlight for Android 是一个开源的 NVIDIA GameStream / Sunshine 客户端，可将 Windows PC 上的游戏和桌面串流到 Android 设备。

## License

本项目沿用上游 Moonlight Android 的开源许可。请查看 [LICENSE.txt](LICENSE.txt) 获取完整许可文本。

原始 Moonlight Android 作者包括 Cameron Gutman、Diego Waxemberg、Aaron Neyer、Andrew Hennessy 以及其他贡献者。木木糖定制版在此基础上进行功能和文案层面的本地化调整。
