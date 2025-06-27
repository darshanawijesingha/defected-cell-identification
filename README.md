# 🦠 Malaria Cell Image Classification

This project classifies microscopic blood cell images into **Parasitized** or **Uninfected** categories using a Convolutional Neural Network (CNN). The goal is to assist in the detection of malaria-infected cells through image classification.

---

## 📂 Dataset Overview

The dataset comprises high-resolution images of blood cells with two labels:

- **Parasitized**: Cells infected with malaria parasites.
- **Uninfected**: Healthy cells.

> The dataset is balanced, with an approximately equal number of samples from each class.

### 🔍 Sample Predictions

Below are examples of model predictions on unseen images:

![Sample Predictions](attachment:Screenshot_2025-06-27_180431.png)

---
## Labeling them as we need 
![Sample Predictions](attachment:Screenshot_2025-06-27_180431.png)


## Normalizing the given data 

![Sample Predictions](attachment:Screenshot_2025-06-27_180431.png)


## 🧠 Model Architecture

We use a **Sequential CNN** built using TensorFlow/Keras with the following architecture:

| Layer        | Output Shape   | Parameters |
| ------------ | -------------- | ---------- |
| Conv2D       | (222, 222, 32) | 896        |
| MaxPooling2D | (111, 111, 32) | 0          |
| Conv2D       | (109, 109, 64) | 18,496     |
| MaxPooling2D | (54, 54, 64)   | 0          |
| Conv2D       | (52, 52, 128)  | 73,856     |
| MaxPooling2D | (26, 26, 128)  | 0          |
| Flatten      | (86528)        | 0          |
| Dense (128)  | (128)          | 11,075,712 |
| Dropout      | (128)          | 0          |
| Dense (1)    | (1)            | 129        |

**Total Parameters:** ~11.6 million  
**Trainable Parameters:** ~11.6 million

---

## ⚙️ Dependencies

- Python 3.7+
- TensorFlow / Keras / opencv
- NumPy
- Matplotlib
- Scikit-learn

### Install packages:

```bash
pip install tensorflow numpy matplotlib scikit-learn
```
Prepare Dataset
Organize the dataset into folders like:

```
Edit
├── train/
│   ├── Parasitized/
│   └── Uninfected/
├── test/
```


## 📊 Class Distribution
Balanced class distribution ensures fair training:

## Parasitized: ~13,000 images

## Uninfected: ~13,000 images

## 📈 Performance Evaluation
## Confusion Matrix
The confusion matrix shows the model’s performance on the test set:

![Sample Predictions](attachment:Screenshot_2025-06-27_180431.png)


Note: The matrix shows that all predictions were for the "Parasitized" class. This may indicate a training bias or data leakage that should be investigated.

Accuracy and Loss Over Epochs
Model accuracy and loss on training and validation sets:
![Sample Predictions](attachment:Screenshot_2025-06-27_180431.png)

Accuracy reaches ~87%

Low loss on both train and validation sets

Slight validation loss increase at the end suggests mild overfitting

📌 Notes
All images are resized to (224, 224) before feeding into the model.

Binary classification:

0 = Parasitized

1 = Uninfected

The Dropout layer is used to prevent overfitting.
