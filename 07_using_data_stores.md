# 7. Using Data Stores in Application Development

https://aws.amazon.com/architecture/databases/?cards-all.sort-by=item.additionalFields.sortDate&cards-all.sort-order=desc&awsf.content-type=*all&awsf.methodology=*all

## 7.1 CRUD
#### Concepts
- **CRUD** Create, Read, Update, Delete (set of basic operations a system should provide to manage data (generic concept))
- **Data Consistency**: Accucarcy and reliability of data sotred in a system
  - Data is in a valid state
  - Meets requirements
  - Examples: Amazon RDS, DynamoDB, ElastiCache, there are many more...
- **Caching**: Process of storing frequently accessed data in memory or disk
  - reduces access time and improves performance
  - Commonly used to speed up web applications, reduce database load, and improve user experience
  - **Cache Invalidation**: Process of removing cached data when it becomes invalid or stale
    - Examples: Amazon ElastiCache
  - Ensures users always see the latest data and that the cache does not store outdated or incorrect information

#### Best Practices
- Use managed database services such as Amazon RDS, DynamoDB, etc
- Use caching services such as Amazon ElastiCache or Amazon Cloudfront to reduce database load and improve performance
- Use cache invalidation techniques such as TTL or real-time invalidation, to ensure data freshness and consistency

#### Further Reading:
- Tutorial:Build a CRUD API with Lambda and DynamoDB
- CloudFront Developer Guide

## 7.2 Simpole Storage Service (S3) and S3 Glacier
- Touch often and understand early, store generic files
- "Object storage build to store and retrieve any amount of data from anywhere"
#### Understanding S3
- Simple (Easy to Use), Storage (Cloud Storage), Service (AWS Service)
- Intentionally minimal, REST and SOAP Interfaces
- Region based pricing
- Fine-grained permissions
- Store and infinite amount of data
- Objects up to 5TB in size
- Created with Console, CLI, API
#### Storage Class Options
![alt text](image-4.png)
![alt text](image-5.png)

#### S3 Components
- **Buckets**: Container for objects stored in Amazon S3, every object is stored in a bucket
- **Objects**: *"Thing"* (with path) stored (aka file, etc.), Entities stored in Amazon S3:
  - Object Data: Opaque to Amazon S3
  - Meta Data: Name-value pairs that describe the object:
    - Default metadata: Date last modified, standard HTTP metadata such as Content Type
    - Custom Metadata: Specified when the object is stored
  - Objects can be encrypted, client-side and server-side options
- **Keys**: Unique identifier for an object
  - Every object has one key
  - Bucket + Key + Version identifies all objects
  - Every object in Amazon S3 can be addressed with combination of:
    - The web service endpoint
    - Busket name
    - Key
    - Version

#### Features of S3
- S3 buckets can be made public
- If so, accessed via fully qualified domain name
- Commonly used for storage of images for websites
- **Versioning** by default this is enabled, but once enabled, can't disable
- **Lifecycle Managment** Manage cost through lifecycle management

#### Further Reading
- https://docs.aws.amazon.com/s3/
- https://docs.aws.amazon.com/AmazonS3/latest/userguide/GetStartedWithS3.html

## 7.3 S3 Demo

## 7.4 S3 Global Replication and SDK Interaction Demo

## 7.5 Relational Database Service (RDS) Including Aurora
#### What is AWS RDS?
- Cloud based service that provieds managed database engines for popular relational databases:
  - MySQL, PostgreSQL, Oracle, SQL Server
- Automates time consuming tasks:
  - Hardware provisioning, Patching, Backups, Monitoring
- Managed Service, Highly Available, Scalable, Secure
#### Available Engines (RDS)
- **Amazon Aurora**
  - MySQL and PostrGRES Compatible
  - Powerful and very capable database
- **MySQL**
  - Up to 32 vCPUs and 244 GiB Memory
  - Database up to 6TB
  - Free tier eligible
- **MariaDB**
  - MySQL compatible
  - Up to 32 vCPUs and 244 GiB Memory
  - Database up to 6TB
  - Free tier eligible
- **PostgreSQL**
  - Free tier eligible
- **Oracle**
  - Enterprise Edition
  - Standard Edition: Up to 32 vCPUs
  - Standard Edition One: Up to 16 vCPUs
  - Standard Edition Two: Up to 16 vCPUs
