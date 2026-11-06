# Labs / 实验与复现

[Home](../README.md) · [中文首页](../README.zh-CN.md) · [RoboParty 导航](../docs/ROBOPARTY.md) · [Source guide](../docs/ROBOPARTY.en.md)

第一版聚焦 RoboParty 人形机器人。先核实具体机型、自由度、上游版本与环境，再进行模型/接口检查和运动基线实验。RPO 与 RP1、不同模型配置及策略不默认兼容。

The first edition focuses on RoboParty humanoids. Check the exact robot, DoF, upstream versions and environment before model/interface checks and a motion baseline. RPO, RP1, model configurations and policies are not assumed interchangeable.

每个实验包含 / Each experiment records:
1. 问题、预期与验证层级 / Question, expected behavior and verification level
2. 硬件配置、模型、代码、数据和策略的来源与版本 / Hardware, model, code, data and policy provenance and versions
3. 环境依赖、命令与配置 / Dependencies, commands and configurations
4. 随机种子、指标、对比和评测条件 / Seeds, metrics, comparisons and evaluation conditions
5. 日志、结果、失败与局限 / Logs, results, failures and limitations
6. 相关笔记、论文、署名与许可 / Notes, papers, attribution and licenses

运动技能、感知驱动行为与自主任务分别评测。区分仿真运行、跨环境复现和实机验证。

Evaluate motion skills, perception-driven behavior and autonomous tasks separately. Distinguish simulation runs, cross-environment reproduction and hardware validation.

**Status / 状态：** planned / 计划中。No experiments are claimed as reproduced yet. 首个实验的具体平台与版本尚未锁定。
