# FusionStatusBar 状态栏融合图标

FusionStatusBar 是面向 MIUI/HyperOS 的 LibXposed 模块，提供融合图标、双排状态栏、时钟天气与设备遥测、控制中心布局和外观编辑，以及桌面应用隐藏与手势。

## 功能

- 调整融合图标、状态栏布局和双排显示，选择充电时显示闪电或电量数字。
- 自定义时钟与天气，显示温度、功率电流和网络速度等信息。
- 编辑控制中心的布局、磁贴与外观，并提供预览和配置备份。
- 横屏自定义布局、分组成员图标缩放、统一容器材质与全局描边。
- 分别调整电源菜单、音量菜单、通知中心与悬浮通知外观，支持三条电源菜单和短款音量条。
- 隐藏桌面应用图标，自定义桌面手势与返回停顿，选择系统动作、应用、活动、快捷方式和功能切换。
- 设置页面、底部导航和公共弹窗使用 Compose/Miuix 控件。
- 杂项页提供可选的链式启动确认移除、截屏剪贴板保护和指定版本的手机管家扩展，设置页可切换毛玻璃悬浮底栏。

## 最新正式版：0.5.24

- 版本号 `0.5.24`，构建号 `238`，沿用末位满 100、中间位满 10 的版本进位规则。以下为相对 `0.5.21` 的累计更新。
- “融合图标 → 显示 → 充电时显示充电图标”默认开启；关闭后充电期间显示电量数字，保留圆环配色、位置与缩放。旧配置缺少该字段时默认开启。
- “杂项 → 截屏 → 截屏自动写入剪贴板”默认关闭。开启后在系统侧 SettingsProvider 保护 Secure 设置 `mi_screen_shots_write_clipboard_enable=1`；关闭时写回 `0` 并解除保护，保留原系统权限和跨用户检查。
- “杂项 → 手机管家扩展”新增 26 项独立开关，默认全部关闭；仅适配 `com.miui.securitycenter`、`13.8.0-261020.0.1`、versionCode `40001380`，未知版本不套用新增映射。涵盖隐私与出行、扫描与确认、游戏/视频工具箱、电池与充电，另提供 `1～60` 分钟的参考亮屏时间显示粒度，默认 `1` 分钟，仅改变显示粒度。
- Release 先启用 R8 代码压缩、优化和混淆，再生成正式签名包；精确保留 LibXposed 入口及回调，未启用资源压缩。优化 APK 的入口、Manifest/XML 构造和枚举配置边界已单独验包，映射中有 `523` 个模块类型重命名。

[下载正式 APK](https://github.com/Xposed-Modules-Repo/io.github.yudigaga.fusionstatusbar/releases/tag/238-0.5.24) · [0.5.24 更新说明与验证范围](https://github.com/yudigaga/FusionStatusBar/blob/v0.5.24/docs/release-notes-v0.5.24.md)

使用原正式证书签名，可覆盖更新 `0.5.21`。本版没有新增 LSPosed 作用域；升级时核对系统、SystemUI、插件、桌面与手机管家作用域已勾选。从更早版本升级时，仍按 [0.3.197 升级说明](https://github.com/yudigaga/FusionStatusBar/blob/v0.3.197/docs/release-notes-v0.3.197.md) 核对 **System（system / system_server）** 作用域。已有图标位置与缩放设置保留。

首次加载系统侧截图保护时，需勾选系统作用域并整机重启；后续修改开关按配置通知应用，无需每次重启。手机管家扩展需勾选 `com.miui.securitycenter`，安装新版后重启手机管家相关进程或手机，修改选项后可能需要重建对应页面或工具箱；仅重启 SystemUI 不等于重启手机管家。

手机管家选项主要开放本地入口、支持判断、名单或显示，不会增加缺失硬件。风扇、游戏音效和独显增强标为 UI 功能；超分、插帧、HDR、影院和充电仍依赖原生服务与硬件。“三秒进游戏”不保证进入耗时，填充展示不保证扩大视野；视频工具箱温度选项不解除底层硬件温控。影院缺少杜比支持时可能导致手机管家崩溃，晕车缓解与车祸检测仍需真实传感器。完整边界见[手机管家实施报告](https://github.com/yudigaga/FusionStatusBar/blob/v0.5.24/docs/2026-11-09_security-center-13.8-report.md)。

本版归档记录 Debug、Release 各 `204` 类、`1,572` 项完整单元测试通过，失败、错误和跳过均为 `0`；两种变体 lint 均为 `0` 错误、`101` 条警告。Python 工具测试 `45` 项通过，其中包含 `17` 项 R8 验包回归。普通 JVM 单元测试执行在混淆前类上，优化 APK 的结构检查另有记录；两者都不能代替设备验收。本版手机安装、真实 LSPosed 回调、目标 ROM、硬件与服务效果尚未验收；远端 CI 以发布提交的 GitHub Actions 为准。

R8 的 `mapping.txt`、最终规则、seeds、usage、`r8-verification.json` 和两套测试、lint 报告随[源码发布页的验证附件](https://github.com/yudigaga/FusionStatusBar/releases/tag/v0.5.24)提供。签名、APK 元数据与验证范围见 [0.5.24 更新说明](https://github.com/yudigaga/FusionStatusBar/blob/v0.5.24/docs/release-notes-v0.5.24.md)及[本次构建记录](https://github.com/yudigaga/FusionStatusBar/blob/v0.5.24/artifacts/release-v0.5.24.json)。

当前高光玻璃没有实现真实背景折射，尚未完成目标 ROM 的真实 MiGlass 绘制、视觉和稳定性验收。

正式 APK 大小：`3,335,213` 字节，SHA-256：`c81924b0db367c26822c3032476eb1fbba59c02b49ff05b9e574e42886eb3789`。本次从干净源码提交 `e2ab818` 重新构建，归档为 `official_signed`。签名证书 SHA-256：`ccfaf42f8f14bb36973aeb971572fcc956a256196f68ff088340dfa7eca96fe2`。

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
3. 首次安装或补选 System 作用域后重启设备，使系统侧 Hook 加载，再打开模块设置并确认连接状态。

## 从旧包名迁移

从 `0.3.150` 起，应用包名为 `io.github.yudigaga.fusionstatusbar`。旧版 `com.xtjm.fusionstatusbar` 是另一应用，无法直接覆盖安装或自动继承配置。

1. 在旧版设置中选择“导出配置备份”。
2. 安装新版，在设置中选择“导入配置备份”。
3. 在 LSPosed 中关闭旧模块，只启用新版，再重启系统界面。确认新版正常后可卸载旧包。

不要同时启用新旧两个模块，以免两套 Hook 同时修改系统界面。

## 源码与反馈

[项目源码及问题反馈](https://github.com/yudigaga/FusionStatusBar)
