# WDM2VST Ultra

[🇨🇳 中文版](#-中文说明-chinese) | [🇬🇧 English Version](#-english-version)

WDM2VST Ultra 是一款 Windows 音频桥接工具，通过内核级 WDM 驱动实现系统音频与 DAW（数字音频工作站）之间的低延迟音频路由。

## 🇨🇳 中文说明 (Chinese)

### 功能特性
- **WDM2VST Ultra** — 将系统音频（WDM）捕获到 DAW 中
- **VST2WDM Ultra** — 将 DAW 音频路由到系统输出设备
- **Send Ultra 发送端** — 跨插件音频发送器
- **Receive Ultra 接收端** — 跨插件音频接收器
- **内核驱动** — 8 通道播放 + 8 通道录制，通过共享内存实现低延迟传输

### 系统要求
- Windows 10/11 x64（版本 1809 及以上）
- 支持 VST3 的 DAW 宿主软件
- 管理员权限（用于驱动安装）

### 安装
1. 下载 `WDM2VST_Ultra_v*_Setup.exe`
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

---

## 🇬🇧 English Version

WDM2VST Ultra is a Windows audio bridging tool that provides low-latency audio routing between system audio and your DAW via a kernel-level WDM driver.

### Features
- **WDM2VST Ultra** — Capture system audio (WDM) into your DAW
- **VST2WDM Ultra** — Route DAW audio out to system output devices
- **Send Ultra** — Inter-plugin audio sender
- **Receive Ultra** — Inter-plugin audio receiver
- **Kernel Driver** — 8 playback channels + 8 capture channels with low-latency shared memory transport

### System Requirements
- Windows 10/11 x64 (Version 1809 or higher)
- VST3 compatible DAW host
- Administrator privileges (for driver installation)

### Installation
1. Download `WDM2VST_Ultra_v*_Setup.exe`
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

### Usage Guide
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

---

## 版本历史 / Changelog

### v1.0.1
- **Plugin Titles**: Changed "Send/Receive" titles to actual plugin names ("Send Ultra 发送端" / "Receive Ultra 接收端")
- **Branding**: Unified vendor name to **GeekASMR** across all components
- **Installer**: Fixed Chinese translation gaps in the installation wizard
- **Driver**: Updated driver version to 1.0.1.0
- **VST3**: Added custom folder icon for VST3 directory

### v1.0.0
- First release / 首个正式版本
- 8 channel playback + capture / 8通道播放+录制
- IPC shared memory transport / IPC共享内存传输
- Bilingual installer / 中英文安装界面
- Includes 4 VST3 plugins / 包含 4 款 VST3 插件

## 致谢 / Acknowledgments

本项目在开发过程中使用或参考了以下优秀的开源项目，特此致谢：
- **[JUCE](https://github.com/juce-framework/JUCE)** - The audio application framework.
- **[Scream](https://github.com/duncanthrax/scream)** - Virtual network sound card for Microsoft Windows.
- **[Inno Setup](https://jrsoftware.org/isinfo.php)** - Free installer for Windows programs.

This project uses or references the following excellent open-source projects. We express our sincere gratitude to their authors:
- **[JUCE](https://github.com/juce-framework/JUCE)** - The audio application framework.
- **[Scream](https://github.com/duncanthrax/scream)** - Virtual network sound card for Microsoft Windows.
- **[Inno Setup](https://jrsoftware.org/isinfo.php)** - Free installer for Windows programs.

## 许可证 / License
Free to use / 免费使用. Copyright &copy; 2026 GeekASMR.

## 相关链接 / Links
- [GitHub Repository](https://github.com/GeekASMR/WDM2VST-Ultra)
