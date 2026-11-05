# Wichun.lab Study Plan · v0.1

> **Status:** planned, dated 2026-11-05. A planned topic is not a completed tutorial or verified reproduction.  
> [Knowledge Atlas](KNOWLEDGE-ATLAS.md) · [简体中文](STUDY-PLAN.zh-CN.md) · [Home](../README.md)

## Two complementary guides

- **Knowledge Atlas:** what problems must a robot solve as a complete physical and intelligent system?
- **Study Plan:** what will we learn first, how deeply, and what can we share after doing the work?

The atlas follows the robot from hardware to learning and action. **Study order follows research experience first**, not a strict bottom-to-top sequence.

## Principles and pace

- Long-term aim: broad understanding, selective depth and increasingly tested implementations.
- About **20+ hours per week**, with an initial target of 50% foundational study, 30% paper reading, 20% hands-on work.
- Explore the real problem before specific model names. Introduce shared mathematics and machine learning prerequisites at the point where they become relevant.
- A topic progresses through **clear explanation → technical understanding → experimental verification when appropriate**.
- Share source-backed tutorials and concise bilingual outreach only after checking claims. Do not mark proposed experiments as reproduced.
- A **12-month first cycle** is a planning guide, not a promise or fixed weekly quota.

## The 12 core topics

| Phase | ID | Topic | Main question | Illustrative output |
| --- | --- | --- | --- | --- |
| Months 1–3 | 01 | Robot Kinematics & Dynamics | How does joint motion or torque affect robot motion? | 2-link model, Jacobians, dynamics explanations and tested demo |
| | 02 | Motion Planning & Control | How are feasible motions planned and executed robustly? | LQR/MPC/feedback explanations, documented comparison |
| | 03 | Reinforcement Learning for Locomotion | How can robots learn movement by interacting? | MDP, PPO, GAE, quadruped training study |
| Months 4–5 | 04 | Mechanisms, Actuators & PCBs | What makes a physical robot move and sense? | Hardware breakdown, interface and design notes |
| | 05 | Embedded & Robot Software | How do sensors, compute and controllers cooperate in time? | Embedded/ROS 2 workflow, timing example |
| | 06 | Perception & State Estimation | How does a robot infer itself and the environment from sensors? | Depth/point-cloud or estimation demonstration |
| Months 6–9 | 07 | Spatial Intelligence & Multimodality | How does a robot interpret geometry and physical relations? | Spatial reasoning overview with example |
| | 08 | Manipulation & Imitation Learning | How can robots learn to grasp and manipulate objects? | Behavior cloning/DAgger/diffusion-policy study |
| | 09 | World Models | Can predicting consequences help planning and learning? | Dynamics prediction and evaluation experiment |
| | 10 | VLA & Robot Foundation Models | How do language, vision and action connect? | Architecture and action-interface analysis |
| | 11 | Agents & Long-Horizon Autonomy | How do robots plan multiple steps and recover from failure? | Task/skill orchestration example |
| Months 10–12 | 12 | Data, Simulation, Deployment & Evaluation | How are full robot systems built and validated? | Integrated project with evidence and limitations |

**Continuous throughout:** safety, evaluation, data quality, reproducibility, human–robot interaction, and sim-to-real. They are not postponed until topic 12.

## Topic completion template

1. Problem and motivation
2. Prerequisite concepts and physics/mathematics
3. Technical explanation and key equations
4. Representative original papers and their evidence
5. Code, configurations, and results **only when tested**
6. Links back to related knowledge atlas nodes
7. Chinese shareable visual summary and English research post where appropriate

Suggested topic states: **planned → studying → technically reviewed → published**. Software artifacts are separately marked verified/unverified.

## First topic: Robot Kinematics & Dynamics

Start with links, joints, and coordinate frames; derive forward kinematics, inverse kinematics, and Jacobians for a planar two-link arm; derive dynamics and external force terms; compare fixed-base arms with floating-base legged and humanoid robots; then implement a minimal reproducible demonstration.

Initial outreach question: **“Why doesn't knowing the joint angle directly tell us how the robot's end-effector moves?”**

This first cycle should evolve with experience. The goal is durable understanding and useful open resources, not filling a calendar.
