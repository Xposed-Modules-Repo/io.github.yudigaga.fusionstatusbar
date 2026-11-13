# 历史更新

以下内容从原 README 迁入，保留各版本发布时的正文和验证范围；其中的“本版”“当前”等表述指对应历史版本。

[返回项目首页](README.md)

## 0.5.25 更新（历史）

- 版本号 `0.5.25`，构建号 `239`；以下为相对已发布 `0.5.24` R8 正式版的更新。
- 新增“设置 → 界面 → 应用语言”，提供跟随系统及简中、繁中、英、日、韩、俄、西七种语言。每种语言覆盖 `850` 条 string，包含设置、导航、对话框、控制中心画布与编辑器、无障碍提示，以及手机管家 26 项设置的分类、标题和说明。
- 切换前等待设置保存或已明确发起的控制中心发布成功；保存失败时取消切换。重建后恢复页面、滚动位置、编辑会话和杂项设置，并重新提交尚未完成的明确保存目标。未推送草稿保持草稿，保留发布期间的后续修改。
- 语言选择由 Android 原生 `LocaleManager` 保存；跟随系统会清除应用语言覆盖。切换模块界面语言无需重启 SystemUI 或手机管家，不改变这些宿主进程的全局语言。用户文本、配置键、已保存的时钟格式和既有中文农历语义保留。
- 延续 `0.5.24` 已启用的 Release R8 压缩、优化和混淆；标准构建、验证及 CI 改为只处理 Release，并核对成品 DEX 的 R8 标记与 mapping 编译器版本、映射 ID。原有充电显示、截屏剪贴板和手机管家扩展保持独立，本版没有新增 LSPosed 作用域。

[下载正式 APK](https://github.com/Xposed-Modules-Repo/io.github.yudigaga.fusionstatusbar/releases/tag/239-0.5.25) · [0.5.25 更新说明与验证范围](https://github.com/yudigaga/FusionStatusBar/blob/v0.5.25/docs/release-notes-v0.5.25.md) · [多语言实现说明](https://github.com/yudigaga/FusionStatusBar/blob/v0.5.25/docs/2026-11-09_app-languages.md)

沿用原正式证书，可覆盖更新 `0.5.24` 及后续本地正式签名版本。已有系统、SystemUI、插件、桌面与手机管家作用域及首次加载系统侧截图保护的整机重启要求保持适用；具体功能边界见下方历史说明。

本版原始归档记录 Release `208` 类、`1,598` 项完整单元测试通过，失败、错误和跳过均为 `0`；lint 为 `0` 错误、`145` 条警告，高风险政策通过。本轮 Python 工具回归 `62` 项和独立 R8 成品验包通过；本次发布未执行 Debug 构建或验收。R8 版本为 `8.13.19`，外部入口、构造和回调另有静态核验。普通 JVM 单测执行在混淆前类上，Robolectric 重建和静态 APK 检查不能代替手机验收。本版尚未验证手机安装、真实语言自动重建与跨重启持久化、R8 后实际 LSPosed 回调、ROM、硬件或服务效果；远端 CI 以本版发布提交的 GitHub Actions 为准。

最终 APK 见[主仓 v0.5.25 发布页](https://github.com/yudigaga/FusionStatusBar/releases/tag/v0.5.25)；R8 mapping、合并规则、seeds、usage、测试和 lint 报告随验证附件提供。构建来源和最终签名信息见[本次构建记录](https://github.com/yudigaga/FusionStatusBar/blob/v0.5.25/artifacts/release-v0.5.25.json)。原始构建保留 `buildMode=local_dirty_signed`、`sourceCommit=fe7bb9d230781985779e11e7151fc509acffd59f`、`sourceDirty=true` 和 `validationInput=existing_build_outputs`；随附源码快照、文件索引和补丁记录当时的未提交改动，发布提交与 APK 构建来源分别记录。

正式 APK 大小：`3,875,941` 字节，SHA-256：`ce5d19fd99bf16aba7b02a807d5bbde248b4143fd8e87a3b627884b528d1989c`。签名证书 SHA-256：`ccfaf42f8f14bb36973aeb971572fcc956a256196f68ff088340dfa7eca96fe2`。

## 0.5.24 更新（历史）

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
