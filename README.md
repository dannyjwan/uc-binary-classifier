# Ulcerative Colitis Binary Classifier

A deep learning pipeline designed to detect the presence of Ulcerative Colitis (UC) from endoscopic images. This project utilizes transfer learning with a ResNet50 Convolutional Neural Network (CNN) to assist gastroenterologists in making more accurate diagnoses in clinical practice.

## Clinical Context
Ulcerative Colitis is a chronic autoimmune-related inflammatory bowel disease (IBD) affecting the lower gastrointestinal tract. Currently, the gold standard for diagnosis is physician evaluation of endoscopic images and biopsies. Due to differences in physician perception, misdiagnoses are common. 

This project aims to reduce misdiagnosis rates and subsequent healthcare burdens by providing a reliable, automated secondary assessment tool.

## Dataset
The model is trained on the ERS dataset from the Computer Vision & Artificial Laboratory at Gdańsk University of Technology. 
* **Scope:** ~1TB of raw endoscopy video frames.
* **Current Subset:** 17,011 filtered, meaningfully labeled frames across 334 patients.
* **Preprocessing:** Data splits (80/10/10) were strictly performed at the patient level to prevent data leakage between frames of the same video.

## Current Model Performance
The current best-performing model is a ResNet50 pre-trained on ImageNet, optimized using Binary Cross-Entropy loss. It was evaluated against a custom 3-layer CNN baseline.

| Metric | Baseline CNN | ResNet50 |
| :--- | :--- | :--- |
| **Accuracy** | 0.52 | 0.72 |
| **AUROC** | 0.63 | 0.93 |
| **F1-Score** | 0.27 | 0.62 |
| **Precision** | 0.29 | 0.98 |
| **Recall** | 0.25 | 0.45 |


## Project Structure

```text
uc-binary-classifier/
├── data/                  # Ignored by git; contains raw and processed data
├── docs/                  # Academic artifacts (proposal, presentations)
│   ├── project_proposal.docx
│   └── project_slides.pptx
├── notebooks/             # Exploratory Jupyter notebooks
│   ├── preprocessing_final.ipynb
│   └── ResNet50_Final_Project_550.ipynb
├── src/                   # Executable source code
│   ├── data/              # Data generation and cleaning scripts
│   ├── models/            # PyTorch model definitions
│   └── utils/             
│       └── utils.py       # Core helper functions 
├── scripts/               # SLURM job submission scripts for Amarel
├── requirements.txt       # Environment dependencies
└── README.md              # Project documentation
```
