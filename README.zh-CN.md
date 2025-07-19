<a href="./README.md"><img src="https://img.shields.io/badge/Language-English-lightgrey?style=for-the-badge" alt="English"></a> <a href="./README.zh-CN.md"><img src="https://img.shields.io/badge/语言-简体中文-blue?style=for-the-badge" alt="简体中文"></a>

# OpenWave: 构筑流动的个人声场

[![许可证: Apache 2.0](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Discord](https://img.shields.io/discord/YOUR_DISCORD_ID?label=Discord&logo=discord&color=5865F2)](https://discord.gg/YOUR_INVITE_LINK)
[![GitHub Discussions](https://img.shields.io/github/discussions/YOUR_USERNAME/openwave?label=Discussions&logo=github)](https://github.com/YOUR_USERNAME/openwave/discussions)

> [!NOTE]
> 本项目尚处于早期开发阶段，可能存在大量Bug且功能不完整。不建议在生产环境中使用。

**让音乐，真正随你而动。** OpenWave 是一个开源项目，致力于创造一种革命性的家庭音频体验。我们相信，未来的背景音乐不应再局限于冰冷的“房间”，而应是以“人”为中心的、动态流动的、无缝沉浸的个人声场。

---

## 🌟 核心理念

在当今的多房间音频（Multi-room Audio）系统中，音乐是被绑定在特定空间的。当您从客厅走到厨房时，音乐并不会跟随您。您需要手动切换，或者将整个屋子的音响都调至最大声，这破坏了体验的私密性和沉浸感。

**OpenWave 彻底改变了这一点。**

通过集成先进的室内定位技术和智能家居平台，OpenWave 能够实时感知您在家中的位置，并像一个围绕着您的“音乐波”一样，智能地、平滑地将音频在不同位置的音响之间切换和过渡。无论您走到哪里，您都始终处于最佳的听音位置（Sweet Spot）。

### 流程可视化

想象一下这个场景：

**1. 您身处客厅：**
声音主要来自离您最近的音响，为您创造一个个人声场。

```
+-----------------+     +-----------------+     +-----------------+
|      客厅       |     |      走廊       |     |      书房       |
|                 |     |                 |     |                 |
|    (( (🚶) ))    |     |      . . .      |     |                 |
|                 |     |                 |     |                 |
|    🔊 (大声)    |     |    🔉 (中等)    |     |    🔈 (关闭)     |
+-----------------+     +-----------------+     +-----------------+
      音频节点A             音频节点B             音频节点C
```

**2. 当您走向书房时：**
OpenWave 检测到您的移动。它并非生硬地切换音响，而是平滑地将客厅音响的声音淡出，同时将走廊音响的声音淡入，并开始预热书房的音响。这股“音乐波”正随着您移动。

```
+-----------------+     +-----------------+     +-----------------+
|      客厅       |     |      走廊       |     |      书房       |
|                 |     |                 |     |                 |
|      . . .      |     |    (( (🚶) ))    |     |      . . .      |
|                 |     |                 |     |                 |
|    🔉 (中等)    |     |    🔊 (大声)    |     |    🔉 (轻柔)     |
+-----------------+     +-----------------+     +-----------------+
      音频节点A             音频节点B             音频节点C
```

正是这种连续、动态的调整，才使 OpenWave 成为一种真正沉浸式的体验。

## ✨ 主要特性

* **🚶‍♂️ 以用户为中心的动态播放**：音乐跟随着用户的脚步，自动在全屋的音响系统中流转。
* **🎶 无缝平滑的音频过渡**：不仅仅是简单的切换，而是通过精细的音量和EQ（均衡器）动态调整，创造出声音平滑移动的“声波”效果。
* **👨‍👩‍👧‍👦 多用户支持 (规划中)**：为家庭中的每个成员创建独立的、互不干扰的个人音乐波。
* **🔌 高度可扩展性**：以 [Home Assistant](https.home-assistant.io/) 为核心，天然兼容其生态下的数千种传感器和智能设备。
* **🔊 灵活的音频输出**：主要为高保真、低延迟的有线系统（如 **Dante**）设计，以实现极致的无缝体验。同时也兼容主流的无线协议（如 Sonos, Chromecast），以提供更广泛的可用性。

## 🔧 工作原理

OpenWave 的核心是一个决策引擎，它作为智能家居平台（如 Home Assistant）的一部分运行。下图展示了其数据流：

```
                               +--------------------------+
[各类传感器] ----------------> |   智能家居平台 (H.A.)   |
(毫米波雷达, Wi-Fi, UWB等)      +--------------------------+
                                           |
                                           | (用户位置、设备状态)
                                           |
                               +--------------------------+
                               |   OpenWave 核心引擎     |
                               +--------------------------+
                                           |
                                           | (播放、暂停、音量、EQ指令)
                                           |
+-----------------+           +-----------------+           +-----------------+
| 音频节点A (客厅)  | <---------+ 音频节点B (走廊)  | <---------+ 音频节点C (书房)  |
+-----------------+           +-----------------+           +-----------------+
```

1. **感知 (Perception)**: Home Assistant 从全屋的传感器（如毫米波存在传感器、Wi-Fi设备追踪、未来或支持UWB）收集原始数据。
2. **决策 (Decision)**: OpenWave 引擎分析这些数据，精准判断一个或多个用户的位置，并根据预设的音频策略，计算出各个音频节点（音响）应有的状态。
3. **执行 (Execution)**: 引擎通过 Home Assistant 向各个音频节点发送指令，控制其播放、暂停、以及实时调整音量和EQ，从而实现声音的平滑流动。

## 🗺️ 项目路线图

我们正处于项目的黎明阶段，欢迎每一位志同道合的朋友加入我们，共同实现这个激动人心的目标。

* **Phase 1: v0.1 (基础框架)**
  * [x] 项目概念与架构设计
  * [ ] 实现与 Home Assistant 的基础集成
  * [ ] 支持单用户、基于**房间级别**的粗略切换
  * [ ] 支持首批音频协议 (如: Sonos, Chromecast)
  * [ ] 发布首个 HACS (Home Assistant Community Store) 可安装版本

* **Phase 2: v0.5 (声波效果)**
  * [ ] 引入相邻音响间的音量交叉淡化（Crossfade）算法
  * [ ] 实现基础的“声波”平滑移动效果
  * [ ] 支持更精准的室内定位传感器

* **Phase 3: v1.0 (多用户时代)**
  * [ ] 探索并实现多用户的识别与追踪
  * [ ] 实现多个独立音乐波的隔离播放
  * [ ] 研究用户靠近时的声场智能混合模式

* **未来展望**
  * [ ] 官方 `OpenWave Hub` 硬件的可能性
  * [ ] 对 Dante 等专业音频协议的深度支持
  * [ ] 引入 AI 预测用户移动轨迹，实现“零延迟”切换

## 🚀 快速开始

详细的安装和配置指南正在撰写中，将发布在 `docs` 目录下。

我们计划通过 [HACS](https://hacs.xyz/) 进行分发。基本要求：
1. 一个正在运行的 Home Assistant 实例。
2. 家中部署了至少一个（推荐多个）受支持的传感器（如 Aqara FP1/FP2 毫米波雷达）。
3. 拥有至少两个受支持的智能音响。

## 🙌 如何贡献

我们欢迎来自任何背景的朋友为 OpenWave 贡献力量！无论是代码、文档、测试、还是一个全新的想法，对我们都至关重要。

1. **Fork** 本仓库。
2. 创建一个新的功能分支 (`git checkout -b feature/AmazingFeature`)。
3. 提交您的更改 (`git commit -m 'Add some AmazingFeature'`)。
4. 将分支推送到您的仓库 (`git push origin feature/AmazingFeature`)。
5. **提交一个 Pull Request**。

请在提交前阅读我们的 `CONTRIBUTING.md` (待创建) 文件以获取更详细的指南。您也可以在 [GitHub Issues](https://github.com/YOUR_USERNAME/openwave/issues) 中报告Bug或提出功能建议。

## 💬 加入我们

一个伟大的项目离不开一个充满活力的社区。

* **💬 来 [GitHub Discussions](https://github.com/YOUR_USERNAME/openwave/discussions) 聊聊您的想法**：这里是进行功能讨论、分享您的使用案例和提出问题的最佳场所。
* **🗣️ 加入我们的 [Discord](https://discord.gg/YOUR_INVITE_LINK) 频道**：进行更即时的交流和协作。

## 📄 许可证

本项目采用 [Apache 2.0](https://opensource.org/licenses/Apache-2.0) 许可证。详情请见 `LICENSE` 文件。

## 🙏 致谢

* 感谢 **Home Assistant** 团队和社区，为我们提供了如此强大和开放的平台。
* 感谢所有为开源世界无私奉献的开发者们。
