# Dynamic-Data-Ingestion-and-Storage-in-HDFS-with-Automated-Hive-Integration
📦 VMware Hadoop ETL Project — Local CSV & MySQL to Hive
Introduction

This project demonstrates a complete ETL workflow on a VMware virtual machine environment using Python 2.4, Hadoop HDFS, Hive, and Sqoop.

Since Python 2.4 does not support HTTPS downloads, all source files are assumed to be available locally. This ETL workflow includes:

Uploading a local CSV file to HDFS

Creating a Hive table from the CSV file

Importing a MySQL table into HDFS using Sqoop

Creating a Hive table from the imported Sqoop data

Objectives

By completing this project, you will be able to:

Upload local CSV files to HDFS

Create Hive tables from CSV and HDFS data

Use Sqoop to import MySQL tables into HDFS

Integrate HDFS, Hive, and Sqoop using Python scripts

Prerequisites

VMware environment with Python 2.4 installed

Hadoop and HDFS configured

Hive installed and properly configured

MySQL server running with a database named training

Sqoop installed and configured

Local CSV file available at /home/training/product_data.csv

Dataset

Local CSV: product_data.csv
Columns: id, product_name, price, city

MySQL Table: Movies
Columns: movieid, movie_name, release_date, imdb_url, unknown, action, adventure, ..., western

ETL Steps
1. Verify Local CSV

The script checks if the CSV file exists and is not empty.

Exits with an error if the file is missing or empty.

2. Upload CSV to HDFS

Removes any previous directory in HDFS (/product_data)

Creates HDFS directory /product_data

Uploads local CSV file to HDFS

Verifies upload by listing files in HDFS

3. Create Hive Table for Product Data

Drops existing Hive table product_table if it exists

Creates product_table with appropriate columns and data types

Loads data from HDFS CSV file

Queries the first 10 rows to verify

4. Import Movies Table from MySQL using Sqoop

Removes any previous HDFS directory (/sqoop_movies)

Uses Sqoop to import Movies table from MySQL into HDFS

Imports with a single mapper (-m 1)

5. Create Hive Table for Movies

Drops existing Hive table movies_table if it exists

Creates movies_table with all columns from Movies table

Loads data from Sqoop-imported HDFS file (part-m-00000)

Queries the first 10 rows to verify

Folder & File Structure
VMware_ETL_Project/
│
├── product_data.csv          # Local CSV file
├── etl_hive_sqoop.py        # Python 2.4 ETL script
├── HiveTables/              # Hive database (virtual)
├── HDFS/                    # Hadoop file system (HDFS)
└── README.md

How to Run

Ensure all prerequisites are installed and running:

Hadoop HDFS

Hive

MySQL with Movies table

Sqoop

Place the local CSV at /home/training/product_data.csv.

Run the ETL Python script:

python etl_hive_sqoop.py


The script will perform:

CSV upload to HDFS

Hive table creation for product data

Sqoop import from MySQL

Hive table creation for Movies

Verify results using Hive queries:

SELECT * FROM product_table LIMIT 10;
SELECT * FROM movies_table LIMIT 10;

Notes

The Python script uses os.system() commands to interface with Hadoop, Hive, and Sqoop.

Designed for Python 2.4, which does not support HTTPS downloads. Local files must be used.

All HDFS directories are removed before upload to avoid conflicts.

Conclusion

This project demonstrates a full ETL workflow in a VMware Linux environment using Hadoop ecosystem tools:

Local CSV → HDFS → Hive

MySQL → Sqoop → HDFS → Hive

It showcases essential data engineering skills, including:

HDFS file management

Hive table creation and data loading

Sqoop data import from MySQL

Python automation for ETL orchestration
