# Intrusion Detection Using Machine Learning
---

## 📖 Overview

This repository contains a **Jupyter notebook** that demonstrates an end‑to‑end workflow for detecting network intrusions with machine‑learning techniques. The notebook walks through:

1. **Data acquisition** – loading the *Network Intrusion* dataset from Kaggle.
2. **Pre‑processing** – cleaning, deduplication, handling missing values, column renaming, and label simplification.
3. **Feature engineering** – optional scaling and encoding of categorical columns.
4. **Balancing** – undersampling the majority class to mitigate class imbalance.
5. **Model training & evaluation** – a baseline binary classifier (e.g., Logistic Regression, Random Forest) with performance metrics.

All steps are fully reproducible and documented inside the notebook `Intrusion_Detection_Using_Machine_Learning (2).ipynb`.

---

## 📂 Repository Structure

```
├── Intrusion_Detection_Using_Machine_Learning (2).ipynb   # Main notebook
├── README.md                                            # This file
└── requirements.txt                                     # Python dependencies
```

---

## 🗂️ Dataset

The notebook uses the **Network Intrusion Dataset** from Kaggle (`chethuhn/network-intrusion-dataset`).
Key characteristics:

| Feature Count | Rows (after cleaning) | Classes |
|---------------|----------------------|---------|
| 79            | 2,522,009            | 2 (Normal / Attack) |

The raw CSV files are downloaded automatically by the notebook using `kagglehub`.

---

## 🛠️ Pre‑processing Summary

| Step | Description |
|------|-------------|
| **Mount Drive** | Connects Google Colab to your Drive (if running on Colab). |
| **Load CSVs** | Reads all CSV files, concatenates them into a single `DataFrame`. |
| **Drop duplicates & NaNs** | `df.drop_duplicates(inplace=True)` and `df.dropna(inplace=True)`. |
| **Rename columns** | Removes leading spaces (`' Label' → 'Label'`). |
| **Normalize dash characters** | Replaces `–` and `—` with `-`. |
| **Simplify attack labels** | Merges all web‑attack sub‑categories into a single `Web Attack`. |
| **Binary label conversion** | `Label` → `Normal` (0) or `Attack` (1). |
| **Feature selection** | Drops non‑informative columns (`Flow ID`, `Source IP`, …). |
| **Encode categorical columns** | `LabelEncoder` applied to any remaining `object` columns. |
| **Handle infinities / NaNs** | Replaces `inf` with `NaN`, then imputes missing values using `SimpleImputer(strategy='mean')`. |
| **Class balancing** | Undersamples the majority class to a 0.7 : 1 ratio using `RandomUnderSampler`. |

---

## 📊 Results

After the preprocessing pipeline, the dataset contains:

```
After cleaning: (2,522,009, 79)
Label distribution:
Normal    2,096,134
Attack      425,875
```

The notebook proceeds to split the data, train a model, and prints evaluation metrics such as:

* **Accuracy**
* **Precision / Recall**
* **F1‑score**
* **Confusion matrix**

> **Note:** The exact numbers depend on the chosen classifier and random seed. The notebook includes a section where you can swap in any scikit‑learn model (e.g., `LogisticRegression`, `RandomForestClassifier`, `XGBoost`) and instantly see the updated metrics.

---

## 🚀 How to Run

1. **Clone the repository**

   ```bash
   git clone https://github.com/yourusername/intrusion-detection-ml.git
   cd intrusion-detection-ml
   ```

2. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

   *If you are using Google Colab, the notebook will install missing packages automatically.*

3. **Open the notebook**

   ```bash
   jupyter notebook "Intrusion_Detection_Using_Machine_Learning (2).ipynb"
   ```

4. **Execute cells sequentially** – the notebook will download the dataset, preprocess it, and train the model.

---

## 📧 Contact

If you have questions, suggestions, or would like to collaborate, feel free to reach out:

- **Email:** `workflow.raza@gmail.com`
- **GitHub Issues:** Open an issue in this repository for bug reports or feature requests.

---

## 🙏 Acknowledgements

- **Kaggle** – for providing the *Network Intrusion* dataset.
- **scikit‑learn**, **imbalanced‑learn**, **pandas**, **numpy** – core libraries used throughout the notebook.

---

*Happy hacking! 🚀*
