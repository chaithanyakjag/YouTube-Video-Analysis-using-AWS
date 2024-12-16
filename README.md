# YouTube-Video-Analysis-using-AWS

## Project Overview
This project processes YouTube trending video data from multiple regions and transforms it into a clean, queryable format. The final output is visualized using Amazon QuickSight to analyze trends like top-performing videos, popular categories, and regional audience engagement.

## Architecture Diagram
![image](https://github.com/user-attachments/assets/d449f34f-7a12-4854-997a-119508ea805c)

## Steps and Workflow
### 1. Data Ingestion
- Created an Amazon S3 bucket to store raw JSON and CSV files of YouTube trending video data from Kaggle.
- Uploaded the raw files to the S3 bucket using the AWS CLI

## 2. Data Transformation & Cataloging
- Used AWS Glue Crawlers to scan and catalog raw data, generating metadata for schema discovery.
- Deployed an AWS Lambda function to:
  - Flatten and clean nested JSON files.
  - Convert the cleaned data into Parquet format for optimized querying and storage.
  - Save the transformed files in the s3://<bucket-name>/processed-data/ folder.
- Configured an AWS Glue ETL job to:
  - Convert CSV files into Parquet format.
  - Save the transformed files in the same processed data folder.

## 3. Data Integration
- Created an AWS Glue ETL job to:
  - Join the cleaned JSON and CSV datasets into a consolidated Parquet dataset.
  - Store the integrated dataset in S3

## 4. Querying and Analysis
- Connected Amazon Athena to the consolidated dataset for SQL-based querying.
- Analyzed key metrics, including:
  - Most-viewed and most-liked videos.
  - Engagement trends across regions and categories.

## 5. Data Visualization
- Set up Amazon QuickSight and linked it to Athena to visualize the consolidated data.
- Built dynamic dashboards to display:
  - Engagement trends by region.
  - Popular categories and channels.
  - Top-performing videos by views and likes.

