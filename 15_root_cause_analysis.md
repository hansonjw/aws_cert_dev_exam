# Root Cause Analysis and Code Instrumentation

## 15.1 Cloudwatch and Cloudwatch Logs
- https://aws.amazon.com/cloudwatch/
- *"Observe and monitor resources and applications on AWS, on premises, and on other clouds"*
- Use CloudWatch and CloudWatch Logs to optimize monitoring logging, and automation in your AWS infrastructure
- A monitoring and observability service that collects data and provides actionable insights
- Monitor resources and applications, troubleshoot issues, and optimize performance
- Features: Metrics, Dashboards, Anomaly Detection, Alarms, Events
- "CloudWatch is an umbrella service that includes many things, including CloudWatch Logs, CloudWatch Metrics, etc."
- "CloudWatch is a very large service with many, many features"
#### CloudWatch Logs
- ***A log management service that collects, stores, and analyzes log data***
- Centralize logs, analyze trends, and troubleshoot issues
- Features: log groups, log retention, log streams, log insights
- Standard Out / Standard Error from Lambda functions go here
#### CloudWatch Metrics
- Time ordered data points representing the performance of AWS resources
- Types: Built In, Custom metrics
- Metric Retention: High-resolution (up to 1 second), Extended retention (up to 15 months)
#### CloudWatch Alarms
- Notifications triggered bny metric thresholds
- Automate actions and respond to changes in your AWS environment
- Actions: Send Notifications, Trigger Auto Scaling, Instance Actions (Stop, Terminate, Reboot, Recover)
#### CloudWatch Dashboards
- Customizable and shareable visualizations of CloudWatch data
- Monitor and visualize key performance indicators (KPIs) and trends
- Features: Support for mulitple widgets, Cusomizable time rnages, Cross-account dashboards
#### CloudWatch Events
- A stream of events representing changes in your AWS environment
- Respond to changes and automate actions using rules and targets
- Targets: AWS Lambda, Amazon SNS, AWS Step Functions...
#### CloudWatch Anomaly Detection
- Machine learning-based detection of abnormal metric behavior
- Identify trends, forecast future values, and set more accurate alarms
- Features: Band visualization, dynamic thresholds, automatic model updates
#### CloudWatch Log Groups and Streams
- Log Groups: Containers for related log streams
- Log Streams: Sequences of log events from a single source
- Log Retention: Configurable retention period for each log groups
#### CloudWatch Log Insights
- A log analysis tool that enables fast and interactive querires
- Analayze logs, troubleshoot issues, and generate reports
- Features: Query language, visualizations, query history
#### Custom Alerts with CloudWatch Alarms
- Set custom threshold for metrics to triggler alarms
- Create an alarm for high CPU usage or low free memory
- Use anomaly detection for dynamic thresholds
- Combine multiple metrics for more accurate alerts
#### Auto-scaling with CloudWatch Alarms
- SCale your infrastructure atomatically based on CloudWatch alarms
- Scale EC2 instances of DynamoDB thorughput based on demand
- Use target tracking scaling policies
- Set cooldown periods for efficient scaling
#### Monitoring and Logging Best Practices
- Centralize logs with CloudWatch Logs for easier analysis
- Set up alarms for critical metrics and events
- Use dashboards to visualize trends and KPIs
#### Security and Compliance
- **Encryption**: Enable encryption for log data at rest and in-transit
- **IAM**: Use AWS Identity and Access AManagement (IAM) to control access to CloudWatch and CloudWatch Logs
- **Retention Policies**: Set appropriate retnention policies for logs and metrics to meet compliance requirements
- **Audit Trail**: Monitor and analyze API calls with *AWS CloudTrail* for auditing purposes

## 15.2 CloudWatch Demo

## 15.3 SDK Exceptions and HTTP error codes
- AWS SDKs help developers build, deploy, and manage applications in AWS
- AWS SDK *"Tools for developing and managing applications on AWS"*
- A set of libraries and tools to help developers build, deploy, and manage applications in AWS
- Simplify the development process and enable seamless integration with AWS services
- SDKs are available for multiple programming languages: Java, Python, JavaScript, .NET, Go, Rust (not an exhaustive list)
#### AWS SDK Exceptions
- Exceptions raised by the SDK when an operation encounters and error
- Provide a way to handle errors gracefully and ensure application stability
- Service-specific exceptions, Client-side exceptions, Server-side exceptpions
#### AWS SDK Client-Side Exception
- Exceptions raised when there's an error on the client-side (e.g. invalid parameters, network issues)
- AWS SDK for Java - AmazonClientException
- Check for invalide parameters
- Handles network errors
- Add retry logic
#### Server Side Exceptions
- Exceptions raised when raised when there's an error on the server-side (e.g. service unabailable, access denied)
- Example: AWS SDK for Java - AmazonSErviceException
- Handle service-specific errors
- Add/use exponential backoff and retry logic
- Ensure proper authentication and authorization
- *"You sent a request to Amazon and AWS sent back and exception"*
- Common AWS Error Codes: 400 Bad Request, 403 Forbidden, 404 Not Found, 500 Internal Server Error
#### Handling HTTP Error COdes in AWS SDKs
- Check the error code return by the exception
- Handle common error codes like 400, 403, 404, 500
- Implement/employ appropriate retry logic and backoff strategies for transient errors
#### Best Practices
- Use proper exception handling techniques in your code
- Implement/use retry logic with exponential backoff to handle transient errors
- Monitor and log exceptions and errors to troubleshoot issues and improve application stability
- Refer to the documentation for each AWs service to understand the possible exceptions and error codes
#### Demo

