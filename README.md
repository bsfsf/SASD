# Visibility-guided Keypoint Inference for Disambiguating Non-cooperative Spacecraft Pose Estimation
## 📦 FGST Dataset

### 📖 Overview

**FGST (Fermi Gamma-ray Space Telescope Dataset)** is a synthetic dataset designed for **monocular pose estimation of non-cooperative spacecraft**. It is built based on the publicly available 3D model of the *Fermi Gamma-ray Space Telescope (FGST)* from NASA.

Compared with existing datasets such as **SPEED**, FGST provides **richer and more comprehensive supervision**, including:

- 2D semantic keypoints  
- Keypoint visibility labels  
- Depth information  
- Geometrically consistent annotations  

This makes FGST particularly suitable for **keypoint-based pose estimation**, **learnable PnP frameworks**, and **multi-task learning**.

---

### 🎯 Motivation

Although deep neural networks (DNNs) have become the dominant paradigm in pose estimation, their performance heavily depends on **large-scale, high-quality annotated datasets**.

Existing datasets (e.g., SPEED) suffer from several limitations:

- Lack of keypoint annotations  
- Missing visibility information  
- Absence of structural geometric supervision  

To address these issues, FGST is proposed to provide **fine-grained and geometrically consistent annotations** for spacecraft pose estimation.

---

### 🛠️ Data Generation Pipeline

The dataset is generated using the **Blender rendering engine**, ensuring full control over the data generation process.

Each rendered sample contains:

- RGB image  
- 2D projections of predefined semantic keypoints  
- Keypoint visibility (computed via ray casting)  
- Depth map  

All annotations are generated automatically under a unified geometric framework, ensuring **strict consistency and accuracy**.

---

### 📷 Camera Sampling Strategy

To simulate realistic on-orbit observation scenarios:

- Cameras are sampled on a sphere centered at the spacecraft  
- The optical axis always points toward the target centroid  
- Additional perturbations are introduced to improve generalization  

Sampling ranges:

- **Azimuth angle**: [0°, 360°]  
- **Elevation angle**: [-75°, 75°]  
- **Distance**: 100 m – 600 m  

This setup ensures:

- Diverse viewpoints  
- Avoidance of extreme distortions  
- Proper target scale in images

<p align="center">
  <img src="assets/camera_position_3d_distribution.svg" width="45%">
  <img src="assets/camera_position_3d_point_cloud(1).svg" width="45%">
</p>

<p align="center">
  <em>Predefined semantic keypoint layout on the FGST spacecraft. Left: front view; Right: back view.</em>
</p>

---

### 🔑 Keypoint Definition

A set of **semantic 3D keypoints** is predefined on the spacecraft model:

- Distributed across the main body and solar panels  
- Includes symmetric structures for ambiguity analysis  
- Defined in the local coordinate system for cross-sample consistency  

For each frame:

- 2D keypoints are obtained via projection  
- Visibility is computed using **ray casting**, considering:
  - Field-of-view constraints  
  - Self-occlusion  

This guarantees **physically accurate and reliable annotations**.

---

### 📊 Dataset Statistics

- **Total images**: 10,500  
  - Training set: 10,000  
  - Test set: 500  

- **Resolution**: 1920 × 1200  

- **Camera parameters** (aligned with SPEED dataset):

| Parameter | Description | Value |
|----------|------------|-------|
| Nu | Image width (pixels) | 1920 |
| Nv | Image height (pixels) | 1200 |
| fx | Focal length (horizontal) | 0.0172 m |
| fy | Focal length (vertical) | 0.0172 m |
| Px | Pixel size (horizontal) | 5.86 µm |
| Py | Pixel size (vertical) | 5.86 µm |

---

### ✨ Key Features

- High-fidelity synthetic rendering  
- Pixel-level keypoint annotations  
- Visibility-aware labeling  
- Depth supervision  
- Fully reproducible data generation pipeline  
- Compatible with SPEED dataset  

---

### 🚀 Applications

FGST can be used for:

- Monocular spacecraft pose estimation  
- Keypoint detection and matching  
- Learnable PnP algorithms  
- Multi-task learning (pose + depth)  
- Ambiguity-aware pose estimation  

---

### 📌 Notes

- The dataset is generated with **fixed random seeds** for reproducibility  
- The CAD model is slightly simplified (e.g., chamfer removal) to improve annotation consistency  
- Designed for **non-cooperative space scenarios**  

---

