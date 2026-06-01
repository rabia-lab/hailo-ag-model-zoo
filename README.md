# Hailo Ag Model Zoo

[![Agriculture](https://img.shields.io/badge/Application-Precision%20Agriculture-green)]()
[![Edge AI](https://img.shields.io/badge/Edge%20AI-Hailo--8%2F8L-blue)]()
[![Model Format](https://img.shields.io/badge/Model%20Format-HEF-orange)]()
[![Status](https://img.shields.io/badge/Status-Active%20Development-lightgrey)]()

## Overview

**Hailo Ag Model Zoo** is a deployment-focused repository for agricultural AI models optimized for **Hailo edge AI accelerators**, including **Hailo-8** and **Hailo-8L**.

The goal of this repository is to support practical, reproducible, and field-oriented deployment of deep learning models in precision agriculture. Instead of only sharing trained models, this repository is designed to provide complete model packs that include compiled **Hailo Executable Format (HEF)** files, metadata, inference scripts, evaluation outputs, and documentation needed to run agricultural AI models on edge devices.

This initiative was developed as part of our broader research on scalable and energy-efficient edge AI for precision agriculture.

The first model pack in this repository is based on our published paper:

> **Enabling scalable and energy-efficient weed detection using data-driven edge AI for precision agriculture**  
> *Frontiers in Agronomy*, 2026  
> DOI: [10.3389/fagro.2026.1808404](https://www.frontiersin.org/journals/agronomy/articles/10.3389/fagro.2026.1808404/full)

The paper presents a deployment-oriented evaluation of YOLO-based weed detection models under realistic edge-AI conditions, focusing on the trade-offs among detection accuracy, inference latency, throughput, and energy efficiency.

---

## Repository Objectives

The **Hailo Ag Model Zoo** is intended to help researchers, students, and developers move agricultural computer vision models from offline training environments to real edge-AI deployment.

The repository focuses on:

- Providing deployment-ready **HEF models** for Hailo accelerators
- Supporting reproducible inference on edge devices
- Sharing metadata and documentation for each model pack
- Reporting both model accuracy and deployment performance
- Encouraging reusable model releases for agricultural robotics and precision agriculture
- Reducing the gap between AI model development and field implementation

---

## Current Model Pack

### Crop–Weed Detection Model Pack

The first release focuses on **multi-class crop and weed detection** using YOLO-based object detection models.

This model pack includes models trained for crop–weed discrimination and compiled for Hailo-based edge deployment.

| Item | Description |
|---|---|
| Task | Multi-class crop and weed detection |
| Model type | Object detection |
| Model families | YOLOv8, YOLOv10, YOLOv11 |
| Original format | PyTorch `.pt` |
| Intermediate format | ONNX |
| Deployment format | Hailo Executable Format `.hef` |
| Target hardware | Raspberry Pi 5 + Hailo-8L AI Kit |
| Application | Edge AI weed detection for precision agriculture |

### Model Files

The current crop–weed detection model files can be accessed here:

[Crop–Weed Detection Models](https://ndusbpos-my.sharepoint.com/:f:/g/personal/ahmed_rabia_ndus_edu/IgDKLpzTpid6SKVExzjNa_4pAa6T31DqfG9JrRDw6uaKQdU?e=7Cycro)

> Note: Large model files are hosted externally to keep this GitHub repository lightweight. Please download the required HEF model files before running inference.


## Example Results

The following figures show example deployment results from the current crop–weed detection model pack.

### Inference Speedup

The figure below compares the inference speedup obtained when running the compiled Hailo Executable Format `.hef` models compared with the original PyTorch `.pt` models.

![Inference speedup between PyTorch and HEF models](https://github.com/rabia-lab/hailo-ag-model-zoo/blob/main/Figure10.png)

### Bootstrap F1-score Comparison

This figure compares the mean F1-score with 95% confidence intervals for the original PyTorch `.pt` models and the compiled Hailo `.hef` models.

![Bootstrap F1-score comparison between PT and HEF models](https://github.com/rabia-lab/hailo-ag-model-zoo/blob/main/Figure3.png)

### Class-wise Detection Performance

This figure shows the average class-wise AP@0.5 performance for PyTorch and HEF models, along with the observed HEF-induced performance change for each crop and weed class.

![Class-wise AP performance and HEF-induced degradation](https://github.com/rabia-lab/hailo-ag-model-zoo/blob/main/Figure8.png)

## Analysis of HEF Conversion Effects

![](https://github.com/rabia-lab/hailo-ag-model-zoo/blob/main/Figure6.png)

### Detection Examples

The figure below shows representative crop–weed detection outputs from selected HEF models compared with the ground-truth annotations.

![Ground-truth and HEF model prediction examples](https://github.com/rabia-lab/hailo-ag-model-zoo/blob/main/Figure16.png)

---

## Supported Applications

Although the first model pack focuses on crop–weed detection, this repository is designed to support additional agricultural AI tasks in future releases, including:

- Weed detection and crop–weed discrimination
- Crop disease and pest detection
- Plant phenotyping
- Fruit detection and counting
- Yield-related visual analytics
- Produce quality assessment
- Livestock monitoring
- UAV and remote sensing inference
- Robotic perception for field operations

---

## Repository Principles

This repository follows several core principles:

1. **Deployment-first model release**  
   Models should be prepared for real edge-AI deployment, not only offline evaluation.

2. **Reproducibility**  
   Each model pack should include enough information to reproduce the training, export, compilation, and inference workflow.

3. **Transparent evaluation**  
   Model performance should be reported using both accuracy-based metrics and deployment-oriented metrics.

4. **Hardware-aware benchmarking**  
   Edge-AI performance should include latency, throughput, and energy-efficiency considerations whenever possible.

5. **Responsible data sharing**  
   Datasets are not redistributed unless the original license allows redistribution. When datasets cannot be shared, links and preparation instructions should be provided.

---

## Requirements

The repository is designed for Hailo-based edge-AI deployment. Requirements may vary depending on the device, operating system, and Hailo software version.

### Hardware Requirements

Recommended hardware:

- Raspberry Pi 5
- Hailo-8L AI Kit or compatible Hailo accelerator
- MicroSD card or SSD with sufficient storage
- Camera, image folder, or video input source
- Stable power supply for Raspberry Pi and Hailo hardware

### Software Requirements

Recommended software environment:

- Python 3.x
- OpenCV
- GStreamer
- HailoRT
- Hailo Python bindings
- Hailo application examples / `hailo_apps` package
- NumPy
- Required packages listed in `requirements.txt`

Install Python dependencies using:

```bash
pip install -r requirements.txt
```

### Usage

```bash
python run.py \
  --hef yolov11n.hef \
  --input sample_images/
```


### BibTeX

```bibtex
@article{salem2026edgeaiweed,
  title={Enabling scalable and energy-efficient weed detection using data-driven edge AI for precision agriculture},
  author={Salem, Mohamed Abdallah and Rabia, Ahmed Harb},
  journal={Frontiers in Agronomy},
  volume={8},
  pages={1808404},
  year={2026},
  doi={10.3389/fagro.2026.1808404}
}
```

This repository uses the Hailo application pipeline style and should be used with a properly configured Hailo software environment. Users who are new to Hailo deployment are encouraged to first review the official Hailo Raspberry Pi 5 examples and the newer Hailo Apps repository:

- [Hailo Raspberry Pi 5 Examples](https://github.com/hailo-ai/hailo-rpi5-examples/tree/main)
- [Hailo Apps](https://github.com/hailo-ai/hailo-apps)

## Acknowledgment of Hailo Examples

This repository builds on the public Hailo Raspberry Pi 5 example ecosystem and follows the general structure of Hailo’s edge-AI deployment examples.

In particular, our inference workflow was developed with reference to the official Hailo Raspberry Pi 5 examples repository:

[Hailo Raspberry Pi 5 Examples](https://github.com/hailo-ai/hailo-rpi5-examples/tree/main)

The Hailo Raspberry Pi 5 examples provide reference pipelines for running AI models on Raspberry Pi 5 with Hailo AI accelerators, including support for the Raspberry Pi AI Kit, AI HAT, Hailo-8, and Hailo-8L devices. These examples provide a useful foundation for building custom edge-AI applications.

Our repository extends this direction toward **precision agriculture** by providing agriculture-specific model packs, documentation, and inference outputs for crop–weed detection and future agricultural AI tasks.

Please note that the Hailo Raspberry Pi 5 examples repository currently points users to the newer Hailo Apps repository for more up-to-date examples:

[Hailo Apps](https://github.com/hailo-ai/hailo-apps)

We gratefully acknowledge Hailo’s open-source examples, documentation, and community resources, which helped support the development of this agriculture-focused model zoo.

## License

This repository is released for research and educational use.

Unless otherwise stated, the source code, documentation, and example scripts in this repository are provided under the **MIT License**. See the [LICENSE](LICENSE) file for details.

The trained and compiled model files, including Hailo Executable Format `.hef` files, are provided for non-commercial research, education, and evaluation purposes. Users are responsible for ensuring that any use of the models, datasets, or deployment outputs complies with the licenses and terms of the original datasets, model frameworks, and third-party tools.

Datasets are not redistributed in this repository unless redistribution is explicitly permitted by the original dataset license. When datasets cannot be shared directly, links and preparation instructions are provided instead.

This repository builds on and references publicly available Hailo examples and tools. Users should also follow the licensing terms of HailoRT, Hailo Apps, Hailo Raspberry Pi 5 examples, Ultralytics YOLO, OpenCV, GStreamer, and any other third-party software used in the deployment pipeline.

Please cite the associated paper when using this repository in academic work:

```bibtex
@article{salem2026edgeaiweed,
  title={Enabling scalable and energy-efficient weed detection using data-driven edge AI for precision agriculture},
  author={Salem, Mohamed Abdallah and Rabia, Ahmed Harb},
  journal={Frontiers in Agronomy},
  volume={8},
  pages={1808404},
  year={2026},
  doi={10.3389/fagro.2026.1808404}
}
