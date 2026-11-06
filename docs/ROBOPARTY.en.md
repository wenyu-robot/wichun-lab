# RoboParty Source Guide and Research Starting Point

> First-edition scope · 2026-11-06 · [简体中文](ROBOPARTY.md) · [Home](../README.md) · [Knowledge Atlas](KNOWLEDGE-ATLAS.md)

## Research goal

Use RoboParty humanoids to investigate how hardware, software, modeling, control, perception and learning produce autonomous behavior. This guide indexes official sources and their overview descriptions. **Subsystem files have not yet been audited in detail, executed or verified on hardware.**

RP1 is the starting point for source mapping; RPO provides prototype context; Party_OS links capability research and its roadmap. The first experiment's actual robot, DoF configuration and versions remain to be selected after checking support. They are not assumed interchangeable.

## Official entries

| Entry | Purpose | Check before use |
| --- | --- | --- |
| [RP1](https://github.com/Roboparty/RP1) | Hardware, firmware, models, deployment and learning overview | Actual files, configurations and release versions |
| [ROBOTO_ORIGIN / RPO](https://github.com/Roboparty/roboto_origin) | Prototype platform and development material | Differences from RP1 hardware, models and interfaces |
| [Party_OS](https://github.com/Roboparty/Party_OS) | Data, retargeting, learning, perception and interaction roadmap | Released work, future plans and robot support |

## Map system questions to sources

The mapping below follows the [RP1 overview](https://github.com/Roboparty/RP1) and [Party_OS index](https://github.com/Roboparty/Party_OS) as read on 2026-11-06. These are reading leads, not compatibility or reproduction results.

| System question | Official source | What to inspect next |
| --- | --- | --- |
| How is the body designed and assembled? | [rp1_hardware](https://github.com/Roboparty/rp1_hardware) | Mechanical source, electronics, BOM, assembly and test versions |
| How are joints driven and measured? | [ROMOMO](https://github.com/Roboparty/ROMOMO) | Actuators, firmware, protocol and host tools |
| How does low-level software connect devices? | [RP1_firmware](https://github.com/Roboparty/RP1_firmware) | BSP, USB-CAN, low-level SDK and timing |
| How is the whole robot represented? | [RP1_description](https://github.com/Roboparty/RP1_description) | URDF/MJCF, meshes, joint order, frames, inertia and configuration |
| How do states and commands flow? | [roboparty_deploy](https://github.com/Roboparty/roboparty_deploy) | IMU, motor, inference and camera interfaces; supported robots |
| How are motion policies trained and transferred? | [roboparty_train](https://github.com/Roboparty/roboparty_train), [MimicLite](https://github.com/Roboparty/MimicLite) | Environments, tasks, observations, actions, rewards, data and deployment |
| How are human motions mapped to the robot? | [human-humanoid-tools](https://github.com/Roboparty/human-humanoid-tools) | Skeletons, joint mappings, constraints, formats and target robot |
| How are reusable and perception-aware behaviors learned? | [UFO](https://github.com/Roboparty/UFO), [P-BFM](https://github.com/Roboparty/P-BFM) | Training assumptions, observations, metrics and actual RP1 support |
| How can interaction and prediction be studied? | [I-BFM-Code](https://github.com/Roboparty/I-BFM-Code), [INTACT-JEPA](https://github.com/Roboparty/INTACT-JEPA) | Methods, models, transfer requirements and release boundaries |

**Upstream boundaries:** the RP1 overview currently describes roboparty_train as an RPO locomotion training workspace, and marks RP1 support for I-BFM, PredActor and INTACT-JEPA as coming soon. Party_OS marks data generation as not yet released. A link in the RP1 overview therefore does not establish that a module runs directly on RP1. Check each sub-repository at a specific commit.

## First planned output: humanoid system anatomy

Status: **planned**. Follow one joint before expanding to the whole body:

1. Locate mechanical files and joint models; explain axes, transmission and motion limits.
2. Trace one state read and one command through electronics, firmware and communication.
3. Check actuator IDs, model order, units, zero positions and frame conventions.
4. Follow observations into a policy and policy outputs into actuator commands.
5. Run a minimal check in a matching model and simulator; record configuration, commands and observations.

Each step should cite upstream paths and commits, explain the mechanism, and record open questions and verification status. Runtime conclusions require actual execution.

## Evaluate capabilities incrementally

| Stage | Candidate capability | Example evidence |
| --- | --- | --- |
| Models and interfaces | Single-joint motion, model loading, state/command flow | Consistent axes, ordering, units and feedback |
| Motion skills | Standing, walking, turning, motion tracking | Tracking error, falls, disturbances and energy |
| Perception-driven behavior | Adapt motion to terrain or objects | Success under environmental changes, collisions and failures |
| Autonomous tasks | Select skills from goals, check outcomes and recover | Task success, interventions and recovery success |

These are research stages, with no completed experiments yet. Language, VLA, world models and agents are introduced when a task needs them. Upstream availability, robot compatibility and verification in this project are separate questions.

## Version and reproduction record

Before starting the first experiment, record:

- Platform, hardware revision, DoF, joint modules, sensors and computing configuration.
- URL, commit/tag, model file and configuration path for each upstream repository.
- Operating system, drivers, simulator and training framework versions.
- Data and policy sources, versions, access conditions and licenses.
- Commands, seeds, metrics, logs, failure cases and limitations.
- Verification level: reading / source analysis / simulation / physical robot.

An upstream demo, a local run, cross-environment reproduction and hardware validation provide different evidence. Preserve upstream attribution and applicable licenses. This project is independently maintained.

## Change log

- **2026-11-06:** Focus the first edition on RoboParty humanoids; add source mapping and verification boundaries; update the atlas to v0.3 and maps to v0.2.
