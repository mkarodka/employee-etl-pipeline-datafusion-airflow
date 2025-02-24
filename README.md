# employee-etl-pipeline-datafusion-airflow

# 🚀 ETL Data Pipeline in Google Cloud

## 📌 Overview
This project builds a **fully automated ETL pipeline** on **Google Cloud Platform (GCP)** using **Apache Airflow, Cloud Data Fusion, Google BigQuery, and Looker Studio**. The pipeline extracts employee data, applies transformations (masking sensitive data), and loads the processed data into BigQuery for visualization.

---

## 📂 **Project Structure**
📁 Employee_Data_ETL_Pipeline │── 📜 dag.py # Apache Airflow DAG to orchestrate ETL workflow │── 📜 extract.py # Python script to generate and upload employee data │── 📜 employee_data.csv # Sample employee dataset │── 📜 Architecture_Diagram.drawio # Architecture diagram (editable) │── 📜 Project_Notes.docx # Detailed project documentation │── 📂 dags # Airflow DAGs directory │── 📂 scripts # Python scripts for extraction & transformation │── 📂 data # Data storage folder │── 📂 logs # Execution logs │── 📂 gcs_bucket # GCS bucket for raw data storage │──


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
![ETL Pipeline Architecture](Architecture_Diagram.drawio)

### **🔧 Tech Stack**
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

### **2️⃣ Data Transformation (Cloud Data Fusion)**
- Reads employee data from GCS.
- **Wrangler Transformation:**
  - **Masks salaries** for privacy.
  - **Encodes passwords** using Base64.
  - Cleans and standardizes data.
- Loads transformed data into **Google BigQuery**.

### **3️⃣ Data Orchestration (Apache Airflow)**
- DAG (`dag.py`) automates the ETL process:
  - **Extract data** using Python script.
  - **Upload data** to GCS.
  - **Trigger Cloud Data Fusion pipeline**.
  - **Monitor job execution**.
- Scheduled to **run daily**.

### **4️⃣ Data Analysis & Visualization**
- Data stored in **BigQuery**.
- Looker Studio connects to **BigQuery** for real-time **dashboard visualization**.

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
git clone https://github.com/yourusername/Employee_Data_ETL_Pipeline.git
cd Employee_Data_ETL_Pipeline

🔹 2. Install Dependencies
sh
Copy
Edit
pip install -r requirements.txt
🔹 3. Set Up Google Cloud Authentication
sh
Copy
Edit
gcloud auth application-default login
gcloud config set project <your-project-id>
🔹 4. Create GCS Bucket
sh
Copy
Edit
gcloud storage buckets create bkt-employee-data-management --location=us-central1
🔹 5. Run Data Extraction
sh
Copy
Edit
python extract.py
🔹 6. Upload to Google Cloud Storage
sh
Copy
Edit
gcloud storage cp employee_data.csv gs://bkt-employee-data-management/
🔹 7. Deploy Cloud Data Fusion Pipeline
Go to Google Cloud Data Fusion
Create a pipeline named etl-pipeline
Ingest Data from GCS → Apply Transformations → Load into BigQuery
Deploy and run pipeline.
🔹 8. Start Airflow DAG
Upload dag.py to Airflow DAGs folder.
Trigger DAG manually:
sh
Copy
Edit
airflow dags trigger employee_data
Monitor in Airflow UI.
🛠 Troubleshooting
1. Airflow DAG Fails (404 Data Fusion Error)
Cause: Pipeline name mismatch or missing pipeline.
✅ Fix:

Ensure pipeline name in DAG matches Data Fusion.
Check pipeline logs in Cloud Data Fusion.
2. Data Not Showing in BigQuery
Cause: Data Fusion pipeline failed.
✅ Fix:

Go to Data Fusion UI and check logs.
Ensure BigQuery dataset exists.
3. Looker Studio Not Connecting
Cause: Missing permissions for BigQuery.
✅ Fix:

Grant BigQuery Data Viewer role in IAM.
📊 Visualization Dashboard
Looker Studio connects to BigQuery to create dashboards.
Displays Employee Data Insights.
Accessible in Google Data Studio.
🚀 Next Steps
Optimize pipeline for performance.
Add real-time data ingestion using Pub/Sub.
Implement data quality checks.
🏆 Key Learnings
✅ Python (Faker, GCS SDK)
✅ Google Cloud Storage (GCS)
✅ Apache Airflow (Cloud Composer)
✅ Cloud Data Fusion (Wrangler, Pipelines)
✅ Google BigQuery
✅ Looker Studio for Visualization

🤝 Contributing
Feel free to fork the repo, submit PRs, or open issues.

sh
Copy
Edit
git checkout -b feature-branch
git commit -m "Add feature"
git push origin feature-branch
📜 License
This project is licensed under the MIT License.

📞 Contact
For questions, reach out via:

Email: mugdhakarodkar0819@gmail.com
LinkedIn: Your Profile
