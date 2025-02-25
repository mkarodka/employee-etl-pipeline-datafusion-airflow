# employee-etl-pipeline-datafusion-airflow

# 🚀 ETL Data Pipeline in Google Cloud

## 📌 Overview
This project builds a **fully automated ETL pipeline** on **Google Cloud Platform (GCP)** using **Apache Airflow, Cloud Data Fusion, Google BigQuery, and Looker Studio**. The pipeline extracts employee data, applies transformations (masking sensitive data), and loads the processed data into BigQuery for visualization.

---

## 🎯 **Problem Statement**
The goal of this project is to:
1. **Extract** employee data from various sources.
2. **Mask sensitive information** (e.g., salary, passwords).
3. **Load data into BigQuery** for further analysis.
4. **Automate ETL workflows** using Apache Airflow.
5. **Visualize insights** with Looker Studio.

---

## 🏗 **Architecture**
<img width="263" alt="image" src="https://github.com/user-attachments/assets/c6a0a841-61ae-45dd-b384-ae2e9bf0be1f" />

### **🔧 Tech Stack**
<img width="233" alt="image" src="https://github.com/user-attachments/assets/2c7e4203-ad4c-4df1-bbb1-468fa5259770" />

- **Data Extraction** → Python (`extract.py`)
- **Storage** → Google Cloud Storage (GCS)
- **Data Processing** → Cloud Data Fusion
- **Orchestration** → Apache Airflow (Cloud Composer)
- **Data Warehouse** → Google BigQuery
- **Data Visualization** → Looker Studio
---
## ⚙️ **Workflow**
### **1️⃣ Data Extraction**
- The `extract.py` script uses **Faker** library to generate **synthetic employee data**.
- Saves data to **CSV** (`employee_data.csv`). 
- Uploads the file to a **Google Cloud Storage (GCS) bucket**.
- ![image](https://github.com/user-attachments/assets/79401d5f-9f39-4658-ad1c-d35b451823cf)

### **2️⃣ Data Transformation (Cloud Data Fusion)**
- Reads employee data from GCS.
- **Wrangler Transformation:**
  - **Masks salaries** for privacy.
  - **Encodes passwords** using Base64.
  - Cleans and standardizes data.
- Loads transformed data into **Google BigQuery**.
![image](https://github.com/user-attachments/assets/dd2cc1d5-7951-424d-9900-c3854cb19e77)
<img width="468" alt="image" src="https://github.com/user-attachments/assets/aa850842-8375-4fc1-8dcc-5794bc0cd31d" />

![image](https://github.com/user-attachments/assets/e69da14f-f398-49f1-9331-dfca2401f223)
<img width="332" alt="image" src="https://github.com/user-attachments/assets/17ca1099-9656-4dbd-8c2f-537c9f147e5b" />

<img width="468" alt="image" src="https://github.com/user-attachments/assets/aa8615a2-41ff-4430-83ba-20b5b5386f5e" />
<img width="326" alt="image" src="https://github.com/user-attachments/assets/ff6e7657-11b1-4378-b3d5-229e08ccc3ab" />
<img width="292" alt="image" src="https://github.com/user-attachments/assets/359d6cd8-6559-46e5-97ce-294a920e2231" />
<img width="410" alt="image" src="https://github.com/user-attachments/assets/23edc062-984a-4988-9e6e-374a29bc42e5" />

### **3️⃣ Data Orchestration (Apache Airflow)**
- DAG (`dag.py`) automates the ETL process:
  - **Extract data** using Python script.
  - **Upload data** to GCS.
  - **Trigger Cloud Data Fusion pipeline**.
  - **Monitor job execution**.
- Scheduled to **run daily**.

<img width="468" alt="image" src="https://github.com/user-attachments/assets/6d2d01e6-f956-4d2f-a0a1-0bec6dd060af" />


### **4️⃣ Data Analysis & Visualization**
- Data stored in **BigQuery**.
- Looker Studio connects to **BigQuery** for real-time **dashboard visualization**.
  https://lnkd.in/gKgzkybb
![image](https://github.com/user-attachments/assets/633dfa5c-d9c6-4a12-a9b7-b95751aaa80a)
---

## 🔧 **Setup & Deployment**
### **🔹 Prerequisites**
- Google Cloud Project with:
  - **Cloud Storage**
  - **BigQuery**
  - **Cloud Data Fusion**
  - **Cloud Composer (Airflow)**
- Python 3.x installed
- Google Cloud SDK installed

### **🔹 1. Clone Repository**
```sh
git clone https://github.com/mkarodka/Employee_Data_ETL_Pipeline.git
cd Employee_Data_ETL_Pipeline
```

### **🔹 2. Install Dependencies**
```sh
pip install -r requirements.txt
```

### **🔹 3. Set Up Google Cloud Authentication**
```sh
gcloud auth application-default login
gcloud config set project <your-project-id>
```

### **🔹 4. Create GCS Bucket**
```sh
gcloud storage buckets create bkt-employee-data-management --location=us-central1
```

### **🔹 5. Run Data Extraction**
```sh
python extract.py
```

### **🔹 6. Upload to Google Cloud Storage**
```sh
gcloud storage cp employee_data.csv gs://bkt-employee-data-management/
```

### **🔹 7. Deploy Cloud Data Fusion Pipeline**
1. **Go to Google Cloud Data Fusion**
2. **Create a pipeline** named **`etl-pipeline`**
3. **Ingest Data from GCS → Apply Transformations → Load into BigQuery**
4. **Deploy and run the pipeline.**

### **🔹 8. Start Airflow DAG**
- Upload `dag.py` to Airflow DAGs folder.
- **Trigger DAG manually**:
```sh
airflow dags trigger employee_data
```
- **Monitor in Airflow UI.**

---

## **🚀 Next Steps**
- **Optimize pipeline** for performance.
- **Add real-time data ingestion** using Pub/Sub.
- **Implement data quality checks**.

---

## **🏆 Key Learnings**
✅ Python (Faker, GCS SDK)  
✅ Google Cloud Storage (GCS)  
✅ Apache Airflow (Cloud Composer)  
✅ Cloud Data Fusion (Wrangler, Pipelines)  
✅ Google BigQuery  
✅ Looker Studio for Visualization  

---

## **🤝 Contributing**
Feel free to **fork** the repo, **submit PRs**, or **open issues**.

```sh
git checkout -b feature-branch
git commit -m "Add feature"
git push origin feature-branch
```
---

## **📞 Contact**
For questions, reach out via:
- **Email:** mugdhakarodkar0819@gmail.com  
- **LinkedIn:** [Mugdha Karodkar](https://www.linkedin.com/in/mugdha-karodkar)  

