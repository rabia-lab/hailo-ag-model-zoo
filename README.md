# Hailo Ag Model Zoo

**Deployment-ready edge AI models for precision agriculture**

The **Hailo Ag Model Zoo** is an open, agriculture-focused repository developed to support practical deployment of deep learning models on low-power edge AI hardware, especially Hailo accelerators such as the **Hailo-8** and **Hailo-8L**.

This initiative was created to help researchers, engineers, and agricultural technology developers move beyond model training and toward real-world deployment. The repository provides hardware-ready model artifacts, inference scripts, evaluation guidance, and documentation for agricultural perception tasks such as weed detection, crop monitoring, plant phenotyping, disease detection, and robotic field operations.

The first release of this repository is connected to our published study:

**“Enabling scalable and energy-efficient weed detection using data-driven edge AI for precision agriculture”**  
Published in *Frontiers in Agronomy*, 2026  
DOI: `10.3389/fagro.2026.1808404`

---

## Why This Repository?

Deep learning models are widely used in precision agriculture, but many models remain difficult to deploy in real field conditions because of hardware limitations, latency, power consumption, and reproducibility challenges.

The **Hailo Ag Model Zoo** aims to address this gap by providing:

- Deployment-ready **Hailo Executable Format (HEF)** models
- Practical inference scripts for edge devices
- Clear documentation of model architecture, training, export, and compilation steps
- Evaluation protocols that consider both accuracy and deployment performance
- A reusable structure for future agriculture AI model releases

The long-term goal is to support scalable, energy-efficient, and reproducible edge AI solutions for agricultural systems.

---

## Current Model Pack

### Crop–Weed Detection

The first model pack focuses on **multi-class crop and weed detection** using field imagery.

This model pack includes YOLO-based object detection models trained for agricultural crop–weed discrimination and compiled for deployment on Hailo edge accelerators.

**Task:**  
Multi-class object detection for crops and weeds

**Model families:**  
YOLOv8, YOLOv10, and YOLOv11 variants

**Deployment format:**  
PyTorch model → ONNX → Hailo Executable Format (HEF)

**Target hardware:**  
Raspberry Pi 5 + Hailo-8L AI accelerator

**Evaluation focus:**  

- Detection accuracy
- Precision, recall, and F1-score
- IoU and Dice coefficient
- mAP-based object detection metrics
- Inference latency
- Throughput
- Energy efficiency

**Model pack location:**

```bash
models/crop_weed_detection/
