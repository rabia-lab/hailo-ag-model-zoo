# Hailo Ag Model Zoo (Agriculture Model Repository)

A community-oriented repository of **deployment-ready AI models for agriculture** optimized for **Hailo edge accelerators** (e.g., Hailo-8 / Hailo-8L).  
This project aims to provide **reproducible, field-oriented model releases** (HEF + metadata + evaluation scripts) for agricultural perception and decision-support tasks.

## Scope

This repository hosts models and utilities for agricultural applications, including (but not limited to):

- **Weed detection and crop/weed discrimination** ([object detection](https://drive.google.com/drive/folders/1bjlbfw3bd9ndsVB1XkNkYGCLnLL-bBYf?usp=sharing), segmentation)
- **Crop disease and pest detection**
- **Plant phenotyping** (counting, sizing, growth stage)
- **Yield-related tasks** (fruit detection, counting)
- **Livestock monitoring** (detection, tracking)
- **Quality assessment** (e.g., produce grading, defect detection)
- **Remote sensing / UAV inference** (lightweight detectors for onboard compute)

Models are released in **Hailo Executable Format (HEF)** whenever possible, with optional ONNX/PT checkpoints for transparency and reproducibility.

---

## Repository Principles

1. **Deployment-first**: every model release must be runnable on real edge hardware.
2. **Reproducibility**: training and compilation steps must be documented.
3. **Fair evaluation**: metrics and test protocols must be clearly stated.
4. **Clear licensing**: models and code must have explicit usage terms.
5. **No dataset redistribution** unless the dataset license explicitly allows it.

---

## Current Model Packs

### 1) Crop–Weed Detection (Object Detection)
- Task: multi-class crop/weed detection (bounding boxes)
- Models: YOLOv8 / YOLOv10 / YOLOv11 variants (PT → ONNX → HEF)
- Hardware target: Raspberry Pi 5 + Hailo-8L (AI Kit)
- Metrics: Precision, Recall, F1, IoU, Dice + latency + throughput + efficiency
- Pack location: `models/crop_weed_detection/`

> This is the first contributed pack and serves as the reference template for future packs.

---

## Quick Start (Running a HEF model)

1) Install runtime dependencies (host + device requirements may differ):
```bash
pip install -r requirements.txt
