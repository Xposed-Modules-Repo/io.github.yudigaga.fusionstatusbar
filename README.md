# FusionStatusBar 状态栏融合图标

FusionStatusBar 是面向系统界面的 LibXposed 模块，提供融合图标、双排状态栏、时钟天气与设备遥测，以及控制中心布局和外观编辑。

## 功能

- 调整融合图标、状态栏布局和双排显示。
- 自定义时钟与天气，显示温度、功率电流和网络速度等信息。
- 编辑控制中心的布局、磁贴与外观，并提供预览和配置备份。
- 横屏自定义布局、分组成员图标缩放、统一容器材质与全局描边。
- 分别调整电源菜单、音量菜单、通知中心与悬浮通知外观，支持三条电源菜单和短款音量条。

## 最新正式版：0.3.187

- HyperOS 移动信号格优先读取 `SignalStrength.getMiuiLevel()`，与系统原生等级来源保持一致。
- MIUI 等级不可用时明确标记不可用，不以 Android 通用等级替代。
- Wi-Fi 强度仍独立显示；双排信号仅显示移动网络等级。

[下载正式 APK](https://github.com/Xposed-Modules-Repo/io.github.yudigaga.fusionstatusbar/releases/tag/201-0.3.187) · [完整更新说明](https://github.com/yudigaga/FusionStatusBar/blob/v0.3.187/docs/release-v0.3.187.md)

本版 Debug/Release 各 1006 项单元测试通过，lint 各 0 错误、66 条警告；未进行本版实体设备安装、SystemUI 注入或目标 ROM 验收。

正式 APK SHA-256：`05a3fa5e9f3c75a6dbca9615c3be709a28099d3e3d5b6c2154cb295fc4e8e90e`。签名证书 SHA-256：`ccfaf42f8f14bb36973aeb971572fcc956a256196f68ff088340dfa7eca96fe2`。

## 0.3.173 更新（历史）

汇总 0.3.152-0.3.173 的控制中心布局、材质与绘制修复，统一音乐和融合中心的形状与底色，修复磁贴遮罩和重启后材质恢复，并新增系统菜单扩展。

[完整更新说明](https://github.com/yudigaga/FusionStatusBar/blob/v0.3.173/docs/release-v0.3.173.md)

正式包继续使用 `io.github.yudigaga.fusionstatusbar` 和原签名，可覆盖 0.3.150 及后续正式版。历史 0.3.173 验证记录未进行实体手机安装、SystemUI 注入或目标 ROM 验收。

## 适用范围

- Android 13（API 33）及以上，使用支持 LibXposed API 102 的框架。
- 作用域为 `com.android.systemui`；设备存在 `miui.systemui.plugin` 时也勾选该作用域。
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
