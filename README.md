# FusionStatusBar 状态栏融合图标

FusionStatusBar 是面向 MIUI/HyperOS 的 LibXposed 模块，提供融合图标、双排状态栏、时钟天气与设备遥测、控制中心布局和外观编辑，以及桌面应用隐藏与手势。

[下载 0.5.36 正式 APK](https://github.com/Xposed-Modules-Repo/io.github.yudigaga.fusionstatusbar/releases/tag/250-0.5.36) · [主仓发布页](https://github.com/yudigaga/FusionStatusBar/releases/tag/v0.5.36) · [源码与反馈](https://github.com/yudigaga/FusionStatusBar) · [历史更新](HISTORY.md)

## 当前版本：0.5.36

版本号 `0.5.36`，构建号 `250`。相对已发布的 `0.5.34`，本版包含以下布局修订：

- 包含 0.5.35 对隐藏闹钟图标后稳定布局空隙的修订。
- 修订隐私提示退出后的网速布局恢复。
- 沿用现有 19 项状态图标显示设置及五个作用域，没有新增 LSPosed 作用域。

正式包的构建、签名和自动化验证结果见本版发布说明。本版没有设备、真实 LSPosed 回调或目标 ROM 验收，不能将本地验证视为实机布局效果确认。

[0.5.36 更新、签名与验证范围](https://github.com/yudigaga/FusionStatusBar/blob/v0.5.36/docs/release-notes-v0.5.36.md)

## 功能

- 调整融合图标、状态栏布局和双排显示，选择充电时显示闪电或电量数字。
- 自定义时钟与天气，显示温度、功率电流和网络速度等信息。
- 编辑控制中心的布局、磁贴与外观，并提供预览和配置备份。
- 横屏自定义布局、分组成员图标缩放、统一容器材质与全局描边。
- 分别调整电源菜单、音量菜单、通知中心与悬浮通知外观，支持三条电源菜单和短款音量条。
- 隐藏桌面应用图标，自定义桌面手势与返回停顿，选择系统动作、应用、活动、快捷方式和功能切换。
- 设置页面、底部导航和公共弹窗使用 Compose/Miuix 控件。
- 应用界面支持跟随系统及简体中文、繁體中文、English、日本語、한국어、Русский、Español。
- 杂项页提供可选的链式启动确认移除、截屏剪贴板保护和指定版本的手机管家扩展，设置页可切换毛玻璃悬浮底栏。

## 适用范围

- Android 13（API 33）及以上，使用支持 LibXposed API 102 的框架。最低 Android 版本不代表所有厂商 ROM 均已验证兼容。
- 作用域为 `system`、`com.android.systemui`、`miui.systemui.plugin`、`com.miui.home` 和 `com.miui.securitycenter`。
- 侧边栏动作需要先开启系统侧边栏；“重启系统桌面”需要 root 授权。
- 手机管家扩展默认关闭，具体功能依赖对应宿主版本、原生服务或硬件；详见[功能边界](https://github.com/yudigaga/FusionStatusBar/blob/v0.5.36/docs/2026-11-09_security-center-13.8-report.md)。
- 高光玻璃兼容表面不表示真实背景折射或原生 MiGlass；视觉和稳定性仍需在目标 ROM 上验收。

## 安装与启用

1. 从本仓库 Release 下载并安装正式 APK；升级时请使用相同正式签名证书。
2. 在 LSPosed 中启用模块，核对上述作用域。更新后重启 SystemUI 加载新 Hook；首次安装或从早期版本升级时补选 System（system / system_server），随后重启设备。

首次加载系统侧截屏剪贴板保护同样需要 System 作用域及整机重启；后续修改开关按配置通知应用。语言切换只改变模块界面，无需重启 SystemUI 或手机管家。升级后原有图标、布局与语言设置保留，控制中心未推送草稿不会自动发布。

## 从旧包名迁移

从 `0.3.150` 起，应用包名为 `io.github.yudigaga.fusionstatusbar`。旧版 `com.xtjm.fusionstatusbar` 是另一应用，无法直接覆盖安装或自动继承配置。

1. 在旧版设置中选择“导出配置备份”。
2. 安装新版，在设置中选择“导入配置备份”。
3. 在 LSPosed 中关闭旧模块，只启用新版，再重启系统界面。确认新版正常后可卸载旧包。

不要同时启用新旧两个模块，以免两套 Hook 同时修改系统界面。

## 文档与反馈

- [0.5.34 及更早版本的历史更新](HISTORY.md)：保留对应版本的下载地址、签名和验证范围。
- [主仓文档导航](https://github.com/yudigaga/FusionStatusBar/blob/v0.5.36/docs/README.md)：功能说明、构建方法和开发记录。
- [问题反馈](https://github.com/yudigaga/FusionStatusBar/issues)：请提供模块版本、ROM、宿主版本、作用域、复现步骤及脱敏日志。

## 赞助

如果你喜欢这个项目，欢迎请我喝杯咖啡 ☕

<img src="docs/assets/sponsor-wechat.png" alt="微信赞赏码" width="360" />
