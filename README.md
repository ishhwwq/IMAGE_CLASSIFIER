<div align="center">

# CNN Image Classifier

**Deep Convolutional Neural Network for Binary Image Classification**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=flat-square&logo=tensorflow&logoColor=white)
![Keras](https://img.shields.io/badge/Keras-D00000?style=flat-square&logo=keras&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=flat-square&logo=jupyter&logoColor=white)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=flat-square)

</div>

---

## Overview

A binary image classifier built from scratch using TensorFlow and Keras. The model accepts 256×256 RGB images and outputs a sigmoid probability score, making it adaptable to any two-class classification problem. The full pipeline — data loading, preprocessing, training, evaluation, and inference — is documented in a single Jupyter notebook.

---

## Model Architecture

The network consists of three stacked convolutional blocks, each pairing a Conv2D layer with MaxPooling2D to extract and compress spatial features hierarchically. Filter depth follows a 16 → 32 → 16 progression with 3×3 kernels, ReLU activation, and stride 1 throughout. After the final pooling operation, features are flattened and passed through a 256-unit fully connected layer before reaching the sigmoid output neuron for binary classification.

| Layer | Configuration |
|---|---|
| Input | 256 × 256 × 3 (RGB) |
| Conv2D Block 1 | 16 filters, 3×3, ReLU → MaxPool |
| Conv2D Block 2 | 32 filters, 3×3, ReLU → MaxPool |
| Conv2D Block 3 | 16 filters, 3×3, ReLU → MaxPool |
| Dense | 256 units, ReLU |
| Output | 1 unit, Sigmoid |
| Optimizer | Adam |
| Loss | Binary Crossentropy |

---

## Dataset

The model expects a standard two-class directory layout with separate `train/` and `val/` splits, each containing one subdirectory per class. Images are resized to 256×256 and normalized to [0, 1] prior to training. The architecture is fully class-agnostic and can be applied to any binary classification task by simply swapping the dataset.

---

## Project Structure

```
image_classifier/
├── data/                       # Training and validation image dataset
├── logs/                       # TensorBoard training logs
├── model/                      # Saved model weights and architecture (.h5)
├── image_classifier.ipynb      # End-to-end notebook: training, evaluation, inference
├── 8iAb9k4aT.jpg               # Sample test image
├── 154006829.jpg               # Sample test image
└── README.md
```

---

## Performance

Trained for 20 epochs on a small dataset. The model converged steadily from epoch 3 onward with no signs of overfitting — validation loss consistently tracked training loss and validation accuracy matched or exceeded training accuracy across most epochs.

| Metric | Value |
|---|---|
| Final Training Accuracy | 99.55% |
| Final Validation Accuracy | 100.00% |
| Final Training Loss | 0.0227 |
| Final Validation Loss | 0.0196 |
| Epochs | 20 |
| Convergence Point | ~Epoch 9 (90%+ training accuracy) |
| Peak Validation Accuracy | 100.00% (achieved at Epochs 11, 13, 14, 17, 18, 20) |
| Input Resolution | 256 × 256 × 3 |
| Output | Sigmoid probability [0, 1] |

---

## Dependencies

Python 3.x · TensorFlow 2.x · Keras · NumPy · Matplotlib · OpenCV

---

## Author

**[@ishhwwq](https://github.com/ishhwwq)**
