# Multi-Modal Traversability Perception for Autonomous Robots

Real-time semantic terrain understanding system designed for autonomous ground robots operating across structured roads, off-road terrain, and adverse environmental conditions.

This project focuses on robust drivable-area perception under deployment constraints, combining semantic segmentation, edge inference optimisation, and terrain-aware navigation support.

---

# Overview

This project evolved from a conventional road-segmentation pipeline into a deployment-oriented perception system for autonomous robotics.

Unlike standard segmentation projects that focus only on offline accuracy metrics, this system is designed around real-world robotic constraints including:

- Real-time edge inference
- Adverse weather robustness
- Multi-terrain understanding
- Navigation-oriented perception
- Embedded GPU deployment
- Integration with downstream planning systems

The perception module provides semantic traversability information directly to local path planning and obstacle avoidance pipelines.

---

# Key Features

- Multi-class semantic terrain segmentation
- Real-time inference on NVIDIA Orin AGX
- Support for urban + off-road environments
- Robustness across:
  - Day / Night
  - Rain / Fog
  - Illumination variations
- Terrain-aware perception for:
  - Wheeled robots
  - Tracked robots
  - Quadruped robots
- TensorRT accelerated deployment
- Profiling-driven optimisation for edge AI systems

---

# Terrain Classes

The system handles 19 semantic terrain categories relevant to autonomous navigation, including:

- Road
- Grass
- Gravel
- Mud
- Vegetation
- Sidewalk
- Obstacles
- Terrain boundaries
- Traversable / non-traversable regions

> Add complete class definitions and visualization table here.

---

# System Pipeline

## 1. Dataset Engineering

- Dataset collection from diverse outdoor environments
- Annotation management using:
  - CVAT
  - Roboflow
  - Labelme
- Multi-condition data curation for weather and lighting robustness

---

## 2. Semantic Perception

- YOLOv11-Seg based semantic segmentation
- Training and evaluation on custom terrain datasets
- Real-time semantic mask generation
- Multi-class terrain understanding for autonomous navigation

---

## 3. Edge Deployment

- ONNX export + TensorRT optimisation
- Deployment on NVIDIA Orin AGX
- GPU profiling for:
  - Latency
  - Throughput
  - Memory utilisation
  - Inference stability

---

## 4. Navigation Integration

Semantic traversability outputs are integrated with:

- Local path planning
- Obstacle avoidance
- Terrain-aware navigation
- Traversability estimation pipelines

---

# Deployment-Focused Design

A major focus of this project is balancing segmentation quality with real-time robotic deployment constraints.

Key optimisation areas:

- Inference latency
- GPU utilisation
- Throughput vs accuracy tradeoff
- Edge deployment stability
- Memory footprint optimisation

## Example Benchmark

| Model | Resolution | FPS | Latency | Platform |
|------|------|------|------|------|
| YOLOv11-Seg | 1024×576 | XX FPS | XX ms | NVIDIA Orin AGX |

> Replace benchmark values with actual deployment numbers.

---

# Failure Analysis & Robustness

The project studies segmentation behaviour under challenging conditions:

- Fog-induced visibility degradation
- Low-light/night scenes
- Terrain ambiguity
- Shadow leakage
- Motion blur during robot motion
- Off-road traversability uncertainty

## Example Failure Modes

- Vegetation-road boundary confusion
- Puddle reflections
- Gravel-road ambiguity
- Terrain edge fragmentation

---

# Real-World Deployment

The system has been evaluated on real robotic platforms using onboard edge inference.

## Supported Platforms

- Wheeled UGVs
- Tracked robots
- Quadruped robots

## Deployment Environments

- Urban roads
- Construction zones
- Off-road terrain
- Mixed-terrain navigation

> Add real deployment images, videos, or GIFs here.

---

# Research Direction

This project is being extended toward:

- Semantic-geometric traversability fusion
- Uncertainty-aware perception
- Multi-modal terrain understanding
- Domain adaptation under weather shifts
- Temporal consistency for video perception
- Safety-oriented traversability estimation

---

# Tech Stack

## AI / Perception

- PyTorch
- YOLOv11-Seg
- OpenCV

## Optimisation & Deployment

- TensorRT
- ONNX
- CUDA
- NVIDIA Orin AGX

## Annotation & Dataset Tools

- CVAT
- Roboflow
- Labelme

## Robotics Integration

- ROS2
- Navigation pipelines
- Local planner integration

---

# Future Improvements

- Temporal smoothing for video segmentation
- Uncertainty estimation for safety-critical navigation
- Semantic + elevation fusion
- LiDAR-semantic fusion
- Adverse-weather domain adaptation
- Self-supervised terrain adaptation

---

# Project Positioning

This project focuses on:

> Robust traversability perception for autonomous robotic navigation under real-world deployment constraints.

rather than only:

> Offline semantic segmentation benchmark performance.

---
