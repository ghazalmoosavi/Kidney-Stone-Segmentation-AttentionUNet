# Kidney Stone Segmentation with 2D Attention U-Net 🩺🧠

> Deep learning project for **binary medical image segmentation** using a **2D Attention U-Net** to accurately detect kidney stone regions from grayscale medical images.

<p align="center">
  <img src="https://img.shields.io/badge/PyTorch-DeepLearning-red?style=for-the-badge&logo=pytorch">
  <img src="https://img.shields.io/badge/Task-Medical%20Segmentation-blue?style=for-the-badge">
  <img src="https://img.shields.io/badge/Model-Attention%20U--Net-success?style=for-the-badge">
  <img src="https://img.shields.io/badge/Dice%20Score-90%25+-brightgreen?style=for-the-badge">
</p>

---

# 📌 Overview

This project focuses on **automated kidney stone segmentation** using a **2D Attention U-Net** architecture.

The system is designed to:

✅ Detect kidney stone regions from medical images
✅ Handle severe class imbalance using **Focal-Dice Loss**
✅ Improve generalization with strong augmentations
✅ Use **mixed precision training (AMP)** for faster training
✅ Support **Test-Time Augmentation (TTA)** during inference
✅ Visualize predicted masks against ground truth masks

---

# 🧠 Why Attention U-Net?

Traditional U-Net architectures treat all spatial information equally.
**Attention U-Net** improves this by learning to focus on the most relevant regions of the image.

### Key Advantages

* Better localization of small kidney stone regions
* Improved segmentation precision
* Reduced background noise influence
* Strong performance on grayscale medical images

---

# 🎯 Project Goals

This project aims to support:

* Faster medical image analysis
* Automated kidney stone localization
* AI-assisted clinical workflows
* Research in healthcare computer vision

---

# 🏗️ Model Architecture

The model uses an **encoder-decoder Attention U-Net** with skip connections and attention gates.

## Main Components

| Component       | Purpose                         |
| --------------- | ------------------------------- |
| `DoubleConv`    | Feature extraction              |
| `AttentionGate` | Focus on important regions      |
| `Encoder`       | Downsampling + context learning |
| `Decoder`       | Upsampling + reconstruction     |
| `Output Layer`  | Binary segmentation mask        |

---

# 📂 Dataset Structure

```bash
KSSD2025/
├── image/   # Input grayscale images
└── label/   # Ground truth segmentation masks
```

---

# 📊 Dataset Split

| Split      | Samples | Percentage |
| ---------- | ------: | ---------: |
| Training   |     588 |        70% |
| Validation |      83 |        10% |
| Test       |     167 |        20% |
| **Total**  | **838** |   **100%** |

---

# ⚙️ Training Pipeline

## 🖼️ Preprocessing

* Resize images to **256 × 256**
* Normalize pixel values
* Convert masks to binary format

---

## 🔄 Data Augmentation

Strong augmentation is applied to improve robustness:

* Horizontal Flip
* Vertical Flip
* Random Rotation (90°)
* Shift-Scale-Rotate
* Elastic Transform
* Grid Distortion
* Brightness & Contrast Adjustment
* Gaussian Noise

---

# 🚀 Training Configuration

| Setting        | Value                 |
| -------------- | --------------------- |
| Model          | Attention U-Net       |
| Image Size     | 256 × 256             |
| Batch Size     | 8                     |
| Epochs         | 50                    |
| Optimizer      | AdamW                 |
| Scheduler      | OneCycleLR            |
| Learning Rate  | 1e-3                  |
| Loss Function  | Focal-Dice Loss       |
| Precision      | Mixed Precision (AMP) |
| Early Stopping | Patience = 10         |

---

# 📉 Loss Function

The project uses a hybrid **Focal-Dice Loss**:

## 🔹 Focal Loss

Handles:

* class imbalance
* difficult examples
* small foreground objects

## 🔹 Dice Loss

Optimizes:

* overlap quality
* segmentation accuracy
* boundary consistency

This combination is highly effective for **medical segmentation tasks**.

---

# 📏 Evaluation Metrics

The primary evaluation metric is:

## ✅ Dice Score

Additional metrics:

* IoU (Jaccard Score)
* Precision
* Recall
* Specificity

---

# 🏆 Results

## Validation Performance

| Metric               |     Score |
| -------------------- | --------: |
| Best Validation Dice | **91.1%** |

---

## Test Performance

| Metric         |     Score |
| -------------- | --------: |
| Best Test Dice | **90.8%** |

---

## 🔄 Test-Time Augmentation (TTA)

| Metric                | Score |
| --------------------- | ----: |
| Validation Dice (TTA) | 89.4% |
| Test Dice (TTA)       | 89.4% |

---

# 🖼️ Qualitative Results

The notebook visualizes:

* Original medical image
* Ground truth mask
* Predicted segmentation mask

These comparisons demonstrate how effectively the model localizes kidney stone regions.

---

# 💡 Key Features

✨ Attention-based segmentation
✨ Medical image augmentation pipeline
✨ Mixed precision training (AMP)
✨ Test-Time Augmentation (TTA)
✨ Focal-Dice hybrid loss
✨ Dice-based evaluation
✨ Clean visualization pipeline

---


<p align="center">
  ⭐ If you found this project useful, consider giving it a star!
</p>
