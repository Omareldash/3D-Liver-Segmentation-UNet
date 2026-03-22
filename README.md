# 🧠 3D Liver Segmentation using U-Net

This repository contains a PyTorch implementation of a **3D U-Net** designed for dense volumetric segmentation of the liver. By leveraging 3D convolutions, the model captures spatial context across slices, significantly reducing *"staircase"* artifacts compared to traditional 2D approaches.

---

## 🏗️ Architecture Details

The model follows a symmetrical encoder-decoder structure optimized for volumetric medical data:

- **Contracting Path (Encoder):**  
  Uses repeated **DoubleConv3D** blocks *(3×3×3 convolutions + BatchNorm + ReLU)*.  
  Spatial dimensions are reduced using **3D MaxPooling (2×2×2)**, while feature channels increase.

- **Bottleneck:**  
  A high-capacity representation layer with **1024 filters** capturing global volumetric features.

- **Expansive Path (Decoder):**  
  Uses **3D Transposed Convolutions** for upsampling.

- **Skip Connections:**  
  Combines encoder and decoder features to preserve fine spatial details.

- **Output Layer:**  
  A final **1×1×1 convolution** maps features into a binary segmentation mask.

---

## 🧪 Preprocessing

Input volumes are resized, normalized, and cleaned to improve segmentation quality.

![Preprocessing](path/to/your/preprocessing_image.png)

---

### 📈 Dice Accuracy 

Best Validation Dice:   0.9453

Best Train Dice:        0.9448

> **Key Insight:**  
> 3D convolutions allow the model to capture continuity across slices (Z-axis), resulting in smoother and more consistent segmentation compared to 2D methods.

---

## ⚙️ Technical Summary

| **Project** | [3D Liver Segmentation Model](https://www.kaggle.com/code/omareldash75/3d-liver-segmentation-using-u-net) |
| **Input Size** | 64 × 128 × 128 |
| **Architecture** | 3D U-Net |
| **Optimizer** | Adam |
| **Loss Function** | Dice Loss |
| **Dataset** | [Kaggle Liver Segmentation Dataset](https://www.kaggle.com/datasets/prathamgrover/3d-liver-segmentation) |

---

## 📚 References

- Ronneberger, O., et al. (2015).  
  *U-Net: Convolutional Networks for Biomedical Image Segmentation.*

- Çiçek, Ö., et al. (2016).  
  *3D U-Net: Learning Dense Volumetric Segmentation from Sparse Annotation.*

---

## 🚀 Future Improvements

- Add multi-organ segmentation  
- Improve performance using attention mechanisms  
- Experiment with different loss functions (e.g., Dice + BCE)  
- Deploy model as a medical imaging tool  
