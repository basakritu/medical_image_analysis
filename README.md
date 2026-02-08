# Multi-View Radiomics for Skin Lesion Classification
An End-to-End Machine Learning Pipeline for Diagnostic Support

## 🔬 Project Overview
This repository contains a comprehensive research pipeline designed to classify skin lesions from the HAM10000 dataset. By combining clinical metadata with high-dimensional Radiomics features (extracted from both the lesion core and the perilesional boundary), the project achieves a nuanced understanding of tumor morphology and its surrounding microenvironment.

## 🚀 Key Analytical Innovations
This project goes beyond standard "out-of-the-box" modeling by implementing custom quality control and feature engineering 

### steps:
Hollow-Core Detection 
### Logic:
A custom morphological filter that identifies and excludes "thin" or fragmented masks that fail to provide stable textural signals after a $50 \times 50$ pixel erosion.

Perilesional Ring Analysis: Developed a "Ring" mask generation script to capture features at the lesion boundary, where critical biological interactions often occur.
Data Integrity Audits: Automated scripts to detect null values, zero-inflation, and near-zero variance features to ensure model robustness.
Leakage Prevention: Metadata cleaning that strictly maintains a "one-lesion-per-record" rule, preventing the model from over-fitting on multiple images of the same patient.

## 📂 Repository StructurePlaintext: notebooks/
 1. metadata_rf.ipynb     # Feature extraction, cleaning, and RF modeling
 2. image_analysis_rf.ipynb   # Morphological processing & mask generation
data/hollow_core_indices.txt   # Audit trail of excluded outliers
requirements.txt              # Environment dependencies
README.md                     # Project documentation

## 🛠️ Installation & SetupClone the repository:Bashgit clone https://github.com/basakritu/skin-lesion-radiomics.git

Install dependencies: Bash pip install -r requirements.txt

Data Note: Due to size constraints, the raw HAM10000 dataset is not included. Please download the images and segmentations from [Harvard Dataverse] and place them in the ../dataset/ directory.

## 📊 Evaluation & Results
The model is evaluated using a Stratified K-Fold approach to account for class imbalance. Key metrics focused on include:F1-Score: To balance precision and recall across rare classes (e.g., Melanoma).Feature Importance: Identifying which radiomics textures (e.g., Entropy, Sphericity) are most predictive of malignancy.

## 🛠 Technologies UsedImaging
OpenCV, SimpleITK, PILFeature Extraction: PyRadiomicsData Science: Pandas, NumPy, Scikit-LearnVisualization: Matplotlib, SeabornImbalance Handling: Imbalanced-Learn (SMOTE)