## 15.4 X-Ray and Service Maps for X-Ray
- Use AWS X-Ray and Service Maps to analyze and optimize your application's performance and troubleshoot issues effectively
- AWS X-Ray: *"Analyze and debug production and distributed applications"*
- A distributed tracing service that helps developers analyze and debug applications
- Provide insight into application performance, identify bottlenecks and troublehsoot issues
- Key Components: Traces, Service Maps, Segments
#### Segments and Traces
- ***Segments***: Individual units of work that capture the details of an operation within your application
- ***Traces***: A collection of segments representing a request's path through your application
- ***Example***: An HTTP request to a microservice generates a trace containing segments for each service involved in processing the request
#### Getting Started with AWS X-Ray
- SDK - Use the AWS X-Ray SDK to instrument your application code
- X-Ray Agent - Install the X-Ray daemon or agent to collect segment data and send it to the X-Ray service
- AWS Integration - Integrate with various AWS services, e.g.: *Lambda*, *API Gateway*, *Elastick Beanstalk*
#### AWS X-Ray Sevice Maps
- Visual representations of the components fo your application and thier interactions
- Help developers understand the architecture of thier applicatinos and identify performance issues
- Features: Real-time data, Customizable views, Anomaly detection
- Automatic - AWS X-Ray automatically generates service maps from trace data
- Custom - Use the AWS X-Ray console or API to create custom service maps based on specific criteria
#### Interpreting Service Maps
- Nodes - Represent individual services or resources in your application
- Edges - Represent the connections between services indidcating the flow of requests
- Colors and Metrics - Use color coding and metrics like response time and error rates to identify potential issues
#### Troubleshooting with X-Ray
- Trace Filtering - Filter and search for specific traces based on criteria like error codes, response times, or custom annotations
- Trace Analysis - Drill down into individual traces to understand the root cause of issues and bottlenecks
#### Best Practices
- Instrument all componnents of your application, including third-party librarires and services
- Use custom annotations and metadata to add context to your traces
- Set up alarms and notifications based on X-Ray metrics and anomaly detection
- Regularly review service maps and trace data to identify opportunities for optimization
#### Demo

## 15.5 Cloud Trail
- *"Track user activity and API usage"*
- ***A web service that records AWS API Calls for you account and delivers log files to you***
- Enable governance, compliance, operational auditing, and risk management of your AWS account
- Features: Event History, Continuous Monitoring, AWS Service Integration, Security ANalysis
#### CloudTrail Event Types
- Management Events - Capture control plane operations, such as creating or modifying AWS resources
- Data Events - Caputre data plane operations, such as S3 object level actions or Lambda function invocations
- Insight Events - Detect unusual activity and identify potential security issues
#### CloudTrail Event History
- Default Retention - 90 days of management events
- Serach and Filter - QUickly find specific events based on various criteria
- Use Cases - Troubleshooting, security analysis, and compliance verification
#### Configuring AWS CloudTrail
- Trails - Define which events to record, where to store logs, and apply additional settings, such as retention period
- Log File Encryption - Protect log files using AWS Key Management Service (KMS)
#### CloudTrail Insight and Anomaly Detection
- Identify unusual activity in your AWS account based on CloudTrail event data
- Proactively detect security reisks and operations issues
- Console sign-in failures, API calls from unfamiliar locatins, Unusual resource create rates
#### Monitring and Alertin with CloudTrail and CloudWatch
- CloudWatch Metrics - Create custom metrics and dashboards based on CloudTrail data
- CloudWatch Alarms - SEt up alarms and notifications based on specific event patterns or thresholds
#### CloudTrail Best Practices
- Enable CloudTrail in all AWS Regions
- Create separate trails for different purposes (Security, Auditing, Compliance)
- Regularly review and analyze CloudTrail logs
- Implement least privilege access for CloudTrail log access


## Practice Questions

Question 1
When using the AWS SDK, what type of exception is typically raised when there's an error on your side, such as an invalid parameter or network issues?

Responses
Server-side exception
HTTP error code
Service-specific exception
Client-side exception - correct


Question 2
Which AWS service can you use to trigger actions and automate responses based on events and changes in your AWS resources?

Responses
AWS CloudWatch
AWS CloudTrail
AWS Lambda - correct
AWS SNS (Simple Notification Service)


Question 3
What is the key benefit of using AWS CloudWatch Logs in a cloud-based infrastructure?

Responses
Creating and managing AWS resources.
Storing and analyzing log data generated by AWS services. - correct
Real-time monitoring of AWS resources.
Automating the deployment of AWS services.


Question 4
What is the primary purpose of AWS CloudTrail?

Responses
To automatically manage serverless functions in AWS Lambda.
To monitor and log changes to your AWS account. - correct
To provide detailed logs of API calls made within your Lambda functions.
To track the usage of EC2 instances in your AWS environment.


Question 5
What is the primary purpose of AWS X-Ray in a distributed application?

Responses
To generate audit trails of actions in your AWS account.
To provide detailed logs of API gateway interactions.
To automatically manage serverless functions in AWS Lambda.
To instrument your code and create Service Maps for analyzing performance and troubleshooting issues. - correct