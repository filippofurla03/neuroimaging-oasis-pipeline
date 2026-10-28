```markdown
# 🧠 Automated Neuroimaging Pipeline for CDR Prediction (OASIS-1)

Automated end-to-end pipeline for predicting Clinical Dementia Rating (CDR) using structural T1-weighted MRI from the OASIS-1 dataset.

## 📌 Project Overview

This repository compares two approaches to neuroimaging classification:

1. **Approach A — Classical ML:** Structural registration to the MNI152 template, automated hippocampal ROI extraction using the Harvard-Oxford Atlas, and ensemble classification with Random Forest or XGBoost.
2. **Approach B — 3D Deep Learning:** End-to-end volumetric 3D DenseNet121 built with PyTorch and MONAI.

## 🛠️ Tech Stack & Requirements

- **Python environment:** Conda (`neuroimg`)
- **Core libraries:** PyTorch, MONAI, Nilearn, Nibabel, Scikit-learn, Seaborn, Matplotlib

## 📊 Summary of Results

| Approach | Methodology | Key features / inputs | Accuracy |
| :--- | :--- | :--- | :---: |
| **Approach A** | Classical ML (Random Forest) | Clinical data (MMSE, age, eTIV) and total hippocampal volume | **85.71%** |
| **Approach B** | 3D Deep Learning (DenseNet121) | Raw 3D T1 volumes (96 × 96 × 96) | **48.00%** |

### Key Takeaways

- **Classical ML with biomarkers:** Feature extraction and domain knowledge (hippocampal volumetry) can perform well on small sample sizes (N < 50).
- **3D deep learning bottlenecks:** End-to-end 3D CNNs generally require larger training datasets and substantial GPU compute; on this dataset, the model achieved lower accuracy.

## 📁 Repository Structure

├── data/                       # Local raw & processed NIfTI datasets
├── notebooks/
│   ├── 01_data_exploration.ipynb
│   ├── 02_preprocessing_registration.ipynb
│   ├── 03_feature_extraction.ipynb      # Approach A (Hippo Volumetry & ML)
│   └── 04_deep_learning_monai_3d.ipynb  # Approach B (MONAI 3D CNN)
├── environment.yml
└── README.md
