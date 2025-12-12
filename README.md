# Healthcare-Data-Prediction-using-Hive-2025-

```markdown
# Healthcare Data Analysis & Prediction Using Apache Hive

This project demonstrates a complete Big Data analytics workflow using **Apache Hive** on **Cloudera (Hadoop ecosystem)**.  
A synthetic healthcare dataset (1000 records) is used to perform **data cleaning, feature engineering, analytical queries, and prediction** using HiveQL.

The project shows how Hive can be used not only for querying large datasets but also for implementing **simple machine learning logic**, such as majority-rule and Naive Bayes–style classification.

---

## 📁 Project Structure

```

healthcare-hive/
│
├── data/
│   └── healthcare_data_sample.csv          # small sample for testing
│
├── hql/
│   ├── create_table_and_load.hql           # DDL + load into HDFS/Hive
│   ├── queries_analysis.hql                # 10 analysis queries
│   ├── naive_bayes_insurance_final.hql     # prediction model
│   └── nb_evaluation_insurance.hql         # evaluation metrics
│
├── screenshots/                            # screenshots showing results
├── report/
│   └── BDA_project_report.docx
│
├── README.md
├── LICENSE
└── .gitignore

````

> **Note:** Only a small sample CSV is included.  
> The full dataset (1000 rows) should be placed manually into HDFS.

---

## 🧠 Project Overview

This project performs:

### ✔ Data Preprocessing  
- Created a Hive-managed table for healthcare data  
- Loaded data from HDFS  
- Applied transformations (AgeGroup, Cost_Bucket, Payment categories)

### ✔ Data Analysis  
10+ analytical HiveQL queries, including:  
- Most common diseases  
- State-wise patient distribution  
- Insurance distribution  
- Cost-based analysis  
- Gender/age segmentation  

### ✔ Prediction Model in Hive  
Two prediction approaches:

1. **Majority-Rule Classifier (Simple Model)**  
   - Predicts insurance status (`Yes/No`) based on the most frequent label for each `Payment_Method`.

2. **Naive Bayes–Inspired Hive Model (Advanced)**  
   - Computes prior probabilities  
   - Computes likelihoods for features  
   - Uses log-probability scoring with Laplace smoothing  
   - Generates predicted insurance labels  

### ✔ Evaluation  
Using HiveQL:  
- Confusion Matrix  
- Accuracy (achieved **~54.75%**)  
- Class-wise performance metrics  

---

## 🛠️ Technologies Used

| Technology | Purpose |
|-----------|---------|
| **Apache Hive** | Data warehouse querying & prediction logic |
| **Hadoop HDFS** | Data storage |
| **Cloudera VM** | Execution environment |
| **HiveQL** | Querying, transformation, model logic |
| **MapReduce (internal)** | Hive execution engine |
| **Linux Terminal** | Data loading & Hive operation |

---

## 📥 Setup Instructions (Cloudera / Hadoop VM)

### 1️⃣ Place dataset in HDFS
```bash
hdfs dfs -mkdir -p /healthcare
hdfs dfs -put -f data/healthcare_data_sample.csv /healthcare/
````

### 2️⃣ Create table & load data

```bash
hive -f hql/create_table_and_load.hql
```

### 3️⃣ Run analysis queries

```bash
hive -f hql/queries_analysis.hql
```

### 4️⃣ Run prediction model

```bash
hive -f hql/naive_bayes_insurance_final.hql
```

### 5️⃣ Run evaluation metrics

```bash
hive -f hql/nb_evaluation_insurance.hql
```

---

## 📊 Sample Output (From Confusion Matrix)

| Actual → Predicted | Yes | No  |
| ------------------ | --- | --- |
| **Yes**            | 154 | 310 |
| **No**             | 143 | 393 |

**Accuracy:** ~54.75%
**Interpretation:** Majority-rule classifier provides a baseline; better results require additional features or ML frameworks (Spark ML, Python, etc.)

---

## 📝 Key Learning Outcomes

* Working with **Hive tables, partitions, and HDFS integration**
* Designing **HiveQL scripts** for analytics and aggregation
* Implementing **prediction logic inside Hive**
* Understanding confusion matrix, accuracy, and classification evaluation
* Exposure to **distributed computing** concepts

---

## 📄 License

This project uses the **MIT License**.
You can freely use or modify the code.

---
