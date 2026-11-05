# Robotics & Embodied Intelligence: A Knowledge Atlas

> Wichun.lab · Knowledge Atlas v0.2 (text companion) · 2026-11-05  
> [Knowledge map (SVG)](../assets/knowledge-map-v0.1-en.svg) · [简体中文](KNOWLEDGE-ATLAS.zh-CN.md) · [Home](../README.md)

## The question behind the project

**How does a physical robot acquire the ability to sense, understand, reason, act, and learn from interaction?**

This is a map of **problems that a robot must solve**, rather than an exhaustive list of model names. It is designed to make connections visible before diving into algorithms or papers. Detailed tutorials and validated experiments will be added incrementally.

## An example: a quadruped climbing unfamiliar stairs

| Question | Needed knowledge |
| --- | --- |
| Can its body and legs produce the motion? | Mechanisms, actuators, sensors, power |
| Can it read sensors and command joints in time? | Embedded systems, communication, real-time software |
| How do joints and contacts affect motion? | Kinematics, dynamics, contact modeling |
| Where is it and what is the terrain like? | State estimation, depth/LiDAR, fusion |
| Where can it safely place its feet? | 3D geometry, spatial reasoning, terrain representations |
| Which steps and trajectory should it choose? | Decision making, motion planning, learned policies |
| How does it execute the plan reliably? | Feedback control, MPC, WBC, constraints |
| What if it slips or encounters a novel obstacle? | Feedback, recovery, adaptation, evaluation |

These are functional questions, **not a required serial software pipeline**. A learned end-to-end policy may combine several functions.

## Part I — A physical robot that actually works

### 1. Hardware and electronics

**Main question:** How does the robot generate motion, sense the world, and operate reliably?

Mechanisms, degrees of freedom, transmissions, actuators, encoders, IMUs, cameras, tactile and force sensors, PCB and power design. Bandwidth, torque, mechanical limits, accuracy, and power constraints shape what higher-level algorithms can execute.

### 2. Software and computing

**Main question:** How do sensors, control loops, and computers cooperate with reliable timing?

Embedded programming, motor drivers, scheduling and interrupts, CAN/EtherCAT, Linux, ROS 2, synchronization, inference latency and deployment. An algorithm's mathematical behavior is not enough to guarantee system-level reliability.

### 3. Modeling and physics

**Main question:** Given commands and contact forces, what motion follows?

Coordinate transforms, SE(3), forward/inverse kinematics, Jacobians, rigid-body and floating-base dynamics, friction, contact, system identification and model error. This connects mechanical hardware to control and robot learning.

## Part II — Intelligent closed-loop behavior

### 4. Sensing and state estimation

**Main question:** How does a robot infer its state from incomplete and noisy observations?

Proprioception, cameras, depth, point clouds, tactile sensing, calibration, filtering, odometry, SLAM, sensor fusion, uncertainty. Raw sensor measurements are not yet reliable state estimates.

### 5. World understanding and spatial intelligence

**Main question:** What do objects, geometry, spatial relations, and possible physical interactions mean for action?

3D perception, mapping, scene representations, semantics, multimodal grounding, occlusion, reachability, affordances, physical reasoning, temporal prediction and world models.

**Distinction:** Reconstruction estimates geometry; spatial intelligence uses spatial relationships; world models predict state evolution. World models can also support planning, control, and training.

### 6. Reasoning and decisions

**Main question:** Which subtask should the robot choose to accomplish a longer goal?

Goals, symbolic and probabilistic decision making, task planning, natural language grounding, memory, skill invocation, agents, long-horizon execution and recovery.

### 7. Planning and action generation

**Main question:** How is a task converted into executable action?

Path and motion planning, trajectory optimization, foothold planning, manipulation planning, reinforcement learning, imitation learning, diffusion-based policies, VLA policies, feasibility and collision constraints. Different systems may produce trajectories, action chunks, or direct commands.

### 8. Control and physical execution

**Main question:** How are motions executed despite disturbances, delays, and changing contacts?

PID, feedback, LQR, nonlinear and optimal control, MPC, WBC, impedance and force control, safety constraints, hardware interfaces and real-time control. A high-level action proposal does not automatically ensure robust execution.

## Part III — Learning, validation, and engineering

### 9. Learning and adaptation

Learning from demonstrations, reward, offline data, predictive representations, distillation, online adaptation and continual learning. These are methods that can span several functions, not necessarily distinct real-time modules.

### 10. Data, simulation, training, and deployment

Data collection/quality, robot simulators, reproducibility, training infrastructure, domain randomization, sim-to-real, delays and deployment. Frameworks to investigate include MuJoCo, Isaac Lab, ROS 2 and LeRobot.

### 11. Evaluation, safety, and human interaction

Benchmarks, baselines, ablations, random seeds, out-of-distribution testing, failure analysis, safe operation, human–robot interaction and long-term reliability. A demonstration alone is not a generalization result.

## Three main robot platforms

| | Manipulators | Quadrupeds | Humanoids |
| --- | --- | --- | --- |
| Physical challenge | Contact, grasping | Terrain, switching supports | Floating-base dynamics, balance |
| Perception | Object pose, vision, touch | Terrain, proprioception, contacts | Whole-body state and scene |
| Motion | Grasp and impedance | Locomotion and footholds | Whole-body coordination |
| Learning | Demonstrations, VLA | RL, perceptive control | Imitation, full-body learning |

Other robot families will be introduced when relevant.

## How to navigate the knowledge

1. Understand each block's purpose and connections.
2. Start in depth with robot modeling, control, and learning.
3. Expand to perception, spatial intelligence, world models, VLA, and agents.
4. Use experiments, source papers, and reproducibility to test conclusions.

A topic may progress from **clear explanation → mathematical/algorithmic understanding → experimental verification**.

Core foundations such as optimization, probability, linear algebra, transformers, and sequence learning are introduced at the point where they become relevant, with cross-links rather than repeating a general AI textbook.

## Starting resources (official)

These are references for further study, **not claims of completed study or reproductions**:

- [Modern Robotics — Northwestern University](https://modernrobotics.northwestern.edu/)
- [Underactuated Robotics — MIT](https://underactuated.csail.mit.edu/)
- [ROS 2 documentation](https://docs.ros.org/en/rolling/)
- [Isaac Lab documentation](https://docs.nvidia.com/isaaclab/isaac-lab)
- [LeRobot documentation](https://huggingface.co/docs/lerobot)

Future nodes will add **questions, prerequisites, explanations, references, code, experiments, and related topics**, with clear status labels.
