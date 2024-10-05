# Guvi_final_assignment
Retail data 
1.	Stage 1: Data Ingestion and Initial Processing
○	Transfer sales files from a local system to an S3 bucket using a Python script.
○	Use AWS Glue to clean and merge all files in S3 into a new bucket on a scheduled basis.
○	Trigger a Lambda function to load data from the new S3 bucket into AWS RDS upon file availability.
2.	Stage 2: Feature Data Management
○	Store feature files in HDFS.
○	Use PySpark to clean and push feature data from HDFS to a Hive table database.
3.	Stage 3: Data Consolidation
○	Load all store data into AWS RDS (cleaning if required).
○	Use Sqoop to transfer data from AWS RDS to Hive.
4.	Stage 4: Integration of Stages
○	Ensure the environment is capable of integrating stages 1, 2, and 3 seamlessly.
5.	Stage 5: Data Storage and Processing
○	Use PySpark jobs to store processed data in RDS or files based on the requirements.
6.	Stage 6: Pipeline Orchestration
○	Implement an Airflow pipeline to connect and orchestrate all stages from 1 to 5.
7.	Stage 7: Monitoring
○	Use Prometheus to monitor the entire pipeline from stage 1 to stage 6.


All the above steps are automated , no manual intervention is needed except for to create RDS database in AWS which is a one time process. 
Using Airflow with the help of Docker, all the 3 datasets will be uploaded to a S3 bucket and then 
1)Sales files will be processed( merging process) using AWS Glue immediately after the files are loaded in the bucket and then AWS lambda stores the data in these files into a RDS instance.
2) Feature files will be pushed to hdfs using EMR Step and then using Spark a hive table will be created and stored in S3.
3) Store files will be stored in AWS RDS instances and then using EMR with the help of Sqoop import data from RDS will be transfered to Hive.
4) Using Airflow all the above mentioned steps are integrated.
5) Data from hive tables and RDS are combined into a single file for swift analysis.
6) Prometheus and Grafana are used to montior the entire pipeline
