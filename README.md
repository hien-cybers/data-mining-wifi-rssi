# 📍 WiFi Indoor Localization using Machine Learning

## 📖 Project Overview
This Data Mining project applies both supervised and unsupervised Machine Learning algorithms to predict a device's location within an indoor space (Indoor Positioning). Based on Received Signal Strength Indicator (RSSI) data collected from 7 different WiFi routers, the model can accurately classify which of the 4 designated rooms the device is currently located in.

## 📊 Dataset
*   **Source:** D08 - WiFi Localization Dataset.
*   **Size:** 2000 data samples (corresponding to 4 rooms, ~500 samples per room).
*   **Features:** 7 continuous variables representing the signal strength (RSSI) measured by a mobile device.
*   **Target (Label):** Categorical variable ranging from 1 to 4, representing the 4 rooms. The dataset is perfectly balanced.

## 🛠 Technologies & Libraries
*   **Language:** Python 3.1x
*   **Environment:** Jupyter Notebook (Visual Studio Code)
*   **Data Manipulation & Visualization:** `pandas`, `numpy`, `matplotlib`, `seaborn`
*   **Machine Learning:** `scikit-learn` (PCA, KNN, Random Forest, SVM, K-Means, DBSCAN)

## 🚀 Analytical Pipeline & Results
The project is implemented through 4 core phases:

### 1. Exploratory Data Analysis (EDA)
Loaded the dataset, inspected the data structure, and extracted basic descriptive statistics (Min, Max, Mean) to evaluate signal noise and data distribution.

### 2. Dimensionality Reduction
Utilized **PCA (Principal Component Analysis)** to compress the data from a 7-dimensional space (7 Routers) down to 2 dimensions (2D). The visualization shows that the data points form 4 relatively distinct clusters, demonstrating the feasibility of using Machine Learning for this classification task.

### 3. Classification
Performed data standardization (`StandardScaler`) and utilized `GridSearchCV` combined with `10-Fold Cross Validation` to fine-tune hyperparameters for 3 machine learning models. 
🏆 **F-Score (Macro) Results:**
*   **K-Nearest Neighbors (KNN):** `98.75%` (Best parameters: `n_neighbors=3`, `weights='uniform'`) - *Most optimal model*
*   **Support Vector Machine (SVM):** `98.35%` 
*   **Random Forest:** `98.30%` 

### 4. Clustering
Experimented with unsupervised machine learning algorithms to automatically group WiFi signals without using ground-truth labels.
*   **K-Means (k=4):** Performed effectively with an Adjusted Rand Index (ARI) score of **~0.81**, indicating a high similarity to the actual labels.
*   **DBSCAN:** Struggled to cluster effectively with the default density configuration due to the uneven distribution of the signal range, proving that K-Means is more stable for this specific data structure.

## ⚙️ Installation & Setup
1. Clone this repository to your local machine:
      ```bash
      git clone https://github.com/hien-cybers/data-mining-wifi-rssi
   Install the required libraries:
      ```bash
      pip install pandas numpy matplotlib seaborn scikit-learn
 2 Open the *.ipynb file and execute "Run All Cells" to view the entire pipeline and visualizations.
