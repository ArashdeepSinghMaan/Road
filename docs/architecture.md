# System Architecture

## Overview

This document describes the overall architecture of the Terrain Traversability Segmentation System.

The system is designed to provide real-time semantic understanding of the environment and convert visual perception into navigation-relevant terrain information.

The architecture emphasizes:

* Real-time performance
* Modular design
* Edge deployment
* Navigation integration
* Scalability

---

# High-Level System Architecture

```text
                ZED2 Stereo Camera
                        │
                        ▼
                Image Acquisition
                        │
                        ▼
                 Preprocessing
                        │
                        ▼
                 YOLO11m-Seg
                        │
                        ▼
             Semantic Segmentation
                        │
                        ▼
             Traversability Mapping
                        │
                        ▼
            Terrain Mapping Module
                        │
                        ▼
                Navigation Stack
```

---

# System Components

The complete perception pipeline consists of six primary components.

---

## 1. Data Acquisition Layer

Responsible for collecting visual information from the environment.

### Sensor

```text
ZED2 Stereo Camera
```

### Responsibilities

* RGB image acquisition
* Scene observation
* Environment monitoring
* Real-time frame streaming

---

# 2. Preprocessing Layer

Prepares images for inference.

### Responsibilities

* Image resizing
* Normalization
* Format conversion
* Tensor preparation

---

### Input

```text
Raw RGB Image
```

### Output

```text
Model Input Tensor
```

---

# 3. Semantic Segmentation Layer

Core perception component.

### Model

```text
YOLO11m-Seg
```

### Responsibilities

* Semantic classification
* Pixel-level prediction
* Hazard detection
* Terrain identification

---

## Output Classes

```text
Bush
Dirt
Floor
Footpath
Grass
Gravel
Mud
Pothole
Puddle
Road
Rubble
Stairs
Trees
Trench
Water Body
Fire
Smoke
Slushy
Hill
```

---

# 4. Traversability Mapping Layer

Transforms semantic information into navigation-relevant information.

Semantic classes alone do not indicate whether a robot can safely traverse an area.

Traversability mapping bridges perception and navigation.

---

## Traversability Categories

### Safe

```text
Road
Floor
```

---

### Conditional

```text
Grass
Gravel
Dirt
Footpath
Hill
Slushy
```

---

### Hazardous

```text
Mud
Pothole
Puddle
Rubble
Trench
```

---

### Unsafe

```text
Water Body
Bush
Trees
Stairs
```

---

### Environmental Hazard

```text
Fire
Smoke
```

---

# Traversability Workflow

```text
Semantic Mask
       │
       ▼
Class Mapping
       │
       ▼
Traversability Score
       │
       ▼
Terrain Cost Layer
```

---

# 5. Terrain Mapping Module (TMM)

The Terrain Mapping Module acts as the interface between perception and navigation.

---

## Responsibilities

* Terrain aggregation
* Traversability storage
* Occupancy generation
* Navigation support

---

## Input

```text
Traversability Layer
```

---

## Output

```text
Terrain Representation
```

---

# 6. Navigation Layer

Consumes terrain information for planning.

---

## Responsibilities

* Path planning
* Obstacle avoidance
* Risk-aware navigation
* Terrain-aware decision making

---

# Software Architecture

```text
Camera Interface
        │
        ▼
Inference Engine
        │
        ▼
Segmentation Module
        │
        ▼
Traversability Module
        │
        ▼
Terrain Mapping Module
        │
        ▼
Navigation Interface
```

---

# Training Architecture

The training pipeline is separated from deployment.

```text
Dataset
    │
    ▼
Annotation
    │
    ▼
Dataset Audit
    │
    ▼
Dataset Split
    │
    ▼
YOLO11m-Seg Training
    │
    ▼
Validation
    │
    ▼
Benchmarking
```

---

# Dataset Pipeline

```text
Data Collection
        │
        ▼
Annotation
        │
        ▼
Quality Review
        │
        ▼
Dataset Health Audit
        │
        ▼
Version Release
```

---

# Deployment Architecture

The deployed system uses TensorRT optimization.

```text
PyTorch (.pt)
      │
      ▼
ONNX Export
      │
      ▼
TensorRT Engine
      │
      ▼
Jetson AGX Orin
      │
      ▼
Real-Time Inference
```

---

# Runtime Data Flow

## Step 1

Image captured by ZED2 camera.

---

## Step 2

Frame preprocessed and resized.

---

## Step 3

YOLO11m-Seg performs semantic segmentation.

---

## Step 4

Segmentation mask generated.

---

## Step 5

Semantic classes converted into traversability categories.

---

## Step 6

Traversability information sent to Terrain Mapping Module.

---

## Step 7

Navigation stack consumes terrain information.

---

# Performance-Oriented Design Decisions

---

## Why YOLO11m-Seg?

Provides:

* Real-time inference
* High segmentation quality
* Efficient deployment
* TensorRT compatibility

---

## Why TensorRT?

Provides:

* Lower latency
* Better GPU utilization
* Reduced memory footprint

---

## Why AGX Orin?

Provides sufficient compute for:

* Real-time segmentation
* Terrain reasoning
* Navigation integration

---

# System Constraints

Current limitations include:

* Single-camera perception
* RGB-only understanding
* Sensitivity to severe domain shifts
* Reduced visibility under extreme smoke conditions

---

# Scalability

The architecture is intentionally modular.

Future components can be added without redesigning the system.

Potential extensions:

```text
Multi-Camera Support
LiDAR Fusion
Depth-Aware Traversability
Temporal Fusion
ROS2 Integration
Uncertainty Estimation
```

---

# Design Principles

The system was developed using the following principles:

### Modularity

Each component can be upgraded independently.

---

### Real-Time Operation

Designed for embedded deployment.

---

### Deployability

All development decisions consider deployment constraints.

---

### Reproducibility

Training and deployment pipelines are version-controlled.

---

### Navigation-Centric Perception

Perception outputs are designed to directly support navigation.

---

# Summary

The Terrain Traversability Segmentation System transforms raw camera imagery into navigation-relevant terrain understanding.

The architecture combines:

* Dataset Engineering
* Semantic Segmentation
* Traversability Mapping
* Embedded Deployment
* Navigation Integration

into a complete perception pipeline suitable for autonomous ground robots operating in complex real-world environments.
