# 🧠 Glaucoma Detection Pipeline using Retinal Fundus Images

## 📌 Overview
This project presents an end-to-end glaucoma detection system based on retinal fundus images using a **Quality-Guided Hybrid Ensemble Learning approach**. The pipeline integrates deep learning, clinical feature extraction, and statistical validation to ensure both high performance and clinical relevance.

The system is designed not only for accurate classification but also for **interpretability, reliability, and real-world applicability in healthcare settings**.

---

## 🎯 Objectives
- Detect Glaucomatous Optic Neuropathy (GON) from fundus images
- Incorporate clinical features (Cup-to-Disc Ratio / CDR)
- Improve robustness using image quality-aware processing
- Provide explainable and uncertainty-aware predictions
- Simulate real-world clinical scenarios using patient-level aggregation

---

## 📂 Project Structure
Glaucoma-Detection-Pipeline/
│
├── Glaucoma Detection Pipeline/
│ └── [IDSC]_D4.ipynb
│
├── data/
│ └── README.txt
│
├── models/
│ ├── best_gradcam_model.pth
│ ├── mlp_model.pth
│ ├── xgb_model.json
│ └── ensemble_config.json
│
├── results/
│ ├── 01_EDA/
│ ├── 02_Preprocessing/
│ ├── 03_Segmentation/
│ ├── 04_Feature/
│ ├── 05_Model/
│ ├── 06_Explainability/
│ ├── 07_Clinical/
│
└── README.md


---

## 📊 Exploratory Data Analysis

### Label Distribution
![Label Distribution](results/01_EDA/eda_label_distribution.png)

The dataset shows class imbalance, with GON+ (~73%) dominating GON- (~27%). This imbalance is considered during model training to avoid bias toward the majority class.

---

### Patient Distribution
![Patient Distribution](results/01_EDA/eda_patient_distribution.png)

Each patient has multiple images (typically 2–4), highlighting the importance of **patient-level aggregation** to prevent overfitting and data leakage.

---

### Quality Score Distribution
![Quality Score](results/01_EDA/eda_quality_score.png)

Most images have quality scores above the acceptable threshold (QS > 3). Image quality is later used as a weighting factor in prediction aggregation.

---

### Sample Fundus Images
![Sample Images](results/01_EDA/eda_sample_images.png)

The dataset contains diverse retinal conditions, showing clear variation between GON+ and GON- cases.

---

## 🧪 Preprocessing & Augmentation

### Data Augmentation
![Augmentation](results/02_Preprocessing/preprocessing_augmentation.png)

To improve model robustness, several augmentation techniques are applied:
- Horizontal/vertical flipping
- Rotation
- Brightness adjustment
- CLAHE (Contrast Limited Adaptive Histogram Equalization)

These techniques help the model generalize better to real-world variations.

---

## 🧠 Segmentation & Clinical Feature Extraction

### Optic Disc and Cup Segmentation
![Segmentation](results/03_Segmentation/segmentation_cdr_visualization.png)

Segmentation is performed to identify the optic disc and optic cup regions. These regions are essential for computing clinical indicators.

---

### Cup-to-Disc Ratio (CDR) Distribution
![CDR Distribution](results/03_Segmentation/cdr_distribution.png)

CDR is a key clinical feature for glaucoma diagnosis. The distribution shows that GON+ cases tend to have significantly higher CDR values.

---

## 📈 Feature Representation

### PCA & t-SNE Visualization
![Feature Space](results/04_Feature/feature_space_visualization.png)

Feature space visualization shows partial separation between GON+ and GON-, indicating that the extracted features are informative but the problem remains complex.

---

## 🤖 Model Training & Evaluation

### Learning Curve
![Learning Curve](results/05_Model/mlp_learning_curve.png)

The model demonstrates stable convergence, with decreasing training loss and slight validation gap, indicating mild overfitting.

---

### Model Evaluation (ROC & Confusion Matrix)
![Evaluation](results/05_Model/model_evaluation.png)

The model achieves strong performance:
- AUC ≈ 0.98  
- F1-score > 0.96  

The hybrid ensemble model outperforms individual models.

---

### Statistical Validation
![Statistical Validation](results/05_Model/statistical_validation.png)

Bootstrap confidence intervals and DeLong tests confirm that the model performance is statistically stable and reliable.

---

## 🔍 Explainability & Uncertainty

### Grad-CAM Visualization
![GradCAM](results/06_Explainability/gradcam_visualization.png)

Grad-CAM highlights that the model focuses on clinically relevant regions (optic disc and cup), improving interpretability.

---

### Uncertainty Estimation (MC Dropout)
![Uncertainty](results/06_Explainability/uncertainty_estimation.png)

Monte Carlo Dropout is used to estimate prediction uncertainty. High-confidence predictions show low variance, indicating model reliability.

---

## 🏥 Clinical-Oriented Evaluation

### Threshold Optimization
![Threshold](results/07_Clinical/threshold_optimization.png)

The optimal threshold is set around **0.40**, balancing sensitivity and specificity while prioritizing minimizing false negatives.

---

### Patient-Level Aggregation
![Patient Level](results/07_Clinical/patient_level_aggregation.png)

Patient-level prediction using quality-weighted aggregation improves performance:
- AUC ≈ 0.983  
- F1-score ≈ 0.985  

This approach better reflects real-world clinical usage.

---

## 🚀 Key Contributions

- Hybrid pipeline combining deep learning and clinical features (CDR)
- Quality-aware modeling using image quality scores
- Ensemble learning (CNN + MLP + XGBoost)
- Explainable AI using Grad-CAM
- Uncertainty estimation using Monte Carlo Dropout
- Patient-level prediction strategy
- Statistical validation using bootstrap and DeLong test

---

## 📌 Conclusion

This project demonstrates that combining deep learning with clinical features and quality-aware modeling can produce a **robust, interpretable, and clinically relevant glaucoma detection system**.

The proposed approach is suitable as a foundation for a **Clinical Decision Support System (CDSS)** in ophthalmology.

---

## 📎 Dataset

Dataset used:
**Hillel Yaffe Glaucoma Dataset (HYGD)**

Due to licensing restrictions, the dataset is not included in this repository.  
Please access it via:
https://physionet.org/content/hillel-yaffe-glaucoma-dataset/1.0.0/

---

## ⚙️ Requirements
torch
torchvision
numpy
pandas
matplotlib
seaborn
scikit-learn
xgboost
opencv-python

---

## 👨‍💻 Author

- Muhammad Habib Nur Aiman, Nazril Ravi Pratama, Horasio Nissi Immanuel  
- Universitas Negeri Surabaya  

---

## 🏆 Competition

International Data Science Competition (IDSC)
