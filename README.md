# WDM2VST Ultra

WDM2VST Ultra 是一款 Windows 音频桥接工具，通过内核级 WDM 驱动实现系统音频与 DAW（数字音频工作站）之间的低延迟音频路由。

## 功能特性

- **WDM2VST Ultra** — 将系统音频（WDM）捕获到 DAW 中
- **VST2WDM Ultra** — 将 DAW 音频路由到系统输出设备
- **Send Ultra** — 跨插件音频发送器
- **Receive Ultra** — 跨插件音频接收器
- **内核驱动** — 8 通道播放 + 8 通道录制，通过共享内存实现低延迟传输

## 系统要求

- Windows 10/11 x64（版本 1809 及以上）
- 支持 VST3 的 DAW 宿主软件
- 管理员权限（用于驱动安装）

## 安装

1. 下载 `WDM2VST_Ultra_v*_Setup.exe`
2. 以管理员身份运行安装程序
3. 选择需要安装的组件
4. 安装完成后**重启计算机**
5. 在 DAW 中刷新插件列表

## 音频端点

安装驱动后，系统中会出现以下虚拟音频端点：

| 播放（Playback） | 录制（Capture） |
|-----------------|----------------|
| Ultra PLAY 1/2  | Ultra REC 1/2  |
| Ultra PLAY 3/4  | Ultra REC 3/4  |
| Ultra PLAY 5/6  | Ultra REC 5/6  |
| Ultra PLAY 7/8  | Ultra REC 7/8  |

## 使用说明

### 从系统捕获音频到 DAW
1. 将 Windows 音频输出设备设置为某个 Ultra PLAY 端点
2. 在 DAW 中加载 **WDM2VST Ultra** 插件
3. 插件将从对应的 Ultra REC 端点捕获音频

### 从 DAW 输出音频到系统
1. 在 DAW 中加载 **VST2WDM Ultra** 插件
2. 将系统音频输入设备设置为某个 Ultra REC 端点
3. 插件音频将路由到对应的 Ultra PLAY 端点

### 跨插件音频传输
- 使用 **Send Ultra** 发送音频流
- 使用 **Receive Ultra** 接收音频流
- 支持在同一 DAW 内的不同轨道/插件之间传输音频

## 版本历史

### v1.0.0
- 首个正式版本
- 8 通道播放 + 8 通道录制
- IPC 共享内存音频传输
- 中英文安装界面
- WDM2VST、VST2WDM、Send、Receive 四款 VST3 插件

## 许可证

免费使用。版权所有 &copy; 2026 GeekASMR。

## 相关链接

- [GitHub 仓库](https://github.com/GeekASMR/WDM2VST-Ultra)
