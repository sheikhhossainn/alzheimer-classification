# Alzheimer's Disease Classification from MRI Images

A deep learning project for automated multi-class classification of Alzheimer's disease stages from brain MRI scans. The project systematically compares transfer learning models, a custom CNN, and attention-based architectures, then validates the best model on an independent dataset to assess generalizability.

**Dataset:** [Augmented Alzheimer MRI Dataset v2](https://www.kaggle.com/datasets/uraninjo/augmented-alzheimer-mri-dataset-v2) — 40,384 axial brain MRI slices across 4 classes  
**Classes:** Non-Demented · Very Mild Demented · Mild Demented · Moderate Demented

---

## Repository Structure

```
alzheimer-classification/
├── Kaggle Notebook/
│   ├── Task 1 - EDA/          # Exploratory data analysis & class distribution
│   ├── Task 2 (Updated)/      # Transfer learning with 5-fold CV (ResNet50, EfficientNet-B0, DenseNet, MobileNetV2)
│   ├── Task 3/                # Custom CNN trained from scratch
│   ├── Task 4/                # CBAM attention-enhanced CNN (best model)
│   ├── Task 5/                # Generalizability test on independent dataset ⭐
│   └── Task 6/                # Final report & presentation slides
└── Project Report/            # Documentation, literature review, result reports
```

---

## Task Breakdown

### Task 1 — Exploratory Data Analysis
Validates data quality, class distributions, and image properties. Training set is synthetically balanced (~6,400–9,600 images/class); the validation set reflects realistic class imbalance, motivating F1-score as the primary metric.

### Task 2 — Transfer Learning (5-Fold CV)
Evaluates four ImageNet pre-trained architectures with rigorous 5-fold cross-validation:

| Model | Avg Accuracy | Avg F1 |
|---|---|---|
| ResNet50 | 92.87% ± 0.06% | 0.9287 |
| MobileNetV2 | 91.36% ± 0.07% | 0.9134 |
| EfficientNet-B0 | 88.00% ± 0.27% | 0.8797 |
| DenseNet121 | 87.54% ± 0.39% | — |

### Task 3 — Custom CNN (From Scratch)
Implements a bespoke CNN (Conv2D → BatchNorm → MaxPool → Dense) trained with 5-fold CV.  
Result: **72.59% ± 5.27% accuracy**, confirming that transfer learning substantially outperforms training from scratch on this dataset.

### Task 4 — CBAM Attention CNN
Augments the CNN with a **Convolutional Block Attention Module (CBAM)** — channel-wise and spatial attention gates that help the network focus on diagnostically relevant MRI regions.  
5-fold CV result: **93.71% ± 0.86% accuracy | F1: 0.9370** — the best-performing model on Dataset 1.

### Task 5 — Generalizability Testing ⭐
Validates the Task 4 CBAM model on a second, independent Alzheimer's MRI dataset — the **[OASIS (Open Access Series of Imaging Studies)](https://www.kaggle.com/datasets/ninadaithal/imagesoasis)** dataset (86,437 images) — to confirm that learned features transfer across data sources.

The notebook also includes **Grad-CAM explainability visualisations** to highlight which brain regions drive the model's predictions.

**Dataset 2 results:**

| Metric | Score |
|---|---|
| Accuracy | **99.97%** |
| F1-Score | 0.9997 |
| Precision | 0.9997 |
| Recall | 0.9997 |
| Training time | ~187 min (dual T4 GPU) |

The near-perfect scores on unseen data demonstrate that the CBAM model captures robust, generalizable MRI features rather than dataset-specific artifacts.

**Notebook:** `Kaggle Notebook/Task 5/task-5.ipynb`

### Task 6 — Final Report & Presentation
Contains the project slide deck and written report summarising the full experimental pipeline and conclusions.

---

## Results Summary

| Task | Model | Accuracy | F1 |
|---|---|---|---|
| Task 5 | CBAM CNN (Dataset 2) | **99.97%** | 0.9997 |
| Task 4 | CBAM Attention CNN | 93.71% | 0.9370 |
| Task 2 (Updated) | ResNet50 | 92.87% | 0.9287 |
| Task 2 (Updated) | MobileNetV2 | 91.36% | 0.9134 |
| Task 2 (Updated) | EfficientNet-B0 | 88.00% | 0.8797 |
| Task 2 (Updated) | DenseNet121 | 87.54% | — |
| Task 3 | Custom CNN | 72.59% | 0.7137 |

All multi-model results use **5-fold cross-validation**; F1-score is the primary metric to account for class imbalance.

---

## How to Run

1. **Clone the repository**
   ```bash
   git clone https://github.com/sheikhhossainn/alzheimer-classification.git
   cd alzheimer-classification
   ```

2. **Download the datasets**
   - Dataset 1: [Augmented Alzheimer MRI Dataset v2](https://www.kaggle.com/datasets/uraninjo/augmented-alzheimer-mri-dataset-v2)
   - Dataset 2 (Task 5): [OASIS Alzheimer's MRI dataset](https://www.kaggle.com/datasets/ninadaithal/imagesoasis)

3. **Install dependencies**
   ```bash
   pip install tensorflow keras numpy pandas matplotlib scikit-learn seaborn jupyter
   ```

4. **Run notebooks in order**
   ```bash
   jupyter notebook
   ```
   Open each task notebook sequentially: Task 1 → Task 2 (Updated) → Task 3 → Task 4 → Task 5.

> **GPU recommended.** Notebooks were developed on Kaggle with dual NVIDIA T4 GPUs. Training times range from ~2.5 hrs (Custom CNN) to ~4.3 hrs (EfficientNet-B0) depending on model complexity.

---

## Authors

**Sheikh Hossain Bin Bakhtiar** · [@sheikhhossainn](https://github.com/sheikhhossainn)  
**Humaira Habib Usha** · [@Humaira022](https://github.com/Humaira022)  
**Shawna Islam** · [@shawna175](https://github.com/shawna175)  
**Bushra Khan Zilik** · [@bushra-khan-zilik](https://github.com/bushra-khan-zilik)

---

## Acknowledgments

Dataset provided by the Kaggle community. Thanks to the ADNI initiative for supporting Alzheimer's research data accessibility.
