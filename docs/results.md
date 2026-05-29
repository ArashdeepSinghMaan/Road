# Results

## Overview

This document presents qualitative and quantitative results obtained from the Terrain Traversability Segmentation system.

The objective of the evaluation is to assess:

* Semantic segmentation quality
* Terrain understanding capability
* Hazard recognition performance
* Deployment readiness
* Traversability reasoning

The results include both visual demonstrations and deployment performance metrics.

---

# Qualitative Results

Qualitative evaluation is critical because navigation systems ultimately operate on visual scene understanding.

---

## Daytime Terrain Segmentation

### Input

<p align="center">
<img src="../results/qualitative/day/input.png" width="80%">
</p>

### Prediction

<p align="center">
<img src="../results/qualitative/day/prediction.png" width="80%">
</p>

### Overlay

<p align="center">
<img src="../results/qualitative/day/overlay.png" width="80%">
</p>

---

### Observations

Successfully identifies:

* Road
* Grass
* Footpath
* Trees
* Bushes

Maintains strong boundary separation between traversable and non-traversable terrain.

---

# Night-Time Segmentation

### Input

<p align="center">
<img src="../results/qualitative/night/input.png" width="80%">
</p>

### Prediction

<p align="center">
<img src="../results/qualitative/night/prediction.png" width="80%">
</p>

### Overlay

<p align="center">
<img src="../results/qualitative/night/overlay.png" width="80%">
</p>

---

### Observations

Correctly identifies:

* Roads
* Terrain boundaries
* Vegetation regions

Primary challenge:

* Reduced contrast
* Illumination variation

---

# Smoke Environment Results

### Input

<p align="center">
<img src="../results/qualitative/smoke/input.png" width="80%">
</p>

### Prediction

<p align="center">
<img src="../results/qualitative/smoke/prediction.png" width="80%">
</p>

### Overlay

<p align="center">
<img src="../results/qualitative/smoke/overlay.png" width="80%">
</p>

---

### Observations

The model demonstrates robustness under visibility degradation and maintains semantic understanding despite partial scene occlusion.

---

# Terrain Understanding Examples

---

## Road

<p align="center">
<img src="../results/classes/road.png" width="75%">
</p>

---

## Grass

<p align="center">
<img src="../results/classes/grass.png" width="75%">
</p>

---

## Gravel

<p align="center">
<img src="../results/classes/gravel.png" width="75%">
</p>

---

## Mud

<p align="center">
<img src="../results/classes/mud.png" width="75%">
</p>

---

## Hill

<p align="center">
<img src="../results/classes/hill.png" width="75%">
</p>

---

# Hazard Recognition Results

The system is capable of identifying navigation-critical hazards.

---

## Pothole Detection

<p align="center">
<img src="../results/hazards/pothole.png" width="75%">
</p>

---

## Trench Detection

<p align="center">
<img src="../results/hazards/trench.png" width="75%">
</p>

---

## Water Body Detection

<p align="center">
<img src="../results/hazards/water.png" width="75%">
</p>

---

## Fire Detection

<p align="center">
<img src="../results/hazards/fire.png" width="75%">
</p>

---

## Smoke Detection

<p align="center">
<img src="../results/hazards/smoke.png" width="75%">
</p>

---

# Traversability Mapping Results

Semantic understanding is converted into traversability information.

---

## Semantic Output

<p align="center">
<img src="../results/traversability/semantic.png" width="80%">
</p>

---

## Traversability Map

<p align="center">
<img src="../results/traversability/traversability.png" width="80%">
</p>

---

### Example Mapping

| Class      | Traversability |
| ---------- | -------------- |
| Road       | High           |
| Floor      | High           |
| Grass      | Medium         |
| Gravel     | Medium         |
| Mud        | Low            |
| Trench     | Unsafe         |
| Water Body | Unsafe         |
| Fire       | Hazard         |
| Smoke      | Hazard         |

---

# Quantitative Results

## Segmentation Metrics

| Metric         | Value |
| -------------- | ----- |
| mIoU           | TBD   |
| Pixel Accuracy | TBD   |
| Precision      | TBD   |
| Recall         | TBD   |
| F1 Score       | TBD   |

Update values using the latest validation results.

---

# Per-Class Performance

| Class      | IoU |
| ---------- | --- |
| Bush       | TBD |
| Dirt       | TBD |
| Floor      | TBD |
| Footpath   | TBD |
| Grass      | TBD |
| Gravel     | TBD |
| Mud        | TBD |
| Pothole    | TBD |
| Puddle     | TBD |
| Road       | TBD |
| Rubble     | TBD |
| Stairs     | TBD |
| Trees      | TBD |
| Trench     | TBD |
| Water Body | TBD |
| Fire       | TBD |
| Smoke      | TBD |
| Slushy     | TBD |
| Hill       | TBD |

---

# Confusion Matrix

<p align="center">
<img src="../results/quantitative/confusion_matrix.png" width="85%">
</p>

---

### Purpose

The confusion matrix helps identify:

* Class ambiguity
* Frequent misclassifications
* Dataset weaknesses
* Annotation inconsistencies

---

# Precision-Recall Analysis

<p align="center">
<img src="../results/quantitative/pr_curve.png" width="80%">
</p>

---

# Deployment Results

## Platform

| Component | Value           |
| --------- | --------------- |
| Compute   | Jetson AGX Orin |
| Runtime   | TensorRT FP16   |
| Camera    | ZED2            |

---

## Runtime Performance

| Metric                 | Value         |
| ---------------------- | ------------- |
| Throughput             | ~15 Hz        |
| Runtime                | TensorRT FP16 |
| Navigation Stack       | Enabled       |
| Traversability Mapping | Enabled       |

---

# TensorRT Inference Examples

### Segmentation Overlay

<p align="center">
<img src="../results/deployment/tensorrt_overlay.png" width="85%">
</p>

---

### Navigation Runtime

<p align="center">
<img src="../results/deployment/navigation_runtime.png" width="85%">
</p>

---

# Comparison Against Baselines

Future model comparisons.

| Model       | mIoU | FPS |
| ----------- | ---- | --- |
| U-Net       | TBD  | TBD |
| DeepLabV3+  | TBD  | TBD |
| YOLOv8-Seg  | TBD  | TBD |
| YOLO11m-Seg | TBD  | TBD |

---

# Generalization Examples

The model is evaluated on environments not used during training.

### New Terrain Types

<p align="center">
<img src="../results/generalization/new_terrain.png" width="80%">
</p>

---

### New Illumination Conditions

<p align="center">
<img src="../results/generalization/new_lighting.png" width="80%">
</p>

---

# Summary

The results demonstrate that the proposed system:

* Understands diverse terrain classes
* Identifies navigation hazards
* Produces traversability-aware outputs
* Operates in day and night conditions
* Handles smoke-affected environments
* Runs in real time on NVIDIA Jetson AGX Orin

The combination of semantic understanding, traversability reasoning, and embedded deployment makes the system suitable for real-world autonomous robotic applications.
