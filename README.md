# Network Intrusion Detection using K-Nearest Neighbors (KNN)

A supervised machine learning project aimed at identifying and classifying network security anomalies. Utilizing the benchmark **KDD Cup '99 dataset**, this project builds a predictive pipeline to determine whether network connection attempts are standard operational traffic (`normal.`) or unauthorized malicious intrusions.

---

## 📌 Project Overview
Network intrusion detection systems (NIDS) are critical foundations of modern cybersecurity infrastructures. This project implements a complete data-science pipeline, starting with processing specialized network log flags, executing category feature mappings, running multidimensional numerical scalers, and applying a $K$-Nearest Neighbors classifier ($\text{KNN}$) to accurately segment connection threats.

## 📊 Dataset: KDD Cup '99 (`kddcup.data.corrected`)
The project utilizes the corrected variant of the KDD Cup 1999 dataset, tracking simulated military network environments subjected to a variety of cyberattacks. Core features handled in this script include:
* **Protocol Type:** The network communication layout used (e.g., `tcp`, `udp`, `icmp`).
* **Service:** The destination network service (e.g., `http`, `smtp`, `ftp`).
* **Flag:** The connection status status flag (e.g., `SF`, `S0`).
* **Target Label (`normal.`):** The connection categorization (indicating either standard access or a specific signature of a malicious exploit/attack).

---

## 🛠️ Pipeline Architecture & Implementation

### 1. Exploratory Analysis & Preprocessing
* **Integrity Auditing:** Missing values are systematically tracked using conditional aggregation (`.isnull().sum()`), and structural duplication maps are evaluated with `.duplicated().sum()`.
* **Label Encoding:** Multi-class categorical variables (`normal.`, `tcp`, `http`, `SF`) are converted into standardized integers using `scikit-learn`'s `LabelEncoder` to make them compatible with distance-based models.

### 2. Feature Engineering & Scaling
* **Data Splitting:** Data arrays are separated into features ($X$) and target classifications ($y$), then partitioned into training and validation folds ($80\%$ train, $20\%$ test).
* **Z-Score Normalization:** Features are transformed via `StandardScaler`. The training arrays are fitted and transformed (`.fit_transform()`), while test vectors are exclusively transformed (`.transform()`) to completely prevent data leakage.

### 3. Machine Learning Modeling
* **Algorithm Selection:** A **K-Nearest Neighbors (KNN)** model is instantiated with `n_neighbors=5`.
* **Training & Execution:** The model evaluates feature proximities via supervised multi-dimensional geometric distance to predict incoming sample classes (`KNNclassifier.predict(X_test)`).

---

## 💻 Tech Stack & Tooling
* **Language:** Python 3.x
* **Data Manipulation:** `pandas`, `numpy`
* **Machine Learning Framework:** `scikit-learn`
* **Environment:** Jupyter Notebook

## 🚀 Getting Started
1. **Clone the repository:**
   ```bash
   git clone [https://github.com/your-username/network-intrusion-detection-knn.git](https://github.com/your-username/network-intrusion-detection-knn.git)
   cd network-intrusion-detection-knn
