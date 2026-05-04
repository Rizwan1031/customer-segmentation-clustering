# 🛍️ Customer Segmentation using K-Means Clustering

A machine learning project that segments marketing campaign customers into meaningful groups using K-Means clustering — enabling businesses to personalize marketing strategies based on customer behavior and income patterns.

---

## 📌 Project Overview

This project applies **unsupervised machine learning** to a real-world marketing dataset. By clustering customers based on their demographic and purchasing data, we can identify distinct customer groups and predict which segment a new customer belongs to.

> **First ML Project** — Built from scratch covering the full data science pipeline: cleaning → EDA → modeling → visualization → deployment.

---

## 📁 Project Structure

```
customer-segmentation/
│
├── data_cleaning.ipynb                # Step 1: Data preprocessing & cleaning
├── EDA.ipynb                          # Step 2: Exploratory Data Analysis
├── Modeling.ipynb                     # Step 3: K-Means clustering model
├── Visualization_and_Deployment.ipynb # Step 4: Visualization & Streamlit app
│
├── marketing_campaign.csv             # Original raw dataset
├── marketing_campaign_cleaned.csv     # Cleaned dataset (output of Step 1)
└── modeling_data.pkl                  # Saved model & data (output of Step 3)
```

---

## 📊 Dataset

**Source:** Marketing Campaign Dataset  
**Format:** Tab-separated CSV  
**Original Features (29 columns):**

| Category | Features |
|---|---|
| Demographics | `ID`, `Year_Birth`, `Education`, `Marital_Status`, `Income` |
| Household | `Kidhome`, `Teenhome` |
| Behavior | `Recency`, `Dt_Customer` |
| Spending | `MntWines`, `MntFruits`, `MntMeatProducts`, `MntFishProducts`, `MntSweetProducts`, `MntGoldProds` |
| Purchases | `NumDealsPurchases`, `NumWebPurchases`, `NumCatalogPurchases`, `NumStorePurchases` |
| Web Activity | `NumWebVisitsMonth` |
| Campaigns | `AcceptedCmp1–5`, `Response`, `Complain` |

---

## 🔧 Step-by-Step Pipeline

### 1️⃣ Data Cleaning (`data_cleaning.ipynb`)
- Loaded raw tab-separated dataset
- Removed duplicate rows
- Handled missing values — filled `Income` with **median**
- Dropped irrelevant/campaign-specific columns: `Complain`, `Response`, `AcceptedCmp1–5`
- Exported cleaned data to `marketing_campaign_cleaned.csv`

### 2️⃣ Exploratory Data Analysis (`EDA.ipynb`)
- Sorted data by Customer ID
- Visualized **Income distribution** (histogram + KDE)
- Analyzed **Income by Marital Status** (bar chart)
- Plotted **Income vs. Kidhome** and **Income vs. Teenhome** (scatter plots)
- Generated a **Correlation Heatmap** across all numeric features

### 3️⃣ Modeling (`Modeling.ipynb`)
- Selected only numeric features for clustering
- Applied **StandardScaler** for feature normalization
- Used the **Elbow Method** (WCSS for k = 1–10) to find optimal clusters
- Trained **KMeans with 5 clusters** on all scaled features
- Trained a second **KMeans** specifically on `Income` & `Recency` (for deployment)
- Evaluated with **Silhouette Score**
- Saved all model artifacts to `modeling_data.pkl`

### 4️⃣ Visualization & Deployment (`Visualization_and_Deployment.ipynb`)
- Loaded saved model artifacts from pickle file
- Visualized clusters with **color-coded scatter plots** and **cluster center markers (★)**
- Built a **Streamlit web app** for real-time prediction:
  - User inputs `Annual Income` and `Recency` via sliders
  - App predicts and displays the customer's cluster segment

---

## 🤖 Model Details

| Parameter | Value |
|---|---|
| Algorithm | K-Means Clustering |
| Number of Clusters | 5 |
| Feature Scaling | StandardScaler |
| Cluster Selection | Elbow Method (WCSS) |
| Evaluation Metric | Silhouette Score |
| Deployment Features | Income, Recency |
| Deployment Tool | Streamlit |

---

## 🚀 How to Run

### Prerequisites
```bash
pip install pandas scikit-learn matplotlib seaborn streamlit
```

### Run the Notebooks (in order)
```bash
jupyter notebook data_cleaning.ipynb
jupyter notebook EDA.ipynb
jupyter notebook Modeling.ipynb
jupyter notebook Visualization_and_Deployment.ipynb
```

### Run the Streamlit App
```bash
streamlit run app.py
```
> ⚠️ Extract the Streamlit code from `Visualization_and_Deployment.ipynb` into a separate `app.py` file before running.

---

## 📈 Results

- Customers are segmented into **5 distinct clusters** based on their spending habits, income, and purchase behavior
- The model enables businesses to **target specific customer groups** with tailored marketing strategies
- The **interactive Streamlit app** lets anyone predict a customer's segment using just their income and recency values

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| Python | Core programming language |
| Pandas | Data manipulation |
| Scikit-learn | K-Means, StandardScaler, Silhouette Score |
| Matplotlib & Seaborn | Data visualization |
| Pickle | Model serialization |
| Streamlit | Web app deployment |
| Jupyter Notebook | Development environment |

---

## 🌱 Future Improvements

- [ ] Try other clustering algorithms (DBSCAN, Agglomerative)
- [ ] Add more features to the Streamlit app (spending categories)
- [ ] Perform deeper feature engineering (age from `Year_Birth`, total spending)
- [ ] Add cluster profiling with descriptive statistics per segment
- [ ] Deploy the Streamlit app online (Streamlit Cloud / Hugging Face)

---

## 👨‍💻 Author

Made with ❤️ as a first machine learning project.  
*Every expert was once a beginner — keep building!*