- **Microsoft SQL Server**
  - SQL Server Express: Free tier eligible, database size up to 10 GB
  - SQL Server Web: Licensed to support public and internet accessible web sites/services/applications
  - SQL Server Standard Edition
  - SQL Server Enterprise Edition
#### Pricing, RDS - Based on Multiple Components
- **Instance Class**: micro, small, large, xlarge
- **Running Time**: Based on instance-hour
- **Storage**: Per-GB per-month
- **I/O Requests**: Total number of storage I/O requests
- **Backup Storage**: Storage used for automated backups and snapshots
- **Data Transfer**: Internet data transfer in and out of your DB instance

#### RDS Engine Configuration
- Each engine has specific configuration options
- Master username/password specifieid during launch
- Production Option: Multi-AZ deployment
- Dev/Test Option: Free tier eligible
- Allocated storage defined during launch
- Can be scaled without down time

#### RDS Configuration Highlights
- Instance Class - like EC2
- Storage type and size like EC2 - Storage auto-scaling option
- Templates: Production, Dev/Test, Free Tier
- VPC attachment
- Public Access
- Security Group
- Authentication: Password, Password and IAM database authentication, Password and Kerberos authentication
- Automated backups, daily snapshots
- Encryption
- Auto-minor version upgrade
- Termination Protection
- RDS instance (just a computer, similar to an EC2 instance)
  
#### Aurora Serverless
- Fully managed, auto-scaling version of Aurora
- Auto-Scales
  - Based on: Workload, Performance requirements
  - Scales database instances up or down based on the workload
  - Reduces costs and improves performance
- Pay-per-use
  - Charges users based on the usage
  - With no upfront costs or minimum capacity requirements
- High Availability
  - Automatic failover and replication accross multiple availability zones
  - Ensuring high availability and durability
- A Feature: Global Database
  - Global access allows users to read and write to the same database from multiple regions improved performance, reduced lattency
  - Allows users to write to the same database from multiple regions simultaneously, enabling global multi-master access
  - Automatic Fail-over
  - Not necessarily cheap

#### Further Reading
https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html

#### Demo
- "Relatively simple service"

## 7.6 DynamoDB
- *"Fast, flexible NoSQL database service for single-digit millisecond performacne at any scale"*
- Managed NoSQL Database (not a relational database)
- Fault tolerant design distributed across AZs
- Scale up/down without downtime
- Can be connected to a VPC through a VPC endpoint
- Accessible throgh SSL/TLS API endpoints
- Time-to-live Data Expiration
#### DynamoDB Core Components
- **Table**: Collection of Data, contains multiple ***Items***
- **Item**: Contains Multiple ***Attributes***, no limit on the number of ***items*** in a database, similar to rows
- **Attributes**: Key/value pairs describing the ***item***
- **Primary Key**: Uniquely identifies the ***item***
#### Naming Rules
- All names must be encoded using **UTF-8**
- Case-sensitive
- ***Table*** names and index names must be between 3 and 255 characters long
  - Valid characters: "a-z", "A-Z", "0-9"
  - "_" (underscore)
  - "-" (dash)
  - "." (dot)
  - ***Attribute*** names must be between 1 and 255 characters long
- Reserved Words: https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/ReservedWords.html
#### Accessing DynamoDB
- DynamoDB console
- AWS CLI
- AWS API
- note: DynamoDB is accessed exclusively through API, no JDBC or ODBC
#### Security
- ***There are no security groups with DynamoDB***
- Authentication via:
  - AWS Account Root User
  - IAM user with appropriate permissions
  - IAM role with appropriate permissions
- Access enforced with IAM permissions
- Identity base permissions
  - Attach a permissions policy to a user or a group in your account
  - Attach a permissions policy to a role
  - Cognito Identity Pools (Facebook, Google, Login with Amazon)

