# Annotation Guidelines

## Purpose

This document defines the annotation standards used for the Terrain Traversability Segmentation Dataset.

The primary objectives are:

* Consistent semantic labeling
* Reduced inter-annotator variance
* Improved model generalization
* Reliable traversability reasoning
* High-quality benchmark generation

All annotations should follow the definitions provided in this document.

---

# General Annotation Rules

## Polygon Quality

Annotators should:

* Follow object boundaries closely
* Avoid excessive polygon points
* Preserve object geometry
* Capture visible object extent only

Avoid:

* Over-segmentation
* Large boundary gaps
* Approximate shapes when boundaries are visible

---

## Occlusion Handling

Annotate only visible regions.

Do not infer hidden geometry.

### Correct

```text
Visible portion only
```

### Incorrect

```text
Annotate behind obstacle
```

---

## Partial Objects

Annotate partially visible objects when:

* Semantic identity is clear
* At least 20% of the object is visible

---

## Motion Blur

Annotate blurred objects only if class identity remains clear.

Otherwise exclude.

---

# Class Definitions

---

## Bush

### Definition

Dense shrubs and low vegetation.

### Include

* Bushes
* Shrubs
* Dense vegetation clusters

### Exclude

* Trees
* Grass

### Common Confusion

* Grass
* Trees

---

## Dirt

### Definition

Exposed natural soil without vegetation coverage.

### Include

* Dry soil
* Bare earth
* Compacted dirt surfaces

### Exclude

* Mud
* Gravel

### Common Confusion

* Mud
* Gravel

---

## Floor

### Definition

Indoor traversable flooring.

### Include

* Concrete floors
* Indoor tiles
* Industrial flooring

### Exclude

* Roads
* Footpaths

---

## Footpath

### Definition

Pedestrian walking surfaces.

### Include

* Sidewalks
* Walkways
* Paved pedestrian paths

### Exclude

* Roads
* Floors

---

## Grass

### Definition

Vegetation-covered terrain dominated by grass.

### Include

* Lawns
* Grass fields
* Roadside grass

### Exclude

* Bushes
* Trees

### Common Confusion

* Bush

---

## Gravel

### Definition

Terrain covered with loose stones or crushed rock.

### Include

* Gravel roads
* Crushed stone surfaces

### Exclude

* Rubble
* Dirt

### Common Confusion

* Dirt
* Rubble

---

## Mud

### Definition

Soft deformable terrain with significant moisture content.

### Include

* Wet soil
* Mud patches
* Saturated terrain

### Exclude

* Dirt
* Slushy

### Common Confusion

* Dirt
* Slushy

---

## Pothole

### Definition

Localized depression causing mobility risk.

### Include

* Road potholes
* Terrain cavities

### Exclude

* Shadows
* Trenches

### Common Confusion

* Trench
* Shadow

---

## Puddle

### Definition

Small accumulation of standing water.

### Include

* Rainwater pools
* Shallow water patches

### Exclude

* Water bodies

### Common Confusion

* Water Body

---

## Road

### Definition

Primary vehicle traversable surface.

### Include

* Asphalt roads
* Concrete roads
* Paved roads

### Exclude

* Footpaths
* Floors

---

## Rubble

### Definition

Broken debris and fragmented material.

### Include

* Construction debris
* Broken rocks
* Rubble piles

### Exclude

* Gravel

### Common Confusion

* Gravel

---

## Stairs

### Definition

Stepped structures requiring elevation change.

### Include

* Indoor stairs
* Outdoor stairs

### Exclude

* Hills
* Slopes

---

## Trees

### Definition

Large woody vegetation structures.

### Include

* Tree trunks
* Visible tree structure

### Exclude

* Bushes
* Grass

---

## Trench

### Definition

Extended excavation or cut in terrain.

### Include

* Ditches
* Excavated channels

### Exclude

* Potholes

### Common Confusion

* Pothole

---

## Water Body

### Definition

Large regions of standing or flowing water.

### Include

* Lakes
* Rivers
* Ponds

### Exclude

* Puddles

---

## Fire

### Definition

Visible flame regions.

### Include

* Open flames
* Burning regions

### Exclude

* Reflections
* Bright lights

---

## Smoke

### Definition

Visible airborne smoke causing visibility reduction.

### Include

* Dense smoke
* Partial smoke clouds

### Exclude

* Fog
* Dust

---

## Slushy

### Definition

Partially frozen or mixed snow-mud terrain.

### Include

* Slush
* Wet snow mixtures

### Exclude

* Mud

---

## Hill

### Definition

Elevated terrain with noticeable slope.

### Include

* Hillsides
* Elevated ground

### Exclude

* Stairs

---

# Annotation Review Checklist

Before approval:

* Correct class assigned
* Boundary quality verified
* No missing major objects
* No duplicate polygons
* No invalid labels
* Polygon closure verified

---

# Quality Control Process

```text
Annotator
    ↓
Self Review
    ↓
Dataset Review
    ↓
Correction Pass
    ↓
Approval
```

---

# Common Failure Modes

## Boundary Leakage

Object extends beyond actual boundary.

### Fix

Tighten polygon around object.

---

## Under-Segmentation

Multiple semantic regions merged.

### Fix

Separate into individual classes.

---

## Over-Segmentation

Single object split into multiple regions.

### Fix

Merge connected regions.

---

## Class Confusion

Examples:

* Grass ↔ Bush
* Dirt ↔ Mud
* Gravel ↔ Rubble
* Pothole ↔ Trench
* Puddle ↔ Water Body

Review these carefully.

---

# Version Control

Any modification to annotation definitions should result in a new dataset version.

This ensures experiment reproducibility and benchmark consistency.

---

# Final Principle

When uncertain:

> Prioritize semantic consistency over aggressive labeling.

Consistent annotations produce better models than perfectly detailed but inconsistent annotations.
