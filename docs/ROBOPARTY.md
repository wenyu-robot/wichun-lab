# RoboParty 资料导航与研究起点

> 第一版范围 · 2026-11-06 · [English](ROBOPARTY.en.md) · [中文首页](../README.zh-CN.md) · [知识全景](KNOWLEDGE-ATLAS.zh-CN.md)

## 研究目标

以 RoboParty 人形机器人为载体，追踪硬件如何通过软件、模型、控制、感知与学习形成自主行为。下面整理的是官方公开入口及其概览说明，**尚未完成子仓库逐文件审查、运行或硬件验证**。

RP1 是本次资料梳理的起点；RPO 提供原型平台背景；Party_OS 提供能力研究与路线入口。首个实验的实际平台、自由度配置及版本仍待核实后确定，不预设它们可以相互替换。

## 官方入口

| 入口 | 用途 | 阅读时要确认 |
| --- | --- | --- |
| [RP1](https://github.com/Roboparty/RP1) | 硬件、固件、模型、部署和学习子项目总览 | 实际文件、机型配置和发布版本 |
| [ROBOTO_ORIGIN / RPO](https://github.com/Roboparty/roboto_origin) | 原型平台及相关开发资料 | 与 RP1 的硬件、模型和接口差异 |
| [Party_OS](https://github.com/Roboparty/Party_OS) | 数据、重定向、学习、感知和交互研究路线 | 已公开内容、未来计划和机器人支持范围 |

## 从系统问题找到源码

以下对应关系依据 [RP1 官方总览](https://github.com/Roboparty/RP1) 和 [Party_OS 官方索引](https://github.com/Roboparty/Party_OS) 于 2026-11-06 的说明整理。它们是阅读线索，不能当作兼容性或复现结论。

| 系统问题 | 官方入口 | 本项目下一步要核实什么 |
| --- | --- | --- |
| 身体如何构成，如何制造和装配？ | [rp1_hardware](https://github.com/Roboparty/rp1_hardware) | 机械源文件、电气、BOM、装配与测试资料对应的版本 |
| 关节如何驱动和反馈？ | [ROMOMO](https://github.com/Roboparty/ROMOMO) | 执行器、固件、通信协议和上位机工具 |
| 固件和计算系统如何连接设备？ | [RP1_firmware](https://github.com/Roboparty/RP1_firmware) | BSP、USB-CAN、低层 SDK 和时序 |
| 怎样描述机器人全身？ | [RP1_description](https://github.com/Roboparty/RP1_description) | URDF/MJCF、网格、关节顺序、坐标系、质量惯量及配置 |
| 状态和指令怎样贯通？ | [roboparty_deploy](https://github.com/Roboparty/roboparty_deploy) | IMU、电机、推理、相机接口与实际支持机型 |
| 怎样训练与迁移动作策略？ | [roboparty_train](https://github.com/Roboparty/roboparty_train)、[MimicLite](https://github.com/Roboparty/MimicLite) | 环境、任务、观测、动作、奖励、数据和部署依赖 |
| 人体动作怎样对应机器人？ | [human-humanoid-tools](https://github.com/Roboparty/human-humanoid-tools) | 骨架、关节映射、约束、数据格式及目标机型 |
| 怎样学习可复用行为与感知控制？ | [UFO](https://github.com/Roboparty/UFO)、[P-BFM](https://github.com/Roboparty/P-BFM) | 训练设定、观测、任务指标及 RP1 的实际支持范围 |
| 怎样研究交互与预测模型？ | [I-BFM-Code](https://github.com/Roboparty/I-BFM-Code)、[INTACT-JEPA](https://github.com/Roboparty/INTACT-JEPA) | 方法、模型、平台迁移条件与发布边界 |

**需要保留的上游边界：** 本次查阅的 RP1 总览将 roboparty_train 描述为 RPO 运动策略训练工作区；I-BFM、PredActor 和 INTACT-JEPA 标注 RP1 支持即将到来。Party_OS 的数据生成模块标注为即将开源。因此，链接出现在 RP1 总览中，并不自动说明该模块已经可以在 RP1 上直接运行。后续以对应子仓库的具体提交为准。

## 第一份计划成果：人形机器人系统解剖

状态：**计划中**。按一个关节到全身的顺序建立证据：

1. 找到结构文件与关节模型，说明关节位置、轴向、传动和运动限制。
2. 对照电气、固件和协议，追踪一次状态读取及一次控制指令。
3. 核对执行器编号、模型关节顺序、单位、零位与坐标约定。
4. 追踪观测如何送入策略，策略输出如何转成执行器指令。
5. 在匹配的模型和仿真环境中进行最小验证，记录配置、命令与现象。

每一步应给出文件路径、上游提交、解释、待解问题和验证状态。只有实际运行后才记录运行结论。

## 能力怎样逐步验证？

| 阶段 | 可研究的能力 | 证据或指标示例 |
| --- | --- | --- |
| 模型与接口 | 单关节运动、模型加载、状态与指令链路 | 轴向、顺序、单位和反馈是否一致 |
| 运动技能 | 站立、行走、转向、动作跟踪 | 跟踪误差、跌倒率、扰动条件、能耗 |
| 感知驱动行为 | 根据地形或物体调整动作 | 环境变化下的成功率、碰撞和失败原因 |
| 自主任务 | 根据目标选技能、检查结果并恢复 | 任务成功率、人工干预次数、恢复成功率 |

这些是本项目的研究阶段，尚无已完成实验。语言理解、VLA、世界模型和 Agent 根据任务需要引入；是否有上游实现、是否适配目标机型、是否经本项目验证，需要分别回答。

## 版本与复现记录

首个实验开始前，填写：

- 平台名称、硬件修订、自由度、关节模块、传感器与计算配置。
- 每个上游仓库的 URL、commit/tag、模型文件及配置路径。
- 操作系统、驱动、仿真器和训练框架版本。
- 数据与策略权重的来源、版本、获取条件及许可。
- 运行命令、随机种子、指标、日志、失败案例和已知限制。
- 验证层级：资料阅读 / 源码分析 / 仿真运行 / 实机运行。

官方已有演示、本项目成功运行、跨环境复现和实机验证是不同证据。第三方资料保留来源与许可；本项目独立维护。

## 更新记录

- **2026-11-06：** 第一版范围聚焦 RoboParty 人形机器人；增加资料导航与验证边界；知识全景更新至 v0.3，地图更新至 v0.2。