## 7.7 DynamoDB Technical Details
#### DynamoDB Keys
- Primary Keys: Single Attribute, Partition Key, determines the storage partition
- Must be unique across the table
#### Composite Primary Key
- Composed of two attributes
- Partition Key + Sort Key
- Partition keys can overlap, must have different sort values
- Same partition key value are stored togehter, in sorted order by sort key value
- Partition key also known as it's *hash attribute*
#### Scan vs. Query
- **Query**: Searches only primary key attribute values; supports comparison operators on values to refine search; ***Fast***
- **Scan**: Scans the eintire table; Specify filters to refine the results returned; Big table, not fast, Consider secondary index
#### Secondary Indexes
- Data structure that contains a subset of attributes from a table
- Can query secondary index
- Tables can have multiple secondary indexes
- Supports scanning
- Associated with only one table, base table
- Alternate key created
- Include all or only projected attributes
- Secondary index is auto updated with base table is modified
#### Indexes
- Global Secondary Index
  - Index with partition key and a sort key different from base table
  - "Global" = queries can span all of data in the base table, across all partitions
- Local Secondary Index
  - Index with the same partition key as the base table
  - Different sort key
- "local" = scoped to a base table partition that has the same partition key value
#### Read Consistency
- DynamoDB Tables span availability zones for redundancy, takes time to replicate writes
- Eventually Consistent Reads (Default)
  - Read response might not reflect the results of a recently completed write operation
- Strongly Consistent Read
  - DynamoDB returns a response with the most up-to-date data, reflecting the updates from all prior write operations that were successful
#### Read Capacity Units
- "A ***read capacity unit*** represents one strongly consistent read per second, or two eventually consisternt read per second, for an item up to 4 KB in size"
- DynamoDB rounds up
- Item larger than 4 KB, Divide 4KB to determin RCU needed or one read
- Strong Read/Sec = RCU/(itemsize / 4KB)
- Eventual Read/Sec = RCU/(itemsize / 8KB)
- Cross Region Replication (Enables global tables):
  - Automatically replicated table data to another region
  - Supports multi-master writes
  - table must be empty to enable
  - Requires ***streams*** to be enabled
- Streams: Near-real-timme streaming of creates, updates, or deletes of data in a table
- Stream Record: Infromation about a data modification to a single item in a DynamoDB table
- **Triggers**: Execute Lambda function when data modified in table
  - Uses streams to send old/new image to Lambda function
  - AWS Lambda polls the stream and invokes your function synchronously when new stream records are encountered
#### Best Practices
- Understand the differences between ***Relational Data Design*** and ***NoSQL**
- Maintain as few tables as possible in a DynamoDB application
- Keep related data together
- User Sort Order: Related items (e.g. same PK) are grouped toghether, faster to sort
- Architect your data so the queries are distributed, avoid hot spots
- Use global secondary indexes, if needed
- Use DynamoDB Auto Scaling
- Extensive list of best practices for DynamoDB from a developer perspective:
- S3 for storing files, Dynamo for storing ***"Tabular Data"*** (???)
#### Further Reading
- https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/bp-general-nosql-design.html
- https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/best-practices.html
- https://aws.amazon.com/architecture/databases/?cards-all.sort-by=item.additionalFields.sortDate&cards-all.sort-order=desc&awsf.content-type=*all&awsf.methodology=*all

## 7.8 DynamoDB Demo

