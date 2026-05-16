Kidney Stone Segmentation with 2D Attention U-Net

Deep learning project for binary medical image segmentation that detects kidney stone regions from grayscale medical images using a 2D Attention U-Net architecture.

The goal of this project is to improve automated localization of kidney stones and demonstrate a practical application of AI in healthcare and medical image analysis.

Overview

This project:

trains a 2D Attention U-Net for kidney stone segmentation
uses focal-dice loss to handle class imbalance
applies strong medical image augmentation
evaluates performance with Dice Score
supports test-time augmentation (TTA) for inference
visualizes predicted masks against ground truth
Motivation

Kidney stone segmentation is important in medical imaging because accurate localization can support:

faster diagnosis
automated image analysis
better clinical decision support
downstream treatment planning

This project was created as part of my interest in:

Medical Image Analysis
Computer Vision
Deep Learning
AI in Healthcare
Project Highlights
Model: 2D Attention U-Net
Task: Binary segmentation
Input: Grayscale medical images
Output: Segmentation mask of kidney stone regions
Loss: Focal-Dice Loss
Optimizer: AdamW
Scheduler: OneCycleLR
Training: Mixed precision (AMP)
Validation: Train/validation/test split
Inference: Test-time augmentation
Dataset

The dataset contains paired medical images and segmentation masks.

Folder Structure
KSSD2025/
├── image/   # input images
└── label/   # ground truth masks
Dataset Split
Training: 70%
Validation: 10%
Test: 20%
Total Samples
Total images: 838
Train: 588
Validation: 83
Test: 167
Model Architecture

The model is based on Attention U-Net, which combines:

an encoder-decoder U-Net structure
skip connections
attention gates to focus on relevant spatial regions
a binary segmentation output layer
Main Building Blocks
DoubleConv
AttentionGate
AttentionUNet2D
Training Pipeline
Preprocessing

Images are resized to 256 × 256 and normalized before training.

Data Augmentation

The following augmentations are used:

horizontal flip
vertical flip
random 90° rotation
shift-scale-rotate
elastic transform
grid distortion
brightness/contrast adjustment
Gaussian noise
Training Settings
Image size: 256 × 256
Batch size: 8
Epochs: 50
Learning rate: 1e-3
Optimizer: AdamW
Scheduler: OneCycleLR
Early stopping patience: 10
Precision: Mixed precision training
Loss Function

The model is trained with Focal-Dice Loss, which combines:

Focal Loss: helps with class imbalance and hard examples
Dice Loss: improves overlap quality for segmentation

This is especially useful for medical segmentation tasks where the foreground object is often small.

Evaluation Metrics

The main evaluation metric is:

Dice Score

Additional metrics that can be reported:

IoU (Jaccard Score)
Precision
Recall
Specificity
Results
Validation
Best validation Dice: 91.1%
Test
Best test Dice: 90.8%
With Test-Time Augmentation
Validation Dice with TTA: 89.4%
Test Dice with TTA: 89.4%
Qualitative Results

The notebook includes visual comparisons of:

original image
ground truth mask
predicted mask

These visualizations help show how well the model localizes kidney stone regions.
