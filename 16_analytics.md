# 16 Analytics

## 16.1 Amazon Athena
- https://aws.amazon.com/athena/
- *"Analyze petabyte-scale data where it lives with ease and flexibility"*
- A serverless, interactive query service for analyzing data in Amazon S3 using standard SQL
- Simplify big data analysis by removing the need for infrastructure amangement and enabling quick insights
- Features: Pay-per-query pricing, Schema-on-read, Integration with AWS Glue Data Catalog
#### How to use Athena
- Define table schema and specify data location in Amazon S3
- Write SQL queries in the Athena console or throgh API/SDK
- Athena processes the query and stores results in an S3 bucket
#### Schema on Read
- Schema derived during query executino, not predifined during data ingestion
- Benefits: Flexibility, Reduced data preparation time, cost savings
#### AWS Glue Data Catalog Integration
- AWS Glue Data Catalog: A managed metadata repository of storing and managing table definitions and schema
- Benefits: Simplified table management, schema versioning, and unified metadata across AWS analytics services
#### Querying Data Formats
- Supported Data Formats: CSV, TSV, JSON, Parquet, ORC, Avro
- Compression Formats: GZIP, Snappy, LZO, BZIP2
#### Perfomrance Optimization
- Query Execution: Leverage parallel processing for faster results
- Workgroups: Isolate query environments and mange resources for multiple users
- Query Caching: Speed up query execution by caching results of previously executed queries
- Partitioning: Improve query performance by organizing data based on specific columns
#### Example Athena Use Cases
- Log Analysis - Analyze application and infrastructure logs for insight and troubleshooting
- Ad-hoc Data Analysis - Perform exploratory analysis on raw data in S3
- Data Transformation - Preprocess and transform data before loading into other AWS services
#### Athena vs. Other AWS Big Data Services
- Redshift - Use Athena for ad-hoc queries on S3 data; Redshift for structured, high-performance analytics on large datasets
- EMR - Use Athena for serverless, SQL based analytics; EMR for managed, customizable big data frameworks
- AWS Athena simplifies big data analytics with a severless, interactive query service that requres no infrastructure management

## 16.2 Kinesis Data Analytics
- *"Gain actionable insights from streaming data iwth serverless, fully-managed APache Flink"*
- https://aws.amazon.com/kinesis/
- Kinesis Data Analytics Service - A fully-managed, serverless service for processing and analyzing streaming data in real time
- Easily build and deploy streaming applicatinos without infrastructure management
- Features: Scalability, Low-latency processing, AWS Service Integration
#### Common Use Cases:
- Real-time dashboards, Anomaly detection
- Log and event data analysis
- Real-time reommendations
#### Kinesis Data Analytics Components
- Kinesis Data Streams - Ingest and store streaming data
- Kindesis Data Firehose - Load data into destinations such as Amazon S3 or Amazon Redshift
- Kinesis Data Analytics - Process and analyze streaming data using SQL or Apache Flink applications
#### Creating a Kinesis Data Analytics Applicatino
1. Select a runtime - SQL or Apache Flink
2. Connect to a data source - Kinesis Data Stream of Dinesis Data Firehose
3. Define Processing logic - Write SQL queries or Flink code
4. Set up destinations - Output processed data to other services
#### SQL Runtime
- Use SQL queries to process and analyze streaming data
- Supports windowed queries and aggregations
- Pre-built analytics functinos, e.g.: anomaly detection, time series analysis
#### Apache Flink Runtime
- Develop applications using the APache Flink framework
- Supports: Complex event processing; Statuful processing; Custom analytics logic
- Leverage the full power of the Flink API for advanced use cases
#### Scalability and Performance
- Kinesis Processing Unit (KPUs): Scale processing power and memory as needed
- Scaling: Automatic based on input data rate and application complexity
- Low-latency processing: Near-real-time insights
#### Kindesis Data Analytics Studio
- Develop, test, and troubleshoot applications using an interactive notebook interface
- Interactive Notebooks: Jupyter notebooks, write code, collaborate
- Integration with Kinesis Data Analytics: Seamless transition between Studio and Kinesis Data, deploy tested code
- Support for Apache FLink and SQL

## 16.3 Amazon OpenSearch Service
- *"Securely unlock real-time search, monitoring, and analysis of business and operational data"*
- https://aws.amazon.com/opensearch-service/
- A fully-managed, scalable search and analytics service based on OpenSearch and Elasticsearch
- Simplify the deployment, management, and scaling of search and analytics workloads
- Features: Easy deployment, scalability, high availability, security
##### OpenSearch vs. Elasticsearch
- ***OpenSearch***: A community driven, open source search and analytics suite, derived from Elasticsearch
- ***Elasticsearch***: A powerful, open-source search and anlaytics engine for various types of data
- ***AWS OpenSearch Service***: Supports both OpenSearch and ElasticSearch APIs
#### Common Use Cases
- Full-text search
- Log and event data analyis
- Real-time application monitoring
- Security analytics
#### Deploying AWS OpenSearch Service
- Domain Creation - Create and OpenSearch domain to hold your data configuration
- Instance Types - Choose from various instance types to optimize for cost, performance, and storage
- Data Durability - Automatically replicate data across multiple Availability Zones
#### Indexing Data
- Data Ingestion
- Indexing
#### Scalabiliyt and PErfomrance
- Shards, Replicas, Auto scaling
#### Monitoring and Troubleshooting
- AWS CloudWatch, OpenSearch Dashbaords, AWS CloudTrail


## Practice Questions


Question 1
What is the key benefit of AWS Glue Data Catalog when used with AWS Athena?

Responses

Simplified table management and schema versioning. - correct
Data storage in Amazon S3.
High-performance analytics on large datasets.
Real-time data processing.


Question 2
What is AWS Athena primarily used for?

Responses

Performing high-performance analytics on large datasets in Redshift.
Analyzing data stored in Amazon S3 using SQL queries. - correct
Running serverless functions in AWS Lambda.
Extracting, transforming, and loading data in AWS Glue.


Question 3
Which AWS service is used to create time series data?

Responses
Amazon S3
Amazon Kinesis Data Analytics - correct
Amazon Redshift
AWS Glue


Question 4
What is the primary use case for Amazon Kinesis Data Analytics?

Responses

Real-time processing and analysis of streaming data. - correct
Batch processing of historical data.
Long-term data storage and archiving.
Machine learning model training.


Question 5
Which AWS service is specifically designed for high-performance analytics on large datasets, offers data warehousing capabilities, and supports complex queries and reporting?

Responses

Amazon Redshift - correct
Amazon Glue
Amazon Athena
Amazon S3