#  Landslide Automation Segmentation using Deep Learning  

This project develops and evaluates **five deep learning architectures** —  
**U-Net**, **ResU-Net**, **Attention U-Net**, **Attention ResU-Net**, and **ASDMS U-Net** —  
for **landslide detection and segmentation** using **PlanetScope AnalyticMS 8-band satellite imagery**.  

The models are **trained on 2024 satellite data** and **tested on 2022 imagery** to evaluate  
**cross-year generalization**, a crucial benchmark for **temporal transferability** in  
Earth observation and geohazard mapping.  
---
## Project Title
*LTS-Net: A Temporal Transfer Learning Framework for Cross-Year Landslide Segmentation**  
**Supervised by:**  
*Dr. Yunus Ali Pulpadan* — Assistant Professor, Earth and Environmental Science (EES), IISER Mohali  
**Developed by:**  
*Atrii Roy* — 3rd Year BS (Hons.) Data Science & Artificial Intelligence, IIT Guwahati  
---
---

##  Dataset Context

| Year | Dataset | Imagery Type | Description |
|------|----------|--------------|--------------|
| **2024 (Train)** | `20241110_053942_45_24f7_3B_AnalyticMS_SR_8b_clip.tif` | PlanetScope 3B SR | Used for model training |
| **2022 (Test)**  | `20220503_050008_52_2474_3B_AnalyticMS_8b_clip.tif` | PlanetScope 3B AnalyticMS | Used for cross-year validation |

 *These metrics reflect each model’s ability to detect landslides under temporal domain shift, validating the potential for cross-year transfer learning in Earth observation.*

---

##  Model Architectures

| Model | Description |
|--------|--------------|
| **U-Net** | Standard encoder–decoder CNN for pixel-wise segmentation. |
| **ResU-Net** | Adds residual connections to improve gradient stability and robustness. |
| **Attention U-Net** | Introduces attention gates to focus on salient features. |
| **Attention ResU-Net** | Combines residual and attention mechanisms for enhanced precision. |
| **ASDMS U-Net** | Augmented U-Net variant designed for terrain-change and landslide segmentation. |

---

##  Experimental Setup

| Parameter | Value |
|------------|--------|
| **Training Year** | 2024 |
| **Testing Year** | 2022 |
| **Epochs** | 50 |
| **Optimizer** | Adam |
| **Learning Rate** | 5e-4 |
| **Loss Function** | Binary Cross-Entropy |
| **Patch Size** | 256 × 256 |
| **Batch Size** | 8 |
| **Validation Split** | 20% |

---

##  Objective

To evaluate whether deep segmentation networks trained on **recent imagery (2024)**  
can **generalize effectively to past imagery (2022)** of the same region —  
serving as a benchmark for **temporal domain adaptation** in geospatial deep learning.

---

##  Evaluation Metrics

Each model’s performance on the 2022 dataset is measured using:

- **Accuracy**  
- **Precision**  
- **Recall**  
- **F1-Score**  
- **Intersection over Union (IoU)**  
- **Dice Coefficient**

---

## 📈 Cross-Year Performance Summary (Train: 2024 → Test: 2022)

This experiment assesses the **temporal generalization** of five architectures trained on the 2024 Villangad dataset and tested on 2022 imagery.  

| Model                  | Accuracy   | Precision  | Recall     | F1-Score   | IoU        | Dice       |
| ---------------------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- |
| **U-Net**              | 0.9734     | 0.7928     | 0.8517     | 0.8212     | 0.6967     | 0.8212     |
| **ResU-Net**           | **0.9779** | **0.9132** | 0.7643     | **0.8321** | **0.7125** | **0.8321** |
| **Attention U-Net**    | 0.9688     | 0.7621     | 0.8199     | 0.7899     | 0.6528     | 0.7899     |
| **Attention ResU-Net** | 0.9675     | 0.7235     | **0.8834** | 0.7955     | 0.6604     | 0.7955     |
| **ASDMS U-Net**        | 0.9748     | 0.8318     | 0.8124     | 0.8220     | 0.6977     | 0.8220     |

---

###  Interpretation

- **🏆 Best Overall → `ResU-Net`**  
  Achieves the highest accuracy (0.9779) and F1-score (0.8321).  
  Residual connections strengthen temporal robustness.

- **🛰️ Highest Recall → `Attention ResU-Net`**  
  Best at identifying landslide regions (recall = 0.8834), though slightly lower precision.

- **⚖️ Most Balanced → `ASDMS U-Net`**  
  Maintains a consistent trade-off between precision and recall.

- **🔹 Baseline → `U-Net`**  
  Despite simplicity, shows excellent generalization (F1 = 0.8212).

- **🔻 Least Robust → `Attention U-Net`**  
  Slightly overfits spatial patterns in the training year, leading to weaker domain transfer.

---

###  Key Insights

- Residual and hybrid architectures outperform plain attention models under **cross-temporal conditions**.  
- Attention-based networks yield higher recall, useful for **hazard sensitivity mapping**.  
- Consistent IoU (~0.65–0.71) confirms stable segmentation quality even under domain shifts.

---

##  Visualization Outputs

Each model generates the following evaluation plots and overlays:

-  **Confusion Matrix Heatmaps** — Class-wise accuracy  
-  **Radar Plots** — Multi-metric performance visualization  
-  **Bar Charts** — Comparison of model accuracies and F1-scores  
-  **Prediction Maps** — Landslide masks overlaid on 2022 imagery  

Output Files include:
- `metrics_summary_2022.csv`
- `*_confusion.png`
- `*_radar.png`
- `barplot_metrics_2022.png`

---
## How to Run
### Install Dependencies 
pip install -r requirements.txt

