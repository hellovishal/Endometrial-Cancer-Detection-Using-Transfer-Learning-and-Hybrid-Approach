# Endometrial-Cancer-Detection-Using-Transfer-Learning-and-Hybrid-Approach

# Endometrial Cancer Detection Using Transfer Learning and Hybrid Deep Learning Approaches

## Overview

Endometrial cancer is one of the most common gynecological cancers affecting women worldwide. Early diagnosis plays a crucial role in improving treatment outcomes and survival rates. Histopathological examination remains the gold standard for diagnosis; however, manual analysis is time-consuming and highly dependent on expert pathologists.

This project explores the application of Deep Learning and Transfer Learning techniques for automated classification of endometrial histopathology images. Multiple architectures including DenseNet201, InceptionV3, Modified Xception, and a Hybrid ResNet-Xception model were evaluated to distinguish between benign and malignant tissue samples.

The project was developed as a Major Project at **Maulana Azad National Institute of Technology (MANIT), Bhopal**.

## Problem Statement

Histopathological image analysis is a specialized and labor-intensive task. The objective of this project is to develop a Computer-Aided Diagnosis (CAD) system capable of automatically identifying malignant endometrial tissue from microscopic images.

The proposed solution leverages deep convolutional neural networks and transfer learning techniques to improve diagnostic efficiency and reduce dependency on handcrafted image features.

---

## Dataset

The project uses a publicly available Endometrial Histopathology Dataset containing:

* **498 endometrial tissue samples**
* **3,302 image patches**
* Image resolution: **640 × 480**
* Magnification: **10× and 20×**

### Classes

| Class | Description                |
| ----- | -------------------------- |
| EA    | Endometrial Adenocarcinoma |
| EH    | Endometrial Hyperplasia    |
| EP    | Endometrial Polyp          |
| NE    | Normal Endometrium         |

### Binary Classification Mapping

| Category  | Classes    |
| --------- | ---------- |
| Benign    | NE, EP, EH |
| Malignant | EA         |

### Dataset Distribution

* Benign Images: 2,767
* Malignant Images: 535

---

## Methodology

### Data Preprocessing

* Image resizing to **299 × 299**
* Pixel normalization
* Train/Test split: **80:20**
* Validation split from test set
* Data augmentation:

  * Rotation
  * Horizontal Flip
  * Vertical Flip
  * Zoom Augmentation

---

## Models Evaluated

### 1. DenseNet201 Transfer Learning

Pretrained on ImageNet.

Architecture:

* DenseNet201 Backbone
* Global Average Pooling
* Batch Normalization
* Dropout (50%)
* Dense Layer
* Softmax Output

Training Configuration:

* Optimizer: Adam
* Learning Rate: 0.0001
* Loss Function: Binary Cross Entropy

---

### 2. InceptionV3 Transfer Learning

Pretrained on ImageNet.

Architecture:

* InceptionV3 Backbone
* Global Average Pooling
* Batch Normalization
* Fully Connected Layer
* Softmax Output

Training Configuration:

* Optimizer: Adam
* Binary Cross Entropy Loss

---

### 3. Modified Xception Network

Custom architecture trained from scratch without pretrained weights.

Characteristics:

* Depthwise Separable Convolutions
* Batch Normalization
* Residual Connections
* Lightweight Architecture

---

### 4. Hybrid ResNet + Xception Architecture

A custom architecture combining:

* Inception/Xception-style feature extraction
* Residual Learning Blocks
* Global Average Pooling
* Fully Connected Classification Layers

The goal was to leverage both deep feature extraction and residual learning for improved classification performance.

---

## Training Techniques

### Callbacks

* ModelCheckpoint
* ReduceLROnPlateau
* EarlyStopping

### Test Time Augmentation (TTA)

Predictions are averaged across multiple augmented versions of the same image to improve robustness and generalization.

---

## Evaluation Metrics

The models were evaluated using:

* Accuracy
* Precision
* Recall
* F1-Score
* Confusion Matrix
* ROC Curve
* Area Under Curve (AUC)

---

## Project Structure

```text
.
├── 1.ipynb                  # Model training and evaluation notebook
├── Major_Project_Report.pdf # Detailed project report
├── Dataset/
│   ├── EA/
│   ├── EH/
│   ├── EP/
│   └── NE/
├── Saved Models/
├── Results/
└── README.md
```

---

## Technologies Used

### Deep Learning

* TensorFlow
* Keras

### Data Processing

* NumPy
* Pandas
* OpenCV

### Machine Learning

* Scikit-Learn

### Visualization

* Matplotlib

---

## Key Features

* Automated Endometrial Cancer Detection
* Transfer Learning using State-of-the-Art CNNs
* Histopathology Image Classification
* Data Augmentation Pipeline
* Test Time Augmentation (TTA)
* ROC and Confusion Matrix Evaluation
* Comparative Study of Multiple Architectures

---

## Results

The study compares:

* DenseNet201 Transfer Learning
* InceptionV3 Transfer Learning
* Modified Xception
* Hybrid ResNet-Xception

Experimental results demonstrate that transfer learning-based architectures significantly outperform models trained from scratch on limited histopathology datasets.

The work highlights the effectiveness of deep learning for computer-aided diagnosis of endometrial cancer and establishes a foundation for future multi-class histopathological classification systems.

---

## Future Work

* Multi-class classification of all disease subtypes
* Whole Slide Image (WSI) analysis
* Advanced data augmentation techniques
* Attention-based architectures
* Vision Transformers (ViT)
* Explainable AI (XAI) for medical interpretability
* Clinical deployment and validation

---

## References

1. Sun et al., *Computer-Aided Diagnosis in Histopathological Images of the Endometrium Using a CNN and Attention Mechanisms*
2. Ebrahimian et al., *Class-Aware Image Search for Interpretable Cancer Identification*
3. Riasatian et al., *Fine-Tuning and Training of DenseNet for Histopathology Image Representation*
4. TensorFlow/Keras Documentation
5. ImageNet Transfer Learning Models

---

## Disclaimer

This project was developed for academic and research purposes only and is not intended to be used as a standalone clinical diagnostic system. Any medical decision should be made by qualified healthcare professionals.
