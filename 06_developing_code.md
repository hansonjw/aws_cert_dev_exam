# 6. Developing Code in AWS

## Overview
##### AWS Lambda
- Serverless Compute Service
- Runs code in response to events

#### Elastic Beanstalk
- Fully mananged service
- Deploy and run applications in multiple languages

## 6.1 Lambda
- Serverless compute service that runs code in response to events
- **Benefits**: No server management, automatic scaling, pay-per-use pricing
- **Use Cases**: Data processing, API backends, and microservices
#### Event Driven Architectures
- Architectures that respond to events generated systems or users
- Improved sclability, reduced coupling between components, real-time resonsiveness
- **Key Components**: Event producers, Event consumers, Event routers
- Containers that can be copied and run multiple times concurrently
#### Function Basics
- **Function Code** - Custom code written in a supported runtime (Python, Node.js, Java, etc.)
- **Handler** - The entry point of your Lambda function
- **Execution Role** - The IAM role that defines the permissions for your function
#### Lambda Highlights
- Automatic: Scaling, Code Monitoring, Logging
- Language Support: Node.js, Python, Java, C#, Go
- Lambda functions can execute base on: Events, Amazon API Gateway (HTTP call), API Calls, Alexa

#### Context/Limitations/Background
- Lambda functions are launched into a container
- First Execution Latency
- Container "Freeze/Thaw" on subsequent executions
- No reuse guarantee
- Containers run on Amazon Linux
- Container provides 500 MB of additional disk space: `/tmp` directory, Transient Cache
- User specified max memory and execution time
- Intra-=region concurrent execution limit: 1000 (Can request increase)
#### Lambda Event Sources
- ##Event Source##: AWS services or custom applications that trigger Lambda functions
- ##Examples##: S3, DynamoDB, SNS, API Gateway, and custom applications
- Event Types: Asynchronous, Synchronous, Poll-based
#### Lambda Function Triggers
- **AWS Service Triggers**: Configure AWS services to trigger Lambda functions automatically
- **Custom Triggers**: Use custom applications or external services to invoke Lambda functions via the AWS SDK or AWS Lambda API
- **Event Source Mapping**: Set up event source mappings for poo-based event sources, such as Amazon Kinesis or Amazon SQS

## 6.2 Asynchronous, Synchronous, and Poll-based Invocation
#### Asynchronous Invocation
- *"Fire and Forget"* - Lambda functions invoked in response to events without waiting for the function to complete
- **Error Handling**: SWS Example: Configure dead letter queues and retries for failed invocations
- **Use Cases**: Background tasks, Data processing, Event-driven workflows
#### Synchronous Invocation
- Lambda functions are invoked in response to events, and the caller waits for the function to complete
- **Error Handling**: Implement proper error handling in the function code
- **Use Cases**: API backends, Data Validation, Real-time processing
#### Poll Based Invocation
- Lambda functions are invoked by AWS services that poll data sources, such as Amazon Kinesi or Amazon SQS
- **Scaling**: Lambda scales the number of concurrent function invocations based on the volume of events in the data source
- **Use Cases**: Stream processing, Real-time analytics, Message processing
#### Security
- Execution Role - Use IAM orles with the least necessary privileges
- Network Security - Use Amazon VPC to control newtwork access and isolate your function
- Resource Policy - Control permission for invoking your Lambda function
#### Scaling
- Concurrent Executions - Lambda function scale automatically based on the number of incoming events
- Throttling - Control the scaling behavior by setting the reserved and maximum concurrency limit
- Provisioned Concurrency - Improve function performance by pre-warming a specifiied number of function instances
#### Lambda Function Monitoring
- Amazon CloudWatch - Monitor Lambda function metrics, such as invocation count, duration, and errors
  - Anything that is a `console.log`, `print`, `standard out`, etc. is shown in CloudWatch
- AWS X-Ray - Trace requests through your function for in-depth performance analysis and debugging
#### Event-driven Architectures with AWS Lambda
- Event Routing: Use Amazon EventBridge to route events between AWS services and Lambda functions
- Event Filtering: Define rules in EventBridge to filter events and trigger Lambda functions based on specific criteria
- Stateless Design: Embrace stateless design principles to ensure sclability and maintainability in your event-driven architecture
#### Best Practices
- **Idempotency**: Design Lambda functions to handle duplicate events and ensure consistent processing
- **Error Handling**: Implement proper error handling in your function code and configure retries and dead-letter queues
- **Performance Optimization**: Minimize function startup time, optimize memory settings, and reduce package size
- **Goal**: *Keep the lambda function small*
#### Documentation
- https://docs.aws.amazon.com/lambda/
- Developer Guide: https://docs.aws.amazon.com/lambda/latest/dg/welcome.html

## 6.3 Lambda Demo

