# 10. Application Integration

## 10.1 AppSync
Fully managed service that simplifies the proces of building real-time and offline-capable applications
#### Purpose:
- Provide a consistent experience across devices and platforms by synchronizing data across multiple data sources
- **Key Features**: GraphQL Support, Real-time Updates, Offline Access, Data Sources Integration
- AppSync uses *GraphQL*
#### GraphQL
- https://graphql.org/
- Open-source query language for API's
- **Schema Definition**: Define your data schema using GraphQL's type system
- **Flexible Queries**: Clients can request only the data they need reducing payload sizes and improving performance
- Initial developed by Facebook
- AppSync enables real-time updates through GraphQL subscriptions
- **WebSocket**: AppSync uses WebSocket to push real-time updates to connected clients
- **Use Cases**: Chat applications, live notifications, collaborative editing
- AppSync provides offline access and automatic data synchronization when devices reconnect
- **Conflict Resolution**: Define conflict resolution strategies to handle data consistency issues
- **Local Datastore**: AppSync caches data locally on the client, allowing for offline data access and synchronization
#### Data Source Integration
- AppSync integrates with various AWS data sources for seamless data access
- **Supported Data Sources**: Amazon DynamoDB, AWS Lambda, Amazon Elasticsearch HTTP data sources
- **Data Source Resolvers**: Use resolvers to map GraphQL operations to sepcific data sources
#### Comparing AppSync and Cognito Sync
- ***AWS AppSync***: A fully managed service for building real-time and offline-capable applications with GraphQL support
- ***Cognito Sync***: A service that sunchronizes user profile data across mobile devices and the web for Amazon Cognito User Pools
- Key Differences:
  - AppSync offers more flexibility with data sources, real-time updates, and GraphQL support
  - Cognito Sync is limited to user profile data and Amazon Cognito User Pools

## 10.2 Demo

## 10.3 EventBridge
A serverless event bus that connects applicatoins through the exchange of events
#### Purpose
- Enables developer to build event driven architectures by simplifying event processing and decoupling services
- Key Concepts: Custom Event Buses, Event Rules, Event Patterns, Integration with AWS Services
#### Custom Event Buses
- Create custom event buses to organize and mange events within you application
- Seperate event buses for different environments or applicatins ***Segregation***
- Use AWS Identity and Access Management (IAM) to control access to your event buses ***Access Control***
#### Even Rules and Patterns
- Define event rules and petterns to route events to the appropriate targets
- Filter events based on specific ***Event Patterns*** within the event JSON structure
- Route events to one or more ***Targets***: , e.g.: Lambda, Amazon SNS, Amazon SQS
#### Integration with AWS Services
- EventBridge integrations with a wide range of AWS services as event sources and targets
- Services like EC2, S3, and RDS can generate events that are sent to EventBridge
- Can route events to AWS services for processing, such as Lambda, Step Functions, and SNS
#### Integration with SaaS Applications
- Supports integration with popular SaaS applications as event sources
- SaaS Partners: Salesforce, Zendesk, pagerDuty, etc.
- Streamline workflows, automate processes, and improve application responsiveness
#### Benefits, Event Driven Architecture
- Improved scalability
- Faster applicatoin response times
- Easier maintenance through decoupling of services - Key Point!!
#### Scalabiliy and Performance
- Serverless - EventBridge is a fully managed, serverless service that scales with your application needs
- High THroughput - EventBridge is designed to handle millions of events per second
- Low Latency - EventBridge provides low-latency event processing and delivery
- Keep buses seperate per application or environment
#### Demo
- Key idea, event bridge triggers a Lambda function to run daily
- His example is to get the closing price of TSLA stock everyday at a specifc time
- He has written a Lambda function to "ping" an API endpoint...
- Then uses EventBridge to execute that Lambda function every day at...9pm UTC
- Cron-job style; AWS Scheduler

## 10.4 Simplet Notification Service (SNS)
- Pubsub Service, fully managed pub/sub messaging, SMS, email, and mobile push notifications
- Fully managed messaging service for building distributed systems and applications
- Enables developers to send messages to multiple subscribers concurrently usning the publish-subscribe (pub/sub) pattern
- Topics, Message Filtering, Message Fan-out, Service Integration
- Many AWS services already use SNS
#### Filter Policies
- Default - Subscriber recieves all messages to topic
- Filter - Subscriber receives only messages that match filter
- Filter is a JSON object applied to a subscriber of a topic
- Matches on Message Attributes in a message
#### Message Durability
- SNS provides durable storage of all messages that it receives. Note: Once the message is sent, it's removed
- Publish requests are stored as multiple copies to disk
- Stored to multiple, in-region, AZs prior to API acknowledgement receipt of request
#### SNS Delivery Status
- Log delivery status of the following endpoints: Application, HTTP, Lambda, SQS
  - Note that SMS is not on this list, no gurantee of receipt
