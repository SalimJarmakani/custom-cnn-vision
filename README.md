# Custom CNN for Lung Disease Classification

This repository presents a **compact Convolutional Neural Network (CNN)** designed from scratch for **lung disease classification** using chest X-ray images.  
A key contribution of this work is achieving competitive performance with a model containing **only ~1 million parameters**, significantly smaller than standard transfer learning backbones.

## Task
Multi-class classification of chest X-rays into:
- Normal
- Pneumonia
- Tuberculosis

## Model Overview
- **Custom CNN (≈1.0M parameters)**  
  Lightweight architecture optimized for efficiency and generalization:
  - Standard and depthwise-separable convolutions  
  - Residual connections  
  - Squeeze-and-Excitation (SE) blocks  
  - Global Average Pooling + Dropout  

- **Transfer Learning Baselines**
  - ResNet50 (≈25M parameters, ImageNet pretrained)
  - MobileNetV2 (≈3.4M parameters, ImageNet pretrained)

## Training Highlights
- Optimizer: Adam  
- Loss: **Weighted Focal Loss (γ = 1.4)** for the Custom CNN  
- Primary metric: **Weighted F1-score**  
- Safe medical image augmentation  
- Early stopping and learning-rate scheduling  

## Results (Test Set)
| Model        | Params | Weighted F1 | Accuracy |
|-------------|--------|-------------|----------|
| ResNet50     | ~25M   | 75.87%      | 75.0%    |
| MobileNetV2  | ~3.4M  | 75.53%      | 75.2%    |
| **Custom CNN** | **~1.0M** | **77.76%** | **77.5%** |

Despite its small size, the Custom CNN achieved the highest weighted F1-score, demonstrating that **careful architectural design and loss selection can rival much larger pretrained models**.

## Interpretability
Grad-CAM visualizations were used to analyze model attention and confirm reliance on clinically meaningful regions.

## Disclaimer
This project is for **research and educational purposes only** and is **not intended for clinical diagnosis**.
