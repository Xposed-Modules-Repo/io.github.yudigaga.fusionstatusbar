# FusionStatusBar 状态栏融合图标

FusionStatusBar 是面向 MIUI/HyperOS 的 LibXposed 模块，提供融合图标、双排状态栏、时钟天气与设备遥测、控制中心布局和外观编辑，以及桌面应用隐藏与手势。

## 功能

- 调整融合图标、状态栏布局和双排显示。
- 自定义时钟与天气，显示温度、功率电流和网络速度等信息。
- 编辑控制中心的布局、磁贴与外观，并提供预览和配置备份。
- 横屏自定义布局、分组成员图标缩放、统一容器材质与全局描边。
- 分别调整电源菜单、音量菜单、通知中心与悬浮通知外观，支持三条电源菜单和短款音量条。
- 隐藏桌面应用图标，自定义桌面手势与返回停顿，选择系统动作、应用、活动、快捷方式和功能切换。
- 设置页面、底部导航和公共弹窗使用 Compose/Miuix 控件。
- 杂项页提供可选的链式启动确认移除，设置页可切换毛玻璃悬浮底栏。

## 最新正式版：0.5.21

- 版本号 `0.5.21`，构建号 `235`，沿用末位满 100、中间位满 10 的版本进位规则。
- 修复高光玻璃内侧的第二圈暗边，保留外轮廓上的方向反光；通知和控制中心继续共用玻璃绘制器。
- 补全实时字幕、翻译、模式等原生磁贴目录，无需先进入系统编辑页再查询。原控制器无法创建时，仅对标准系统工厂确切声明的非应用磁贴使用后备创建，初始化当前用户，失败时释放新实例。
- 分别保存“模式”`dnd`、MIUI 勿扰 `quietmode` 和模式体系勿扰 `modes_dnd`，避免排序、隐藏和创建路由互相覆盖。
- Wi-Fi、蓝牙等已知磁贴保持固定标题，新增原生磁贴优先显示宿主标签，并为翻译、实时字幕、模式和勿扰提供名称回退。

[下载正式 APK](https://github.com/Xposed-Modules-Repo/io.github.yudigaga.fusionstatusbar/releases/tag/235-0.5.21) · [0.5.21 更新说明与验证范围](https://github.com/yudigaga/FusionStatusBar/blob/v0.5.21/docs/release-notes-v0.5.21.md)

使用原正式证书签名，可覆盖更新 0.5.20。更新后重启系统界面（SystemUI），或重启设备，展开控制中心，再在 FusionStatusBar 中重新拉取控制中心布局，以更新旧版缓存的磁贴目录。旧配置中已保存的 `quietmode` 不自动迁移；若原本要使用“模式”，请重新选择独立的“模式”入口。确认 `com.miui.home` 与 `com.android.systemui` 作用域已启用；从更早版本升级时，仍按 [0.3.197 升级说明](https://github.com/yudigaga/FusionStatusBar/blob/v0.3.197/docs/release-notes-v0.3.197.md) 核对 **System（system / system_server）** 作用域。已有图标位置与缩放设置保留。

本版归档记录 Debug、Release 各 `194` 类、`1,500` 项单元测试通过，失败、错误和跳过均为 `0`；两种变体 lint 均为 `0` 错误、`99` 条警告。Python 工具测试 `28` 项本轮通过。本版手机安装、真实 LSPosed 回调、目标 ROM 模糊合成、磁贴可用性与点击尚未验收；宿主工厂声明不保证硬件、地区、账号或系统服务条件已满足。远端 CI 以发布提交的 GitHub Actions 为准。签名、APK 元数据和完整验证范围见 [0.5.21 更新说明](https://github.com/yudigaga/FusionStatusBar/blob/v0.5.21/docs/release-notes-v0.5.21.md)。

当前高光玻璃没有实现真实背景折射，尚未完成目标 ROM 的真实 MiGlass 绘制、视觉和稳定性验收。

正式 APK SHA-256：`67c558d53a88fd0f76d2e56195c25fe96c760e4ebdce95a0b5d7b2c47819de64`。完整来源见[源码发布页](https://github.com/yudigaga/FusionStatusBar/releases/tag/v0.5.21)与[构建记录](https://github.com/yudigaga/FusionStatusBar/blob/v0.5.21/artifacts/release-v0.5.21.json)。签名证书 SHA-256：`ccfaf42f8f14bb36973aeb971572fcc956a256196f68ff088340dfa7eca96fe2`。

## 0.3.173 更新（历史）

汇总 0.3.152-0.3.173 的控制中心布局、材质与绘制修复，统一音乐和融合中心的形状与底色，修复磁贴遮罩和重启后材质恢复，并新增系统菜单扩展。

[完整更新说明](https://github.com/yudigaga/FusionStatusBar/blob/v0.3.173/docs/release-v0.3.173.md)

正式包继续使用 `io.github.yudigaga.fusionstatusbar` 和原签名，可覆盖 0.3.150 及后续正式版。历史 0.3.173 验证记录未进行实体手机安装、SystemUI 注入或目标 ROM 验收。

## 适用范围

- Android 13（API 33）及以上，使用支持 LibXposed API 102 的框架。
- 作用域为 `system`、`com.android.systemui`、`miui.systemui.plugin`、`com.miui.home` 和 `com.miui.securitycenter`。从 0.3.193 升级后请新增勾选 System（system_server），随后重启手机。
- 侧边栏动作需要先开启系统侧边栏；“重启系统桌面”需要 root 授权。
- SystemUI 与厂商插件实现存在差异，最低 Android 版本不代表所有 ROM 都已验证兼容。

## 安装与启用

1. 从本仓库的 Release 下载并安装正式 APK。
2. 在 LSPosed 中启用模块，选择上述作用域。
3. 重启系统桌面和系统界面，或重启设备，再打开模块设置并确认连接状态。

## 从旧包名迁移

从 `0.3.150` 起，应用包名为 `io.github.yudigaga.fusionstatusbar`。旧版 `com.xtjm.fusionstatusbar` 是另一应用，无法直接覆盖安装或自动继承配置。

1. 在旧版设置中选择“导出配置备份”。
2. 安装新版，在设置中选择“导入配置备份”。
3. 在 LSPosed 中关闭旧模块，只启用新版，再重启系统界面。确认新版正常后可卸载旧包。

不要同时启用新旧两个模块，以免两套 Hook 同时修改系统界面。

## 源码与反馈

[项目源码及问题反馈](https://github.com/yudigaga/FusionStatusBar)