## 6.4 Elastic Beanstalk
#### What is Elastic Beanstalk?
- A fully managed service that allows you to quickly deploy, manage, and scale applications in the AWS Cloud
- **Features**: Automated infrastructure provisioning, application deployment, monitoring, and scaling
- Supported Platforms: Java, .NET, PHP, Node.js, Python, Ruby, Go, Docker
- *"A 'Easy Button' service"*
- **User Manages**: Code Development
- **AWS Manages**: Capacity provisioning, load balancing, scaling, application health monitoring
#### Concepts
- Applications: A logical collection of Elastic Beanstalk components, such as environments, versions, and configurations
- Environments: A specific application deployment, with a unique URL and an associated AWS infrastructure
- Versions (Application Versions): A unique, labeled iteration of your application code, stored in Amazon S3
#### Getting Started
- Create an Application: Define a new Elastic Beanstalk application in the AWS Management Console or CLI
- Deploy an Environment: Choose an environment type (Web or Worker), a platform, and an application version to deploy
- Access and Manage: Use the Elastic Beanstalk console, SLI, or SDK to manage and monitor your application and environment
#### Elastic Beanstalk Environment Configuration
- Environment Tiers: Choose between the Web Server tier for web applications, or the Worker tier for background processing
  - Web Server = Provides some sort of web service
  - Worker = Background processing
- Configuration Templates: Save environment settings and configurations for easy reuse across mulitple environments
- Customization: Modify settings, such as instance type, auto-scaling group settings, and custom domain names
#### Deployment Strategies
- All-at-once - Update all instances simultaneously, causing a brief downtime
- Rolling - Update instances in batches, maintaining partial availability; Use ELB to remove unhealthy hosts from service
- Rolling with Additional Batch -Update instances in batches while launching an additional batch to maintain full capacity
- Immutable - Launch a new, full set of instances with the new version, then swap them with the old instances
#### Monitoring and Logging
- Amazon CloudWatch - Monitor key metrics, such as CPU utilization, latency and request count
- Elastic Beanstalk Health Dashboard - View the health status of your environment and receive alerts for issues
- Log Streaming - Stream logs to Amazon CloudWatch Logs for centralized log analysis and retention
#### Elastic Beanstalk Scaling
- Auto Scaling - Automatically adjust the number of instances based on demand and custom scaling policies
- Load Balancing - Distribute incoming traffic across instances using Elastic Load Balancing
#### Elastic Beanstalk Extension
- can extend to other services that aren't typically available in EB (S3)
#### Further Reading
- https://docs.aws.amazon.com/elastic-beanstalk/
- Developer Guide: https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/Welcome.html

## 6.5 Elastic Beanstalk Walkthrough

## 6.6 Code on EC2
- Objective: Learn how to use AWS IAM roles to securely run your code on Amazon EC2 instances and manage access to AWS resources
- Amazon EC2: A scalable compute service that llows you to launch and manage virtual servers in the AWS Cloud
- IAM Roles: Securely grant permissions to applications and services running on your EC2 instances, with sharing long-term AWS access keys
#### Benefits of using IAM roles with EC2
- Security: Eliminates the need to store AWS access keys on your instances, reducing the risk of unauthorized access
- Granularity: Grant specific permissions to your EC2 instances, following the principle of least privilege
- Flexibility: Easily update and rotate permissions by modifying the IAM role, without the need to redeploy your instances
#### Creating and attaching an IAM role to an EC2 instance
1. Create an IAM role - Define a new IAM role in the AWS Management Console or CLI, with the necessary permissions for you application
2. Attach the Role to an EC2 instance - During instance creation, select the IAM role you created, or attach it to an existing instance
3. Access AWS Services - Once the IAM role is attached to your EC2 instance, applications running on that instance can access AWS services using the permissions granted by the role
#### Benefits and Use Case
- AWS SDK Integration:  The AWS SDKs automatically discover and use the IAM role credentials when running on an EC2 instance
- No Explicit Credential Management: There's no need to hardcode or manage AWS access keys within your code
- Example: Shen using the AWS SDK for Python (Boto3), simply create a client or resource without specifying credentials, and the SDK will automatically use the IAM role credentials associated witht he EC2 instance
- *Don't put keys in code* - ***Use Roles***

## EC2 Demo



## Practice Questions

Question 1
What is a significant benefit of using roles with EC2 instances, especially when using SDKs?

Responses
Developers must manually input AWS keys in their code for SDK authentication.
Roles provide granular permissions to resources without the need to store AWS keys on the instance. - correct
EC2 instances with roles cannot interact with other AWS services like DynamoDB.
The EC2 instances automatically get administrator access to all AWS services.


Question 2
Which deployment strategy in Elastic Beanstalk causes an outage by shutting everything off, updating it, and then bringing it up?

Responses
All-at-once. - correct
Rolling with additional batch.
Rolling.
Immutable.


Question 3
What does the EC2 in AWS stand for and what is its primary function?

Responses
Enhanced Container Cluster - A service for managing Docker containers.
Elastic Compute Control - A service to balance traffic across servers.
Encrypted Code Creator - A service to encrypt code for AWS services.
Elastic Compute Cloud - A service that lets you launch virtual machines in the cloud. - correct


Question 4
Which platforms are supported by Elastic Beanstalk?

Responses

C++, Swift, and Kotlin.
Only Java and .NET
Java, .NET, PHP, Node.js, Python, Ruby, Go, and Docker. - correct
Just Docker.


Question 5
Which of the following best describes AWS Elastic Beanstalk?

Responses
A fully managed service that allows for rapid deployment, management, and scaling of applications. - correct
A storage service for hosting web files.
A machine learning service for generating insights from data.
A service focused on ensuring maximum security within AWS.