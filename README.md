# Walmart Sales Data Ingestion and Transformation in BigQuery using Airflow

This project demonstrates an ETL (Extract, Transform, Load) pipeline for ingesting and transforming Walmart sales data into Google BigQuery using Apache Airflow. The pipeline includes creating datasets and tables, loading data from Google Cloud Storage (GCS) to BigQuery, and performing an UPSERT operation using SQL MERGE.

## Project Architecture
![Project Architecture.png](https://github.com/Kaushik-Puttaswamy/Walmart-Sales-Data-Ingestion-and-Transformation-in-BigQuery-using-Airflow/blob/main/Project%20Architecture.png)


## Folder and File Structure
.

├── Data

│   ├── merchants.json

│   ├── merchants_2.json

│   ├── walmart_sales.json

│   ├── walmart_sales_2.json

│

├── GCP_Console_Walmart_Salesdata_Ingestion_Screenshot

│   ├── Airflow_dag_graph.png

│   ├── Merchant_table_preview.png

│   ├── Walmart_sales_stage_table.png

│   ├── Walmart_sales_target_table.png

│   ├── airflow_bigquery_dag_file_uploaded_in_airflow_bucket.png

│

├── airflow_bigquery_dag.py

├── Project architecture.png

## Key Features

1. Dataset and Table Creation:
	
	• A BigQuery dataset (walmart_dwh) is created to store Walmart sales data.
	
	• Three tables are created:
	  
	• merchants_tb: Contains merchant details.
	
  	• walmart_sales_stage: A staging table for Walmart sales data.
	
	• walmart_sales_tgt: A target table with consolidated sales data and merchant information.
	
2.	Data Loading:
	
 	• Data from GCS is loaded into BigQuery tables:
	
   	• merchants.json → merchants_tb
	
   	• walmart_sales.json → walmart_sales_stage

3.	Data Transformation:
	
 	•	A SQL MERGE query performs an UPSERT to:
	  
   	•	Update existing records in the target table (walmart_sales_tgt) based on the staging table.
	
  	 •	Insert new records if they don’t exist.

4.	Orchestration with Airflow:
	
 	•	DAG (walmart_sales_etl_gcs) automates the workflow:
	
   	•	Creates datasets and tables.
	
   	•	Loads data from GCS to BigQuery.
	
   	•	Performs the MERGE operation to upsert data.


## Steps to Execute

1.	Setup the Environment:
	
 	•	Install Apache Airflow with the required providers (google-cloud).
	
 	•	Configure Airflow to connect to your GCP account.
	
 
2.	Upload Files to GCS:
	
 	•	Place the merchants.json and walmart_sales.json files in appropriate GCS buckets.

3.	Deploy the DAG:
	
 	•	Place airflow_bigquery_dag.py in the Airflow DAGs directory.
	
 	•	Start the Airflow scheduler and webserver.

4.	Run the Pipeline:
	
 	•	Trigger the DAG from the Airflow UI.
	
 	•	Monitor the progress using the DAG graph.

## GCP Console Project Screenshots

### Airflow DAG Graph

![Airflow_dag_graph.png](https://github.com/Kaushik-Puttaswamy/Walmart-Sales-Data-Ingestion-and-Transformation-in-BigQuery-using-Airflow/blob/main/GCP_Console_Walmart_Salesdata_Ingestion_Screenshot/Airflow_dag_graph.png)

### Merchant Table Preview

![Merchant_table_preview.png](https://github.com/Kaushik-Puttaswamy/Walmart-Sales-Data-Ingestion-and-Transformation-in-BigQuery-using-Airflow/blob/main/GCP_Console_Walmart_Salesdata_Ingestion_Screenshot/Merchant_table_preview.png)

### Staging Table (Walmart Sales)

![Walmart_sales_stage_table.png](https://github.com/Kaushik-Puttaswamy/Walmart-Sales-Data-Ingestion-and-Transformation-in-BigQuery-using-Airflow/blob/main/GCP_Console_Walmart_Salesdata_Ingestion_Screenshot/Walmart_sales_stage_table.png)

### Target Table (Walmart Sales Consolidated)

![Walmart_sales_target_table.png](https://github.com/Kaushik-Puttaswamy/Walmart-Sales-Data-Ingestion-and-Transformation-in-BigQuery-using-Airflow/blob/main/GCP_Console_Walmart_Salesdata_Ingestion_Screenshot/Walmart_sales_target_table.png)

### Airflow DAG Uploaded

![airflow_bigquery_dag_file_uploaded_in_airflow_bucket.png](https://github.com/Kaushik-Puttaswamy/Walmart-Sales-Data-Ingestion-and-Transformation-in-BigQuery-using-Airflow/blob/main/GCP_Console_Walmart_Salesdata_Ingestion_Screenshot/airflow_bigquery_dag_file_uploaded_in_airflow_bucket.png)

## Technologies Used
	
 ## •	Google Cloud Platform (GCP):
	
 •	BigQuery
	
 •	Google Cloud Storage (GCS)
	
 ## •	Apache Airflow:
	
 •	DAG orchestration
	
 •	Operators: BigQueryCreateEmptyDatasetOperator, GCSToBigQueryOperator, etc.
	
 ## •	Python:
	
 •	For DAG scripting and SQL transformations.

 ## Conclusion

This project provides a robust ETL pipeline for Walmart sales data using Google BigQuery and Airflow. By leveraging the power of cloud-based tools and automation, the pipeline ensures efficient data ingestion, transformation, and consolidation.

Feel free to explore and enhance this pipeline for more complex workflows! 🚀
