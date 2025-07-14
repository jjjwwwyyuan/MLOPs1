# 🏋️‍♀️ MLOps HW2: Feature Store & ML Pipeline with Feast

This project demonstrates the use of **Feast** (Feature Store) integrated with a complete ML pipeline using data from `athletes.csv`. It includes feature versioning, model training, performance comparison, and carbon emissions tracking.

---

## 📁 Project Structure

├── MLOps HW2.ipynb # Main notebook (Colab-compatible)
├── athletes_data.zip # Compressed dataset (replace athletes.csv)
├── feature_repo/
│ ├── feature_store.yaml # Feast configuration
│ └── feature_definition.py # FeatureView definitions (v1 and v2)
└── README.md # This file

--

## ⚙️ Steps Performed

1. **Data Cleaning & Outlier Removal**
2. **Feature Engineering & Versioning**
    - `v1`: Basic features — age, height, weight, gender, region
    - `v2`: Engineered BMI with reduced feature set
3. **Feature Store Setup**
    - Initialized via `feast init`
    - Feature definitions created and applied via `feast apply`
4. **Model Training**
    - 4 experiments: `v1_hp1`, `v1_hp2`, `v2_hp1`, `v2_hp2`
    - Same algorithm (e.g. Linear Regression), 2 hyperparameter sets
5. **Evaluation**
    - Metrics: RMSE, R² Score
    - Visuals: Predicted vs. Actual plots
6. **Carbon Emissions Tracking**
    - Used `codecarbon` to record energy usage during training

---

## 📦 Dataset Handling (IMPORTANT)

The original `athletes.csv` exceeds GitHub's 25MB upload limit.

### 🔽 Option 1: Download from Cloud  
[Download athletes.csv](https://your-link-to-cloud-storage.com) and place it in your working directory.

### 💡 Option 2: Use Compressed Version  
If using `athletes_data.zip`, extract it or read it directly using:

```python
import pandas as pd
import zipfile

with zipfile.ZipFile("athletes_data.zip") as z:
    with z.open("athletes.csv") as f:
        df = pd.read_csv(f)
