# UBC-OCEAN Image Classification Project

## 📌 Project Overview

This project focuses on classifying histopathological images from the **UBC-OCEAN dataset** into five distinct categories using deep learning techniques. The implementation involves custom CNNs and transfer learning models like **InceptionResNetV2**, with preprocessing, augmentation, and training pipelines built using TensorFlow/Keras.

## 📁 Dataset Overview

- **Dataset Name:** [UBC-OCEAN] 
- **Images:**
  - Full-size Whole Slide Images (WSI): `/kaggle/input/UBC-OCEAN/train_images/`
  - Thumbnail versions: `/kaggle/input/UBC-OCEAN/train_thumbnails/` and `/kaggle/input/UBC-OCEAN/test_thumbnails/`
- **Labels:** 5 classes (`HGSC`, `LGSC`, `EC`, `CC`, `MC`) mapped to numeric values `0–4`
- **Metadata Files:**
  - Train labels: `train.csv`
  - Test metadata: `test.csv`
  - Sample submission: `sample_submission.csv`

### Class Distribution:
| Label | Class Name | Count |
|-------|------------|-------|
| 0     | HGSC       | 222   |
| 1     | LGSC       | 47    |
| 2     | EC         | 124   |
| 3     | CC         | 99    |
| 4     | MC         | 46    |

Class imbalance was addressed using undersampling techniques.


## 🧠 Models Used

### 1. **Custom CNN**

A custom convolutional neural network built using TensorFlow/Keras layers.`

#### Performance:
- This model underperformed due to limited depth and complexity for the given task.

---

### 2. **Improved Custom CNN with Inception-like Blocks**

An advanced CNN architecture inspired by Inception modules, combining multiple filter sizes and concatenating outputs.

#### Key Features:
- Multiple convolution paths (e.g., 1x1, 3x3 convolutions)
- Batch normalization and ReLU activations
- Concatenation of feature maps

#### Performance:
- Significant improvement over basic CNN due to richer feature extraction.

---

### 3. **Transfer Learning with InceptionResNetV2**

Used pre-trained **InceptionResNetV2** as a base model with a custom top layer for fine-tuning.


#### Training:
- **Optimizer:** Adam
- **Loss Function:** Sparse Categorical Crossentropy
- **Metrics:** Accuracy

#### Performance:
- Best performing model due to strong feature extraction capabilities of InceptionResNetV2.


## 📁 Dataset Source

- **Images:** `/kaggle/input/UBC-OCEAN/train_thumbnails/`
- **Labels:** `train.csv`

Images were resized to `(224, 224)` and normalized before being fed into the models.

---

## 📝 Notes

- Class imbalance was handled using `RandomUnderSampler`.
- Image augmentation techniques included rotation, zooming, flipping.
- Best results achieved using **fine-tuned InceptionResNetV2**.
