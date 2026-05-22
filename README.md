# WDM2VST Ultra

[![Latest release](https://img.shields.io/github/v/release/GeekASMR/WDM2VST-Ultra?style=flat-square&color=E91E63)](https://github.com/GeekASMR/WDM2VST-Ultra/releases/latest)
[![Total downloads](https://img.shields.io/github/downloads/GeekASMR/WDM2VST-Ultra/total?style=flat-square&label=total%20downloads&color=0E8A16)](https://github.com/GeekASMR/WDM2VST-Ultra/releases)
[![GitHub stars](https://img.shields.io/github/stars/GeekASMR/WDM2VST-Ultra?style=flat-square&color=FFD700)](https://github.com/GeekASMR/WDM2VST-Ultra/stargazers)
[![Open issues](https://img.shields.io/github/issues/GeekASMR/WDM2VST-Ultra?style=flat-square&color=orange)](https://github.com/GeekASMR/WDM2VST-Ultra/issues)
[![Platform](https://img.shields.io/badge/platform-Windows%2010%2F11-blue?style=flat-square)](#system-requirements)

[🇨🇳 中文版](#-中文说明-chinese) | [🇬🇧 English Version](#-english-version) | [💚 支持开发 / Support Development](#-支持开发--support-development)

WDM2VST Ultra 是一款 Windows 音频桥接工具，通过内核级 WDM 驱动实现系统音频与 DAW（数字音频工作站）之间的低延迟音频路由。

WDM2VST Ultra is a Windows audio bridging tool that provides low-latency audio routing between system audio and your DAW via a kernel-level WDM driver.

---

## 🇨🇳 中文说明 (Chinese)

### 功能特性
- **WDM2VST Ultra** — 将系统音频（WDM）捕获到 DAW 中
- **VST2WDM Ultra** — 将 DAW 音频路由到系统输出设备
- **INST WDM2VST Ultra** — Instrument 模式版本（用于乐器轨道宿主）
- **Send Ultra 发送端** — 跨插件音频发送器
- **Receive Ultra 接收端** — 跨插件音频接收器
- **内核驱动** — 8 通道播放 + 8 通道录制，通过共享内存实现低延迟传输

### 系统要求
- Windows 10/11 x64（版本 1809 及以上）
- 支持 VST3 的 DAW 宿主软件
- 管理员权限（用于驱动安装）

### 安装
1. 下载 [`WDM2VST_Ultra_v*_Setup.exe`](https://github.com/GeekASMR/WDM2VST-Ultra/releases/latest)
2. 以管理员身份运行安装程序
3. 选择需要安装的组件
4. 安装完成后**重启计算机**
5. 在 DAW 中刷新插件列表

### 音频端点
安装驱动后，系统中会出现以下虚拟音频端点：

| 播放 (Playback) | 录制 (Capture) |
|-----------------|----------------|
| Ultra PLAY 1/2  | Ultra REC 1/2  |
| Ultra PLAY 3/4  | Ultra REC 3/4  |
| Ultra PLAY 5/6  | Ultra REC 5/6  |
| Ultra PLAY 7/8  | Ultra REC 7/8  |

### 使用说明

#### 从系统捕获音频到 DAW
1. 将 Windows 音频输出设备设置为某个 Ultra PLAY 端点
2. 在 DAW 中加载 **WDM2VST Ultra** 插件
3. 插件将从对应的 Ultra REC 端点捕获音频

#### 从 DAW 输出音频到系统
1. 在 DAW 中加载 **VST2WDM Ultra** 插件
2. 将系统音频输入设备设置为某个 Ultra REC 端点
3. 插件音频将路由到对应的 Ultra PLAY 端点

#### 跨插件音频传输
- 使用 **Send Ultra 发送端** 发送音频流
- 使用 **Receive Ultra 接收端** 接收音频流
- 支持在同一 DAW 内的不同轨道/插件之间传输音频

### 已知限制 / 常见问题

- **游戏反作弊误报**：Easy Anti-Cheat / 腾讯 ACE / 网易易盾会保守拦截所有非微软签名的内核驱动，与本驱动是否影响游戏无关。临时方案：玩游戏前 `net stop WDM2VSTUltra` 停用驱动服务，玩完再 `net start WDM2VSTUltra` 启回。长期方案见下方 [支持开发](#-支持开发--support-development)。
- **蓝牙耳机麦只有单声道**：A2DP/HFP 协议本身限制，所有软件取到的都是单声道，不是本插件 bug。
- 更多见 [FAQ](docs/FAQ.md) 和 [已关闭 issues](https://github.com/GeekASMR/WDM2VST-Ultra/issues?q=is%3Aissue+is%3Aclosed)。

---

## 🇬🇧 English Version

### Features
- **WDM2VST Ultra** — Capture system audio (WDM) into your DAW
- **VST2WDM Ultra** — Route DAW audio out to system output devices
- **INST WDM2VST Ultra** — Instrument-mode variant (for instrument-track hosts)
- **Send Ultra** — Inter-plugin audio sender
- **Receive Ultra** — Inter-plugin audio receiver
- **Kernel Driver** — 8 playback channels + 8 capture channels with low-latency shared memory transport

### System Requirements
- Windows 10/11 x64 (Version 1809 or higher)
- VST3 compatible DAW host
- Administrator privileges (for driver installation)

### Installation
1. Download [`WDM2VST_Ultra_v*_Setup.exe`](https://github.com/GeekASMR/WDM2VST-Ultra/releases/latest)
2. Run the installer as Administrator
3. Select the components to install
4. **Restart your computer** after installation
5. Rescan plugins in your DAW

### Audio Endpoints
After installing the driver, the following virtual audio endpoints will be available:

| Playback        | Capture        |
|-----------------|----------------|
| Ultra PLAY 1/2  | Ultra REC 1/2  |
| Ultra PLAY 3/4  | Ultra REC 3/4  |
| Ultra PLAY 5/6  | Ultra REC 5/6  |
| Ultra PLAY 7/8  | Ultra REC 7/8  |

### Usage

#### Capture System Audio to DAW
1. Set your Windows default playback device to an Ultra PLAY endpoint
2. Load the **WDM2VST Ultra** plugin in your DAW
3. The plugin will capture audio from the corresponding Ultra REC endpoint

#### Route DAW Audio to System
1. Load the **VST2WDM Ultra** plugin in your DAW
2. Set your system recording device (or VoIP input) to an Ultra REC endpoint
3. The plugin will route audio to the corresponding Ultra PLAY endpoint

#### Inter-Plugin Audio Routing
- Use **Send Ultra** to send an audio stream
- Use **Receive Ultra** to receive an audio stream
- Supports transmitting audio between different tracks/plugins within the same DAW

### Known Limitations

- **Game anti-cheat false positives**: Easy Anti-Cheat / Tencent ACE / NetEase 易盾 conservatively flag any non-Microsoft-signed kernel driver, regardless of what it does. Workaround: `net stop WDM2VSTUltra` before gaming, `net start` after. See [support](#-支持开发--support-development) for the long-term WHQL fix.
- **Bluetooth mic mono only**: A2DP/HFP protocol limitation — every recording app gets a mono stream from Bluetooth headsets. Not a plugin bug.
- See [FAQ](docs/FAQ.md) and [closed issues](https://github.com/GeekASMR/WDM2VST-Ultra/issues?q=is%3Aissue+is%3Aclosed) for more.

---

## 💚 支持开发 / Support Development

### 为什么需要支持

WDM2VST Ultra 当前使用合法的**第三方代码签名证书**——足以让驱动在 Windows 上加载，但**没有微软的二次签名（WHQL/Attestation）**。结果是：

- 国内主流游戏的反作弊系统（腾讯 ACE、网易易盾、Easy Anti-Cheat）会把所有未经微软签名的内核驱动一律标红，提示「检测到可疑驱动，请卸载」，**与驱动是否真正影响游戏无关，纯粹看签名来源**。
- 这是行业现状。唯一彻底解决的办法是申请 **Microsoft Partner Center 的驱动签名认证（WHQL）**，让所有反作弊系统统一放行。

### 这笔钱用在哪

申请 WHQL 必须先购买**有效的 EV 代码签名证书**（约 ¥2000-3000/年），加上微软认证流程的隐性成本（HLK 测试设备、试错次数）。

每一笔捐赠都明确用于支付 WHQL 认证的费用，**金额完全透明、进度公开**。WHQL 认证落地后会立刻发布新版本，届时游戏环境下不再被拦截。

### 怎么支持

> 🌟 **<https://ultra.asmrtop.cn/donate/>**

页面支持 微信支付 / 支付宝，¥5 起，金额自定。也可以留下昵称和留言（会显示在感谢墙）。

不强制——给项目点个 ⭐ 也是最好的鼓励。

### Why Support

WDM2VST Ultra currently ships with a legitimate third-party code-signing certificate — enough for Windows to load the driver, but **without Microsoft's WHQL/Attestation co-signature**. As a result:

- Mainstream Chinese game anti-cheats (Tencent ACE, NetEase 易盾, Easy Anti-Cheat) flag every non-Microsoft-signed kernel driver and ask the user to uninstall it. **It's strictly about signature provenance, not what the driver actually does.**
- The industry's only definitive fix is to obtain **Microsoft Partner Center driver attestation (WHQL)**, which puts the driver on every anti-cheat's allowlist.

### Where the money goes

WHQL requires a valid **EV code-signing certificate** (~¥2000-3000/yr) plus the implicit cost of the certification process (HLK test rigs, retries).

Every donation goes explicitly toward WHQL costs — **fully transparent, progress public**. As soon as WHQL clears, a new release ships and game anti-cheats stop blocking the driver.

### How to support

> 🌟 **<https://ultra.asmrtop.cn/donate/>**

WeChat Pay / Alipay supported, ¥5 minimum, custom amount allowed. Optional nickname + message appears on the contributor wall.

No pressure — a GitHub ⭐ is just as appreciated.

---

## 版本历史 / Changelog

完整发布记录见 [Releases 页面](https://github.com/GeekASMR/WDM2VST-Ultra/releases)。下面列出近期重点：

Latest highlights — see the full [release page](https://github.com/GeekASMR/WDM2VST-Ultra/releases) for everything.

### v1.0.6 — Locked-device UI persistence fix
- W2V: 锁定设备在关闭并重新打开插件窗口后正确显示，不再被清空
- W2V: 修复了一个潜伏 bug，常规 WASAPI 设备选择没有同步回处理器，导致硬件麦克风的锁定 guard 形同虚设
- 内部：修复 `P2PTransport.h` 文件损坏（影响 32-bit 构建，不影响已发布的 v1.0.5 二进制）

### v1.0.5 — Bluetooth survival, endpoint rename robustness
- W2V: 锁定设备消失时（蓝牙断开 / USB 拔出）主动 `closeAudioDevice()` 保持静默，蓝牙重连后自动恢复，不再 fallback 到错误的麦克风
- 端点被改名为不含通道编号的字符串时，IPC 通道列表不再消失
- 驱动：KMDF / HVCI 兼容性加固

### v1.0.4 — IPC stability + LUNA fix
- W2V: LUNA 工程加载顺序问题（state 先于 IPC bridge 就绪时无法连接）
- 驱动元数据清理，VST3 子分类 `Tools`

### v1.0.3 — V2W silence gate + UI polish
- V2W: REC 端点静音门，避免空轨道占用 IPC 带宽
- UI: 延迟标签清理

### v1.0.1 — Branding cleanup
- 插件标题统一为 "Send Ultra 发送端" / "Receive Ultra 接收端"
- 厂商名统一为 **GeekASMR**
- 安装器中文翻译补全
- VST3 文件夹自定义图标

### v1.0.0 — First release
- 8 通道播放 + 录制
- IPC 共享内存传输
- 中英文双语安装界面
- 4 款 VST3 插件

---

## 致谢 / Acknowledgments

本项目在开发过程中使用或参考了以下优秀的开源项目，特此致谢。
This project uses or references the following excellent open-source projects:

- **[JUCE](https://github.com/juce-framework/JUCE)** — Audio application framework
- **[Scream](https://github.com/duncanthrax/scream)** — Virtual network sound card for Windows
- **[Tauri](https://tauri.app/)** — Lightweight cross-platform installer shell

## 许可证 / License
Free to use / 免费使用. Copyright &copy; 2026 GeekASMR.

## 相关链接 / Links
- [GitHub Releases](https://github.com/GeekASMR/WDM2VST-Ultra/releases) — 下载安装器 / Download installers
- [Issue tracker](https://github.com/GeekASMR/WDM2VST-Ultra/issues) — 报告 bug / 功能建议
- [FAQ](docs/FAQ.md) — 常见问题
- 🌟 [支持开发 / Donate](https://ultra.asmrtop.cn/donate/)