## 7.9 ElastiCache
#### What is AWS EstiCache?
- In memory caching service
- Simple, Cost Effective
- Improves the performance and scalability of web applications
- Supports popular caching engines, eg: Redis, Memcached
- Allows users to easily deploy and manage caching clusters in the cloud
- Backend system (allows application to pull information than going to Database)
- Provides low-latency and high-throughput caching, with fast access to frequently accessed data
- Allows users to easily scale thier cahcing clusters up or down, depending on the workload and performance requirements
- **Availability**: Multi-AZ deployments and auto fail over, high availability options
- **Cost Effective**: pay-per-use pricing
#### Redis
- Open-source, in-memory data structure store
- Supports a variety of data structures: Strings, Hashes, Lists, Sets, Sorted Sets, ...
- High performance and low-latency access to data
- Support for persistence, replication, and clustering
- Benefits: High Performance, Persistence, Replication, Clustering
#### Memcached
- Open-source, distributed memory caching system
- Stores data in memory ot reduce database load and improve performance
- Supports simple key-value data model with ***no*** support for advanced data structures
- Benefits: Simple and lightweight, High performance, Scalability, Compatibility (PHP, Python, Ruby, etc)
- Autoscaling is available
#### Security
- ElastiCache provides encryption, access control, and network isolation
- Encryption at rest and in transit
- Fine grained access control, with IAM roles and policies, security groups, and VPC endpoints
- Provides network isolation with dedicated subnets and security groups for caching clusters
#### Use Cases
- Web applications with high traffic: e-commerce, social media, gameing, etc.
- Real-time applications low latency and high throughput: chat, streaming, and analytics
- Content delivery applications high scalability and availability: media streaming, video on demand, etc.
#### Best Practices
- Use the appropriate caching engine and instance type buased on the workload and performance requirements
- Use multiple cahe nodes and replication options to ensure availability and durability
- Use the appropriate scaling options, such as auto-scaling and vertical scaling, to optimize performance and cost
- Use encryption and access control to protect the data and comply with security standards
- Use monitoring and logging tools such as Amazon CloudWatch and ElastiCache Events, to track performance and detect issues
#### Use Case: Gaming Example
- Require low latency and high throughput for real-timedata processing and caching
- ElastiCache with Redis: Provides hgih performance caching for *game state*, *session data*, *leaderboard data*
- ElastiCache with Auto Scaling: Automatic scaling of caching clusters based on the number of players and the workload
- ElateiCache with encryption and access control: Ensures the protection of player data and the compliance with sercurity standards
#### Use Case: E-commerce
- Requires high scalability and availability for fast and reliable access to product data and recommendations
- ElastiCache with Memcache: Provides low-latency caching for product catalogs, session data, and user preferences
- ElastiCache with auto-scaling: Allows automatic scaling of caching clusters based on the traffic and demand
- ElastiCache with monitoring and logging tools: Allows tracking of performance and detection of issues
#### Use Case: Analytics
- Require high throughput and low latency for real-time data processing and caching
- ElastiCache with Redis: provides high performance caching for data sets, results and models
- ElastiCache with clustering: allows scaling of caching clusters across multiple regions for global access and distribution
- ElastiCache with integration with Lambda and Kinesis: Allows real-time processing and event-driven analytics
#### Further Reading
- ElastiCache for Redis User Guide: https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/WhatIs.html
- ElastiCache for Memcached User Guide: https://docs.aws.amazon.com/AmazonElastiCache/latest/mem-ug/WhatIs.html

## 7.10 MemoryDB for Redis
#### What is MemoryDB for Redis?
- **MemoryDB for Redis**: A fully managed, in-memory datase service that is compatible with the Redis data model and API
- **Purpose**: Designed for real-time applications that require high performance, low latency, and durability
- **Key Features**: Automatic data persistence, Failover and recovery, Seamless scalability
- *"Simply, Redis running in the cloud"*
- **Data Model**: Suppors the Redis data types such as strings, lists, sets, sorted sets, and hashes
- **API**: Compatible with most Redis commands enabling easy migration of existing Redis applications
- **Client Libraryies**: Works with existing Redis client libraries, reducing the need for code changes
- **Snapshots**: Automatic, periodic snapshots of your data to Amazon S3 for durability
- **Point-in-time Recovery (PITR)**: Recover your data to any point within the specified retential window
- **Backup and Restore**: Backup your data to Amazon S3 and restore to a new MemoryDB cluster when needed
- **Multi-AZ deployment**: Deploy MemoryDB clusters across multiple Availability Zones for redundancy
- **Automatic Failover**: In case of a primary node failure MemoryDB automatically promotes a read replicat to primary
- **Read Replicas**: Create read replicas to offload read traffic and improve read performance
- **Seamless Scaling**:
- **Partitioning**:
- **Low Latency**: Provides *microsecond latency for read and write operations, enabling real-time processing
- **Encryption**: *At Rest* use AWS Key Management Service (KMS), and *In Transit* using TLS
- **Network Isolation**:
- **Compliance**: Compliant with various industry standards such as HIPAA, GDPR, and PCI (paymet card industry)
- **Amazon CloudWatch**:
- **AWS Management COnsole**:
- **AWS Cloud Trail**:
#### MemoryDB vs ElastiCache Redis
![alt text](image-6.png)
- AWS MemoryDB for Redis offers a fully managed, Redis-compatible, in-memory database that enables real-time applications with high performance and low latency
- *"Doesn't require a database on the side, this is a database"*
#### Further reading:
- https://aws.amazon.com/memorydb/
- https://docs.aws.amazon.com/memorydb/
- https://docs.aws.amazon.com/memorydb/latest/devguide/what-is-memorydb-for-redis.html


