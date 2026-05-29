# Dataset Health Report

## Overview

The quality of a perception system is heavily influenced by the quality of its training dataset.

This project incorporates an automated dataset auditing pipeline to continuously monitor dataset quality, class balance, semantic coverage, and annotation distribution.

The objective is to identify dataset weaknesses before model training and ensure robust generalization across environments.

---

# Why Dataset Health Matters

Poor datasets often result in:

* Class imbalance
* Biased predictions
* Poor rare-class performance
* Overfitting
* Unstable deployment behavior

Dataset health monitoring helps identify these issues early in the development cycle.

---

# Dataset Auditing Pipeline

```text
Images + Labels
        ↓
Dataset Auditor
        ↓
Class Statistics
        ↓
Pixel Distribution Analysis
        ↓
Rare Class Detection
        ↓
Health Metrics
        ↓
Training Readiness Assessment
```

---

# Health Metrics

The dataset auditor evaluates multiple aspects of dataset quality.

---

## Class Frequency

Measures how often each semantic class appears in the dataset.

### Purpose

Identify:

* Missing classes
* Underrepresented classes
* Overrepresented classes

### Example

| Class   | Instances |
| ------- | --------- |
| Road    | XXXX      |
| Grass   | XXXX      |
| Pothole | XXX       |
| Fire    | XX        |
| Smoke   | XX        |

---

## Pixel Distribution

Measures the percentage of total pixels occupied by each class.

### Why It Matters

Two classes may appear equally often but occupy vastly different image areas.

Example:

```text
Road:
Large pixel coverage

Fire:
Small pixel coverage
```

Pixel distribution is often more informative than raw instance count.

---

## Image Presence Percentage

Measures the percentage of images containing a specific class.

### Formula

```text
Images containing class
-------------------------
Total images
```

### Purpose

Identify:

* Rare classes
* Dataset coverage issues
* Missing environmental scenarios

---

## Average Instance Area

Measures the average size of annotated objects.

### Purpose

Understand:

* Small-object classes
* Large-area terrain classes
* Annotation consistency

### Typical Examples

| Small Objects |
| ------------- |
| Fire          |
| Pothole       |
| Puddle        |

| Large Objects |
| ------------- |
| Road          |
| Grass         |
| Hill          |

---

# Dataset Diversity Metrics

---

## Entropy Score

Entropy measures how evenly information is distributed across classes.

### Interpretation

| Entropy Score | Dataset Diversity |
| ------------- | ----------------- |
| > 0.80        | Excellent         |
| 0.65 - 0.80   | Good              |
| < 0.65        | Imbalanced        |

Higher entropy generally indicates better class diversity.

---

## Tail Class Ratio

Measures the proportion of rare classes.

### Definition

Classes occupying less than 1% of total dataset pixels.

### Interpretation

High values indicate:

* Rare classes
* Long-tail distribution
* Increased training difficulty

---

## Dominant Class Ratio

Measures how much the largest class dominates the dataset.

### Example

```text
Road
occupies
45% of all pixels
```

Large dominance can bias training toward majority classes.

---

# Rare Class Detection

Classes are automatically flagged when:

```text
Pixel Share < Threshold
```

or

```text
Image Presence < Threshold
```

### Potential Rare Classes

* Fire
* Smoke
* Pothole
* Trench
* Slushy

Rare classes may require:

* Additional data collection
* Targeted augmentation
* Weighted loss functions

---

# Dominant Class Detection

Classes with significantly higher representation are flagged as dominant.

Typical dominant classes include:

* Road
* Grass
* Floor

Dominance is evaluated using distribution statistics and z-score analysis.

---

# Dataset Quality Flags

Each class is assigned a health status.

---

## OK

Class representation is sufficient.

### Example

```text
Road
Grass
Floor
```

---

## LOW_PIXEL

Class occupies very small pixel area.

### Impact

Poor segmentation performance.

### Recommendation

Collect additional samples.

---

## RARE_CLASS

Class appears in too few images.

### Impact

Weak generalization.

### Recommendation

Increase scenario diversity.

---

## DOMINANT

Class is heavily overrepresented.

### Impact

Training bias.

### Recommendation

Increase minority class coverage.

---

## EXTREMELY_RARE

Class is statistically underrepresented.

### Impact

Potential model collapse on that class.

### Recommendation

Dedicated data collection campaign.

---

## MISSING

No valid annotations found.

### Impact

Class cannot be learned.

### Recommendation

Review dataset construction pipeline.

---

# Class Distribution Analysis

The following visualizations should be generated during each dataset release.

---

## Instance Distribution

```text
Class
    ↓
Number of Instances
```

Purpose:

* Detect imbalance
* Identify missing labels

---

## Pixel Distribution

```text
Class
    ↓
Pixel Share %
```

Purpose:

* Detect dominant terrain classes

---

## Image Presence Distribution

```text
Class
    ↓
Image Coverage %
```

Purpose:

* Evaluate environmental diversity

---

# Dataset Release Checklist

Before training:

* Class distribution reviewed
* Pixel distribution reviewed
* Rare classes verified
* Missing classes checked
* Duplicate images removed
* Corrupted labels removed
* Stratified split generated
* Dataset entropy evaluated

---

# Dataset Versioning

## Version 1.0

Binary road segmentation.

---

## Version 2.0

Multi-class terrain segmentation.

---

## Version 3.0

19-class terrain and hazard segmentation.

---

# Future Improvements

Future dataset audits will include:

* Boundary quality scoring
* Annotation consistency scoring
* Inter-annotator agreement metrics
* Active learning sample selection
* Temporal sequence diversity analysis

---

# Conclusion

Dataset quality directly impacts perception performance.

For this reason, dataset health monitoring is treated as a first-class component of the development pipeline rather than a post-processing step.

Continuous auditing ensures that training data remains balanced, representative, and suitable for deployment in real-world robotic environments.
