# Classical Computer Vision Feature Fusion for Multi-Class Image Classification

### SIFT-Based Bag-of-Words + HOG Features + Linear SVM Classifier

This repository implements a classical computer vision pipeline for multi-class image classification using a hybrid feature extraction framework combining **SIFT Bag-of-Words (BoW)** representation and **Histogram of Oriented Gradients (HOG)** descriptors, classified with a **Linear Support Vector Machine (Linear SVM)**.

The objective is to provide a lightweight, interpretable alternative to deep learning–based models while maintaining solid performance on real-world multi-class datasets such as vehicles and pedestrian images.

---

## 🔍 **1. Overview**

This project proposes a feature-fusion approach using:

- **Local invariant keypoints** through SIFT
- **Visual vocabulary construction** using MiniBatch K-Means
- **BoW histogram representation** (normalized)
- **Global shape descriptors** using HOG
- **Feature-level fusion**:  
  \[
  X*{final} = [X*{BoW} \; || \; X\_{HOG}]
  \]
- **Classification** using Linear SVM with hyperparameter optimization

The pipeline is optimized for speed, low memory usage, and deployability on resource-limited systems.

---

## ⚙️ **2. Features Used**

### ✔ SIFT — Local Keypoint Descriptors

Scale- and rotation-invariant descriptors capturing local image structure.

### ✔ Bag-of-Words — Visual Vocabulary

MiniBatchKMeans is used to cluster SIFT descriptors efficiently, enabling fast BoW construction even for large datasets.

### ✔ HOG — Global Gradient Structure

Captures shape and edge flow patterns complementary to SIFT.

### ✔ Feature Fusion

The concatenation of normalized BoW histograms and HOG vectors results in a high-dimensional but discriminative representation.

### ✔ Linear SVM

Chosen for:

- Stability
- Generalization
- Strong performance on high-dimensional sparse features
- Efficient optimization

---

## 🚀 **3. Training**

Training performs the following steps:

1. Load images and assign labels
2. Extract SIFT descriptors
3. Build BoW dictionary (`k=300` by default)
4. Convert descriptors into normalized BoW histograms
5. Extract HOG descriptors
6. Fuse features
7. Train Linear SVM via GridSearchCV
8. Save model to `.sav` file
9. Save BoW dictionary

---

## 🧪 **4. Evaluation**

The evaluation script:

- Loads test images
- Extracts SIFT descriptors
- Converts to BoW histograms
- Extracts HOG features
- Fuses features
- Loads the trained SVM model
- Predicts class labels
- Computes accuracy
- Generates classification report
- Plots confusion matrix with proper class names

---

## 📊 **5. Result**

Train Accuracy: 1.0
Validation Accuracy: 0.9750692520775623

Model achieve **Test Accuracy : 0.98 overall accuracy** with 10 data each labels