- Log entries will be sent to CloudWatch Logs
#### CloudWatch Monitoring
- SNS and CloudWatch are integrated
- Collect, view and analyze metrics for active SNS notifications
- Metrics configured are pushed to CLoudWatch every 5 minutes
- Metrics are gathered on all topics considered Active - Any topics that have activity with the last six hours
- Free (the integration is free, SNS isn't free)
#### SNS Mobile Push Notification Services
- ADM, APNS, Baidu, GCM, MPNS, WNS
#### SNS Webhook
- HTTP/S Subscription
- HTTP and/or HTTPS endpoints can subscribe to a topic
- Dtaa is sent using Post verb
- With HTTPS:
  - Specify Server Name Indication (DNI)
  - Enable Basic and DIgest Access Authentication - Added in URL

## 10.5 Simple Queue Service (SQS)
- Fully managed message queues for microservices, distributed systems, and serverless applications
- Enables developers to decouple application components and scale independently usning message queues
- Standard and FIFO queues, Message Attributes, Dead-letter Queues, Integration with various AWS services
- ***Simple***: Pretty Easy to use
- ***Queue***: Items awaiting processing
- ***Service***: AWS Service
- Secure, Durable, Highly Available, Scalable, Reliable, Standard & FIFO Queues
- Temporary repository for messages that are awaiting processing
- Allows for decoupling distributed software systems and components
#### Standard Queues
- Available in all regions
- Unlimited throughput - NEarly unlimited number of transactions per second (TPS) per action
- At-Least-Once delivery - A message is delievered at least once, more than one copy of a message is possible
- Best Effort ordering - messages may be delivered out of order
#### FIFO Queues
- N. Viginia, Ohio, Oregon, Ireland Regions
- High throughput: 3000 MPS Batching, 300 MPS no batching
- Exactly once processing: message delivered once, remains available until consumer processes and deletes it; no duplicates
- First in First Out delivery: The order messages are sent and received is strictly preserved
#### SQS At Least Once Delivery
- Messages are copied to multiple servers when added to the queue
- Server witha copy of the message may be unabailable when the message is received or deleted "Rare"
- Message can be returned again
- Applications should handle this message duplication gracefully
- If a message fails to be processed then something went wrong
#### Visibility Timeout
- Default: 30 seconds; Maximum: 12 hours
- The maximum amount of time a message will wait in the queue - Message Retention Period
- Default: 4 days; Min: 1 minute; Max: 14 days
#### Options
- message size: default 256 KB, min: 1 KB, max: 256 KB
- Delivery Delay: defualt 0 seconds, min: 0 seconds, max: 15 minutes
- Per-message timers
#### Dead Letter Queue
- Queue messages that cannot be processed successfully
- Helpful for debbugging consumers
- Configured with Redrive Policy
#### Service Side Encryption (SSE)
- SQS can encrypt messages upon queue reception
- Permits transmission of sensitive data
- Keys managed by Amazon Key Management Servcie (KMS)
- Encrypts the message body
- Does NOT encrypt: Queue metadata, Message metadata, per-queue metrics
- Dead letter queue movement does not change encryption state
#### SQS Security
- Authentication - Permission to access and manage SQS is provided by IAM
- Access Control - SQS has it's own resource based permissions system
- Uses the same language as IAM
#### CloudWatch
- Integrated

## 10.6 SQS Demo
- "SMS is push messaging"
- "SQS is pull messaging"

## 10.7 Step Functions
- Visual workflows for distributed applications
- A fully managed service for coordinating distributed applications and microservices using visual workflows
- Simplify the development and mangaement of complex applications by breaking them down into small, more manageable steps
- Key Features: State Machines, Error Handling, Service Integrations, Monitoring
#### State Machines
- State machines are used to define and execute workflows
- States represent the individual steps ina workflow:
  - Task, Choice, Wait, Fail, Succeed
- Transitions: Define how to move from one state to another based on the output of the previous state
#### AWS Service Integrations
- Step Functions integrates with a wide range of AWS services
- Service Integration Examples:
  - Lambda, DynamoDB, ECS, SNS, SWS, Glue, SageMaker
- Enable Seamless coordination of various services to build complex applications
#### Error Handling
- Robust Error Handling
- Retries: Configure retry policies for individual tasks to handle transient errors
- Catchers: Add catchers to handle specific errors and route the esecution to a different state\
#### Scalability and Performance
- Scalability: Step Functions scale automatically to handle the number of state machine executions
- Concurrent Executions: Support for millions of concurrent executions
- Throttling: Automatic handling of throttling scenarios with retries

## 10.8 Step Functions Demo


## 10.9 Kinesis
- Fully managed service for collecting, processing, and analyzing real-time, streaming data
- Purpose: Enable developers to gain insights from data as it is generated rather than waiting for batch processing
- Components: Kinesis Data Streams, Kinesis Data Firehose, Kinesis Data Analytics, Kinesis Video Streams
### Kinesis Video Streams
- Capture, process, and store video streams for analytics and machine learning
- Connect and stream from millions of devices
- Store, encrypt, and index data
- Serverless
- Build real-time and batch application streams
- Secure streaming
- Pay as you go/grow
### Kinesis Data Streams
- Analyze data streams using popular stream processing frameworks
- Accelerated log and data feed intake and processing
- Real-time metrics and reporting
- Real-time data analytics
- Complex stream processing
###### Streams
- Unit of data: data record
- Stream: group of data record
- The data records in a stream are distributed into shards
- ***Producers***: A producer puts data records into streams
- ***Consumers***: A consumer get data records from Kinesis data streams
###### Shards - Uniquely identified sequence of data records in a stream
- One or more shards = stream
- Each provides a fixed unit of capacity
- Can support up to 5 transactions per second for reads, maximum total data read rate of 2 MB per second
- Up to 1000 reocresd per second for writes Maximum total data write rate of 1 MB per second
###### Partition Key
- Groups data by shard within a stream
- Partition key determines which shard a data record belongs to
- Partition keys are Unicode strings with a maximum length limit of 256 bytes
- Application must specify a partition key when putting data into a stream
##### Kinesis Data Streams Limits
- No upper limit on the number of shards to can have in a stream
- No upper limit on the number of streams you can have in an account
- A single shard can ingest up to 1 MiB of data per second (including partition keys) or 1000 records per second for writes
- The default shard limit is 500 shards fo the following regions
  - N. Virginia, Oregon, and Ireland
  - All other regions, default shard limit is 200 shards
### Kinesis Firehose
### Data Analytics
- Analyze data streams with SQL
- Generate time-series analytics
- Feed real-time dashboards
- Create real-time metrics
### Best Practices
- Use shard level metrics
- Watch extra shard metrics in CloudWatch
- Monitor Iterator Age statistic
- Monitor ReadProvisionedThroughputExceeded metric
- Be aware of poison messages
  - A single failed message can cause a batch to fail and be retried
  - Can cause duplicate results
  - Solution 1: implement logic in Lambda function to log exception and return success so next batch is processed
  - Solution 2: implement retry and failure behaviors
    - on failure destination - send failures to SQS or SNS queue
    - Retry attempts - Control the maximum retries per batch
    - Split batch on error - split retry batch size, attempt to zero in on poison message

## 10.10 Kinesis Demo



## Practice Questions
How does Amazon Kinesis handle scalability and adaptability in terms of streaming data?

Responses
It can automatically scale to accommodate the data from millions of devices, allowing real-time processing without any intervention. - correct
It requires manual configuration each time a new device is added to the network.
It restricts the number of devices that can stream data in real-time to a maximum of 1000.
It scales only during a predetermined maintenance window set by the user.


Which of the following best describes the purpose of Amazon's Simple Queue Service (SQS)?

Responses
To enable developers to decouple application components through managed message queues. - correct
To create an environment for hosting web applications.
To create managed database connections between different AWS services.
To provide managed storage solutions for static data.



AWS EventBridge is primarily designed for:

Responses
Managing user access and permissions to AWS resources.
Deploying and managing containers on AWS.
Monitoring system health of AWS resources.
Building event-driven applications by routing events to appropriate targets. - correct


Which of the following statements best describes the primary difference between AppSync and Cognito Sync based on the provided information?

Responses
AppSync offers a method for building real-time and offline-capable applications with GraphQL support, while Cognito Sync is mainly used for synchronizing profile information across mobile devices with Cognito user pools. - correct
Both AppSync and Cognito Sync are used for real-time and offline data synchronization.
AppSync is primarily for building real-time chat applications while Cognito Sync is used for storing mobile application data.
AppSync is developed by Facebook, while Cognito Sync is developed by OpenAI.