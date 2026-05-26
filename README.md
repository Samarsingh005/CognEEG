# 🧠 CognEEG — EEG-Based Neurological Disease Classification

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python)
![PyTorch](https://img.shields.io/badge/PyTorch-Deep%20Learning-EE4C2C?logo=pytorch)
![MNE](https://img.shields.io/badge/MNE-EEG%20Processing-brightgreen)
![License](https://img.shields.io/badge/License-MIT-yellow)
![Status](https://img.shields.io/badge/Status-Research%20Project-orange)

> An end-to-end machine learning pipeline for classifying **Alzheimer's Disease (AD)**, **Frontotemporal Dementia (FTD)**, and **healthy controls** from raw EEG brain recordings — using signal processing, topomap image generation, and deep learning.

---

## 📌 Overview

CognEEG transforms raw clinical EEG recordings into interpretable frequency-band topomaps and feeds them into a convolutional neural network for neurological disease classification. The project demonstrates practical deep learning deployment in a healthcare ML context.

| Task | Accuracy |
|------|----------|
| Binary Classification (Patient vs. Control) | **~80%** |
| Multiclass Classification (AD / FTD / Control) | **60–70%** |

---

## 🧬 Pipeline Architecture

```
Raw EEG (.set files)
        │
        ▼
  [1] Preprocessing
  MNE-based bandpass filtering (0.5–70 Hz)
  Cz reference / average reference
        │
        ▼
  [2] Topomap Generation
  5 frequency bands: delta, theta, alpha, beta, gamma
  Per-subject PNG topomap images
        │
        ▼
  [3] Dataset Construction
  CSV split: 70% train / 15% val / 15% test
  Stratified by diagnostic label
        │
        ▼
  [4] Deep Learning Classification
  CNN trained on topomap images (224×224)
  PyTorch DataLoader pipeline
        │
        ▼
  [5] Evaluation
  Binary & multiclass accuracy, loss curves
```

---

## 📂 Repository Structure

```
CognEEG/
├── notebooks/
│   └── CognEEG_pipeline.ipynb    # Full pipeline: preprocessing → classification
├── requirements.txt               # Python dependencies
├── .gitignore
└── README.md
```

---

## 📊 Dataset

This project uses the **OpenNeuro EEG dataset** for Alzheimer's and FTD research.

| Detail | Info |
|--------|------|
| Source | [OpenNeuro ds004504 v1.0.8](https://openneuro.org/datasets/ds004504/versions/1.0.8) |
| Subjects | AD patients, FTD patients, healthy controls |
| Format | EEGLAB `.set` files |
| Labels | `A` = Alzheimer's, `F` = FTD, `C` = Control |

> **Note:** The dataset is not included in this repository. Download it from OpenNeuro and place it at the path expected in the notebook (`/content/drive/MyDrive/AD-DATA/`).

---

## ⚙️ Setup & Usage

### 1. Clone the repository
```bash
git clone https://github.com/Samarsingh005/CognEEG.git
cd CognEEG
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Download the dataset
Go to [OpenNeuro ds004504](https://openneuro.org/datasets/ds004504/versions/1.0.8) and download the dataset. Upload it to your Google Drive under `MyDrive/AD-DATA/`.

### 4. Run the notebook
Open `notebooks/CognEEG_pipeline.ipynb` in [Google Colab](https://colab.research.google.com/) and run all cells sequentially.

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| `MNE` | EEG signal loading, preprocessing, topomap generation |
| `PyTorch` | CNN model training and evaluation |
| `Scikit-learn` | Train/val/test splitting, evaluation metrics |
| `Pandas / NumPy` | Data handling and label management |
| `Matplotlib` | Visualization and topomap saving |

---

## 📈 Results

- Achieved **~80% binary accuracy** (Patient vs. Control) using EEG topomap images
- Achieved **60–70% multiclass accuracy** across AD, FTD, and healthy classes
- Applied 5-band spectral decomposition (δ θ α β γ) with per-band color-coded topomaps

---

## 👤 Author

**Samar Singh Rathore**
B.Tech AI/ML — Dronacharya College of Engineering
ML Research Intern @ IIT Delhi & GGSIPU

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?logo=linkedin)](https://linkedin.com/in/samarsinghrathore0001)
[![GitHub](https://img.shields.io/badge/GitHub-Samarsingh005-black?logo=github)](https://github.com/Samarsingh005)

---

## 📄 License

This project is licensed under the MIT License — see [LICENSE](LICENSE) for details.
