# Data-Migration-from-On-Prem-SQL-Server-to-Azure-SQL-using-Azure-Data-Factory

## Project Description:
This project automates the migration of multiple on-premises SQL Server tables to Azure SQL Database using Azure Data Factory (ADF). The data is first extracted and stored in Parquet format in Azure Data Lake Storage, then transformed and loaded into Azure SQL. The pipeline supports validation, parameterization, and is scalable across environments.

## Project Implementation (Key Steps):

1.Lookup / Metadata Extraction:
Use Lookup or Get Metadata activity to fetch the list of tables from SQL Server.

2.ForEach Loop for Table-wise Processing:
Iterate over each table name using ForEach activity.

3.Copy Data to Parquet:
Inside the loop, use Copy Data activity to extract SQL Server data and store it as Parquet files in Azure Data Lake.

4.Pipeline Execution:
Trigger a child pipeline (ParquetToTables) using Execute Pipeline for further transformation and loading.

5.Parquet to Azure SQL:
Use another ForEach inside ParquetToTables pipeline to read each Parquet file and load it into corresponding Azure SQL tables.

6.Parameterization:
Use ADF parameters to dynamically handle table names, file paths, and environment-specific configurations (dev/test/prod).
