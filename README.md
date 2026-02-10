# Alzheimer's Disease Classification from MRI Images

A deep learning approach for automated classification of Alzheimer's disease using brain MRI scans. This project implements a hybrid CNN + ANN architecture for multi-class classification.

---

## Motivation

Alzheimer's disease is a progressive neurodegenerative disorder requiring early and accurate diagnosis. This project aims to develop an automated system to assist clinicians in making faster and more accurate diagnostic decisions using deep learning on neuroimaging data.

---

## Methodology

**Two-stage hybrid architecture:**

1. **CNN (Feature Extraction)**: Learns spatial features from MRI images such as tissue atrophy and structural biomarkers
2. **ANN (Classification)**: Maps extracted features to disease categories

---

## Dataset

**[Augmented Alzheimer MRI Dataset v2](https://www.kaggle.com/datasets/tourist55/alzheimers-dataset-4-class-of-images)** from Kaggle

**Classes:**
- Non-Demented
- Very Mild Demented
- Mild Demented
- Moderate Demented

---

## Repository Contents

```
alzheimer-classification/
├── Kaggle Notebook/       # EDA and model training notebooks
├── Project Report/        # Project documentation and results
└── Related Papers/        # Reference research papers
```

---

## Usage

1. **Clone the repository**:
   ```bash
   git clone https://github.com/sheikhhossainn/alzheimer-classification.git
   cd alzheimer-classification
   ```

2. **Download the dataset** from [Kaggle](https://www.kaggle.com/datasets/tourist55/alzheimers-dataset-4-class-of-images)

3. **Install dependencies**:
   ```bash
   pip install tensorflow numpy pandas matplotlib scikit-learn jupyter
   ```

4. **Open notebooks**:
   ```bash
   jupyter notebook
   ```

---

## Limitations and Future Work

**Limitations:**
- Dataset contains augmented images which may introduce artificial patterns
- Requires significant computational resources
- Generalization limited to ADNI-based cohort

**Future Work:**
- Implement transfer learning with pre-trained models
- Add explainable AI techniques (Grad-CAM, attention mechanisms)
- Cross-dataset validation
- Clinical deployment interface

---

## Authors

**Sheikh Hossain Bin Bakhtiar** ([@sheikhhossainn](https://github.com/sheikhhossainn)) <br>
**Humaira Habib Usha** ([@humaira](https://github.com/Humaira022)) <br>
**Shawna Islam** ([@shawna](https://github.com/shawna175)) <br>
**Bushra Khan Jhilik** <br>

---

## License

MIT License - see full text in repository

---

## Acknowledgments

Thanks to ADNI and the Kaggle community for the dataset.

**Dataset Citation:**
```
Augmented Alzheimer MRI Dataset v2
https://www.kaggle.com/datasets/tourist55/alzheimers-dataset-4-class-of-images
```