## 7.11 Elastic Block Store (EBS) and Elastic File System (EFS)
- "Essentially files on disk"
- "But both work very differently in the background"
#### EBS - Elastic Block Storage
- High performance block storage service designed for use iwht Amazon EC2 Instances
- *"Essentially a hard drive on a computer"*
- **Use Cases**: Boot volumes, databases, big data analytics, and other workloads that require high IOPS and low latency
- High performance, durability, availability, and snapshot capabilities
- Essentially a hard disk (EBS manages, more often than not, this disk)
- **Volume Types**:
  - General Purpose SSD: Balanced performance and cost for a wide range of workloads
  - Provisioned IOPS SSD: Designed for I/O intensive applicatins with strict latency requirements
  - Throughput Optimized HDD: Ideal for bid data, data warehousing, and log processing workloads
  - Cold HDD: Suitable for infrequently accessed, large, and sequential workloads
- Snapshots (Point in Time backups), Incremental Backups, Sharing and Copying (accross AWS accounts and across AWS Regions)
#### EFS - Elastic File Storage
- Network filesystem that multiple instances can access
- *"Standalone server off somewhere with many disks in it"*
- A fully managed elastic, and scalable network file system for use with AWS services
- **Use Cases**: File sharing, content management, big data analytics, and container storage
- Scalability, high availability, durability and integration with AWS services
- **Performance Modes**:
    1.  General Purpose - Content management and web serving, optimized for latency sensitive use cases
    2.  Max I/O - Designed for highly parallel and throughput intensive workloads, such as big data analytics
- **Access Points**: Simplified Access, POSIX Permissions
#### Choosing the right storage solution
- EBS: High performance block storage for Amazon EC2 instances, suitable for databases and boot volumes
- EFS: Scalable and shared file storage for multiple instances, suitable for file sharing and content management
#### Security
- Encryption - Encrypt data at rest and in transit for both EBS and EFS
- IAM Policies - Use IAM policies to control access to EBS volumes and EFS systems
- Network Isolation: Use Amazon VPC to isolate your EBS volumes and EFS file systems within a secure network

#### Further Reading
- https://aws.amazon.com/ebs/
- https://docs.aws.amazon.com/ebs/latest/userguide/what-is-ebs.html
- https://aws.amazon.com/efs/
- https://aws.amazon.com/efs/resources/?whats-new-posts.sort-by=item.additionalFields.postDateTime&whats-new-posts.sort-order=desc

## 7.12 EBS/EFS Demo



## Practice Questions

Question 1
Which of the following accurately describes AWS Simple Storage Service (S3)?

Responses
A cloud-based service for computing resources on demand.
A database service offered by AWS to store relational data.
A service offered by AWS to execute code in response to certain events.
A service for storing and retrieving any amount of data from anywhere, allowing objects up to 5 terabytes in size. - correct


Question 2
Which of the following statements is true about DynamoDB?

Responses
DynamoDB is just like MongoDB in that both are NoSQL databases. - correct
All data in DynamoDB is stored without encryption in transit.
DynamoDB primary keys consist of a single attribute called the partition key.
DynamoDB is a managed relational database offering from Amazon Web Services.


Question 3
Which of the following statements about AWS RDS (Relational Database Service) is NOT true?

Responses
AWS RDS allows unlimited scaling of backend storage with frequent downtime. - correct
AWS RDS simplifies setting up, operating, and scaling a relational database in the cloud.
AWS RDS supports multiple database engines, including MySQL, Postgres, Oracle, and SQL Server.
Aurora is an AWS RDS engine that is compatible with MySQL and offers high throughput.


Question 4
Which of the following statements about AWS S3 is false?

Responses
In the process, the instructor created an S3 bucket, named it adgu-bucket, and subsequently uploaded a clouds.jpg image to it. - no response given
When creating an S3 bucket, users have the option to copy settings from an existing bucket.
Replicating objects from one S3 bucket to another requires versioning to be enabled on both source and destination buckets.
Once bucket versioning is enabled, it cannot be suspended. - correct


Question 5
Which of the following best describes CRUD in the context of AWS development?

Responses
A caching mechanism used in AWS to store frequently accessed data.
A memory caching service that ensures data consistency.
The name of an AWS service dedicated to database operations.
A set of HTTP methods associated with RESTful API endpoints. - correct