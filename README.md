# FusionStatusBar 状态栏融合图标

FusionStatusBar 是面向 MIUI/HyperOS 的 LibXposed 模块，提供融合图标、双排状态栏、时钟天气与设备遥测、控制中心布局和外观编辑，以及桌面应用隐藏与手势。

## 功能

- 调整融合图标、状态栏布局和双排显示。
- 自定义时钟与天气，显示温度、功率电流和网络速度等信息。
- 编辑控制中心的布局、磁贴与外观，并提供预览和配置备份。
- 横屏自定义布局、分组成员图标缩放、统一容器材质与全局描边。
- 分别调整电源菜单、音量菜单、通知中心与悬浮通知外观，支持三条电源菜单和短款音量条。
- 隐藏桌面应用图标，自定义十种桌面手势，选择系统动作、应用、活动、快捷方式和功能切换。
- 设置页面、底部导航和公共弹窗使用 Compose/Miuix 控件。
- 杂项页提供可选的链式启动确认移除，设置页可切换毛玻璃悬浮底栏。

## 最新正式版：0.3.197

- 汇总远端 0.3.193 之后的全部变化：杂项页面、链式启动开关、毛玻璃悬浮底栏及六页导航布局。
- 链式启动最终在 system_server 的 MIUI 确认入口处理；开启后放行，关闭后保留原生行为。早期安全中心自动点击方案已移除。
- 修正作用域，保留必需的 `system`，移除不需要的 `android`；APK 作用域与源码一致性纳入构建检查。

[下载正式 APK](https://github.com/Xposed-Modules-Repo/io.github.yudigaga.fusionstatusbar/releases/tag/211-0.3.197) · [0.3.193 到 0.3.197 完整更新说明](https://github.com/yudigaga/FusionStatusBar/blob/v0.3.197/docs/release-notes-v0.3.197.md)

升级后在 LSPosed 明确勾选 **System（system / system_server）** 并重启手机，再打开 FusionStatusBar 同步配置。旧 `android` 选项可取消。“移除链式启动弹窗”默认关闭，需要时在“杂项”开启；修改杂项配置时应保持设置应用包可用。

本版归档 Debug/Release 各 1116 项单元测试通过，lint 各 0 错误、97 条警告；未进行本版设备安装、system_server/SystemUI 注入、目标 ROM 或功耗验收。

正式 APK SHA-256：`119122b8e9d3c7db4a5d9354fabdada5170963777be51f2fb95efbcc33a5b7f9`。签名证书 SHA-256：`ccfaf42f8f14bb36973aeb971572fcc956a256196f68ff088340dfa7eca96fe2`。

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
3. 重启系统界面或设备，再打开模块设置并确认连接状态。

## 从旧包名迁移

从 `0.3.150` 起，应用包名为 `io.github.yudigaga.fusionstatusbar`。旧版 `com.xtjm.fusionstatusbar` 是另一应用，无法直接覆盖安装或自动继承配置。

1. 在旧版设置中选择“导出配置备份”。
2. 安装新版，在设置中选择“导入配置备份”。
3. 在 LSPosed 中关闭旧模块，只启用新版，再重启系统界面。确认新版正常后可卸载旧包。

不要同时启用新旧两个模块，以免两套 Hook 同时修改系统界面。

## 源码与反馈

[项目源码及问题反馈](https://github.com/yudigaga/FusionStatusBar)
