# Early-Detection-Saves-Life  
**Comparative Evaluation of CNN and Vision Transformer Models for Alzheimer’s Disease Staging from MRI**

---

## 📌 Overview
This repository contains the code, experiments, and results from my bachelor thesis:  
**“Early Detection Saves Life: Comparative Evaluation of Traditional Convolutional Neural Network Model and the Vision Transformer Model – A Deep Learning Approach to Classify Dementia Stages.”**

Alzheimer’s disease diagnosis still relies heavily on subjective MRI/PET interpretation.  
This project evaluates whether **Vision Transformers (ViT)**—originally built for NLP—can outperform a **Convolutional Neural Network (CNN)** in classifying MRI scans into dementia stages.

The models are trained on a **balanced subset** of the OASIS MRI dataset (86,437 samples total) consisting of:
- Non Demented  
- Very Mild Dementia  
- Mild Dementia  
- Moderate Dementia  

---

## 🧠 Objectives
- Compare ViT vs CNN on dementia-stage MRI classification.  
- Evaluate using **precision**, **recall**, **F1-score**, and **accuracy**.  
- Study misclassification patterns in early dementia.  
- Understand trade-offs between accuracy, GPU compute, and scalability.  

---

## 📂 Repository Structure

- `CNN.ipynb` – Data preprocessing, training and evaluation of the CNN model.
- `ViT.ipynb` – Vision Transformer implementation (general ViT experiments).
- `MRI_ViT.ipynb` – ViT pipeline adapted specifically for MRI data.

---

## 📊 Dataset
- **Source:** OASIS (Open Access Series of Imaging Studies) → via Kaggle  
- **Total samples:** 86,437 MRI slices  
- **Four target classes:**  
  - Non Demented  
  - Very Mild Dementia  
  - Mild Dementia  
  - Moderate Dementia  
- Severe class imbalance originally  
- Resampled to **13,725 samples per class** for balanced learning  

---

## 🔧 Preprocessing
- Converted to **RGB**  
- Normalized pixel values  
- Resized:  
  - **ViT:** 224×224  
  - **CNN:** 128×128  
- Train/validation/test split:  
  - **70% / 15% / 15%**  
- Image patches (16×16) used for ViT  
- Stratified sampling to preserve class distribution  

---

## 🏗️ Models

### Vision Transformer (ViT)
- Model: `vit-base-patch16-224-in21k`  
- Pretrained on ImageNet-21k  
- Uses patch embeddings + multi-head self-attention  
- Trained for 5 epochs  
- Requires high GPU compute (L4 used)  

### Convolutional Neural Network (CNN)
- 128×128 input  
- Multiple Conv → BN → ReLU blocks  
- Pooling + Dropout for regularization  
- Lightweight and fast  
- Much lower computational footprint  

---
