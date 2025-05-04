# 5. Developing Code for Applications Hosted on AWS

## 5.1 Architectural Patterns, Idempotency, Stateful vs Stateless
#### Common Architectural Patters
- **Client-server**:
  - Multiple clients connect to a single server to request 'services'
- **Layered**: Components organized into horizontal layers (presentation, application, data, database)
  - Each layer performs a sepcific role within the application
  - Lyaers are connected by well-defined interfaces
- **Model, View, Controller (MVC)**
  - ***Model*** represents the application's data and logic
  - ***View is*** responsible for displaying the data to the user
  - ***Controller*** handles the user's input and controls the flow of data bettween ***model*** and ***view***

#### Lambda (high level view)
- A serverless compute service that runs your code in response to events
- No server management, automatic scaling and pay-per-use pricing
- Use Cases: Data processing, web backends, event-driven architectures, and more

#### Common Architectural Patterns in AWS
- ***Event Driven***: Lambda functions are triggered by events from AWS services, such as S3, DynamoDB, API Gateway
- ***Microservices***: Build decoupled, modular components that can be developed, deployed, and scaled independently
- ***Orchestration***: Use AWS Step Functions to manage complex workflows by chaining together many Lambda func's

#### Idempotency (in AWS Lambda)
- Ensuring that multiple executions of a function with the same input produce the same result without causing unintended side effects
- Improve reliability, simplify error handling, and maintain consisitency in dristributed systems
- Common User Cases: API design, retry mechanisms, and data processing

#### Stateful vs. Stateless Concepts
- Stateful: Systems that maintain the state of a user or session across multiple interactions
  - *Pros and Cons*: Stateful systems can provide better user experiences but may require more complex management
- Stateless: Systems that do not store any state information and treat each interaction as independent
  - *Pros and Cons*: Stateless systems are easier to scale and maintain

#### Lambda and State Management
- Stateless by default - do not store any state information between invocations
- External state storage - Use services like DynamoDB, S3, RDS to store and manage state information
- ***Stateful Architectures***:
  - AWS Step Functions - Orchestrate Lambda functions in stateful workflows, maintaining state between invocations
  - ElastiCache - Utilize in-memory data stores like Redis or Memcached for fast, temporary state storage between Lambda invocations
  - Considerations: Balance the trade-offs between stateful and stateless architectures based on your application's requirements and constraints

## 5.2 Serverless Application Model (SAM)
#### What is SAM?
- Framework for developing, deploying, and managing serverless applications on AWS
- ***Benefits***: Simplify deployment, enhance local testing, and manage resources more efficiently
- ***Components***: SAM template, SAM CLI, SAM policy templates

#### SAM Template
- A ***YAML*** or ***JSON*** configuration file that defies your serverless application and it's resources
- **YAML**: "Yet Another Markup Language"
- **AWS CloudFormation**: SAM templates are an extension fo AWS ClouFormation templates
- Components: Global, Resources, Parameters, Outputs

#### SAM CLI
- A Command Line Interface (tool) for developing, testing, and depolying Serverless Application Model (SAM) applications
- Features: local testing, debugging, packaging, and deploying
- Integration: Works seamlessly with AWS services like AWS Lambda, Amazon API Gateway, etc.

#### SAM Policy Templates
- Predefined AWS Identity and Access Management (IAM) policy templates to streamline permissions management
- **Benefits**: Simplify and standardize IAM policies, reduce human errors, and improve security
- **Examples**:
  - ***AWSLambdaBasicExecutionROle***
  - ***AmazonDynamoDBFullAccess***
  - ***AmazonS3ReadOnlyAccess***

#### Local Testing and Debugging
- **SAM Local**: Use the SAM CLI to run and test your serverless application locally in a Lambda-like environment
- **Event Simulation**: Simulate API Gateway or other event sources to trigger your Lambda function
- **Debugging**: Attach debuggers to your Lambda function for easier troubleshooting

#### Packaging and Deployment
- **SAM Package**: Automates the proecss of uploading your applicatino code to Amazon S3 and generates a new SAM template for deployment
- **SAM Deploy**: Deploys the generated SAM template, creating or updating the necessary AWS resources

#### SAM Best Practices
- **Code Organization**: Use a modular approach to organize your application code and resources
- **Monitoring**: Integrate with Amazon CloudWatch and AWS X-Ray for monitoring and tracing
- **Security**: Follow the principle of least privilege and use managed policies when possible

#### Integrating with AWS Services
- Build powerful serverless applications by integrating SAM with other AWS services
- Example AWS Services: API Gateway, DynamoDB, S3, SNS, SQS, Step Functions, ...
- Seamless Integration: AWS SAM is designed to work seamlessly with these services, making it easy to create end-toend servesrless applications

#### Conclusion and Further Reading
- AWS SAM simplifies serverless application development, testing, and deployment on AWS
- By following best practices and leveraging AWS services, you can build powerful, scalable, and efficient serverless applications
- Further Reading:
  - AWS SAM Developer Guide: https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/what-is-sam.html
  - AWS SAM GitHub Repository: https://github.com/aws/serverless-application-model
  - AWS Well-Architected Framework: https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html

## 5.3 SAM CLI Demo

## 5.4 AWS SDKs and APIs

#### What is a Software Development Kit (SDK)?
- Collections of libraries and tool
- Assist with AWS service integration in your preferred programming language
- **Key Features**: Simplified API interactions, automatic error handling, and efficient resource management
- Supported Languages: C++, Go, Java, JavaScript, Kotlin, .NET, Node.js, PHP, Python, Ruby, Rust, Swift

#### What is an API (Application Program Interface):
- Sets of rules and protocols that enable communication between software components
- **REST**: **R**epresentational **S**tate **T**ransfer
- **RESTful APIs**: AWS APIs follow the REST architecture stule utilizing standard HTTP methods (*Get*, *Put*, *Post*, etc.)
- **AWS API Gateway**: A managed service to create, publish, and manage APIs for your applications

#### Getting Started with AWS SDKs
- **Installation**: Install the SDK for your preferred programming language using package managers like npm, pip, or Maven
- **Configuration**: Set up AWS credentials and configure the SDK to connect to the appropriate AWS region (need programmatic credentials)
- **Usage**: Import hte required AWS service client, create instances, and interact with AWS services programmatically through your application code

#### Features
- **AWS Service Clients**: Interact with individual AWS services through the SDK
- **Automatic Retries**: SDKs handle request retries for intermittent errors, improving application reliability
- **Pagination**: Easily manage large result sets using build-in pagination support
- **Authentication**: Automatically sign requests with AWS credentials to ensure secure communication

#### Using AWS APIs
- **Direct API Calls**: Interact with AWS services by making direct HTTP requests, typically using RESTful methods (GET, POST, PUT, DELETE)
- **Authentication**: Sign API requests using AWS signature version 4
- **Rate Limiting**: Be mindful of API rate limits and implement proper error handling for rate-limiting requests

#### Best Practices for AWS SDKs and APIs
- Error Handling: Implement proper error handling and retry mechanisms for transient errors
- Performance: Use connection pooling and optimize Api calss for better performance
- Security: Follow the principle of least privilege and avoid embedding AWS cerdentials in application code

#### More notes...
- All services offer direct API access
- SDKs talk to these direct APIs - reason these exist!!
- SDKs higher level entry into AWS API services
- All services have API access, and how to use it is covered in the documentation
- Anything you can do in SDK/Console, you can do via Query API
- AWS SDKs and APIs enable developers to build powerful and efficient cloud applications on AWS
- Following best practices and leveraging the full potential of AWS SDKs and APIs will lead to ***more robust and secure applications***
- Further Reading:
  - AWS SDK Docuemntation - See particular language (Java, C++, Python, etc.)
  - AWS API Reference
  - AWS Developer Tools: https://aws.amazon.com/developer/tools/

#### **AUTHPARAMS**
- Authentication, AWS API
- Signs API requests
- Provides identification of who is requesting
- Signature consists of access key and secret access key
- CLI and SDK sign requests for you automatically
- Prevents data manipulation in transit and protects against replay attacks

#### AWS SDK - You do need to package and include the SDK with your application


## 5.6 AWS Cloud Development Kit (CDK)
#### What is CDK??
- **AWS CDK**: A powerful framework for defining cloud infrastructure in your favorite programming language
- Another option for developing Serverless applications besides SAM CLI, SAM Model
- An open-source software development framework for definint cloud infrastructure in code and provisioning it through AWS CloudFormation
- Use familiar programming languages, create reusable components, and utilize pwoerful abstractions
- Support Languages: TypeScript, JavaScript, Python, Java, C#
- Deployment done thorugh ***AWS Cloud Formation***

#### CDK Concepts
- **Constructs**: Basic building blocks of AWS CDK applications, which represent AWS resources or gruops of resources
- **Stacks**: Units of deployment that contain one or more constructs and are deployed using AWS CloudFormation
- **App**: A collection of one or more stacks, representing your entire application

#### Getting Started with CDK
- **Installation**: Install AWS CDK using npm (Node.js Package Manage) or other package managers
- **Initialization**: Initialize a new CDK project using the "cdk init" command and choose your preferred programming language
- **Development**: Define your cloud infrastructure using Constructs and Stacks

#### Writing Constructs and Stacks
- **Define Constructs**: Create resources or group resources together by extending the Construct class
- **Create Stacks**: Extend the Stack class, add constructs to the stack, and define dependencies between resources
- **Compose Apps**: Add multiple stacks to your app, encapsulating different parts of your cloud infrastructure

#### AWS CDK Libraries
- **AWS Construct Library**: A collection of constructs that represent AWS resources and services
- **High-level constructs (L2)**: Provide convenient abstractions and sensible defaults for common use cases
- **Low-level constructs (L1)**: Provide direct access to AWS CloudFormation resources

#### Best Practices
- Organize your CDK code using a modular approach, separating concerns and improving maintainability
- Create reusable constructs and share them across your organization or the wider dcommunity
- Follow the principle of least privilege and use AWS best practices for resource configuration

#### CDK Ecosystem
- AWS Solutions COnstructs: `github/awslabs` A library of vetted, multi-service architecture patterns for common use cases
- AWS CDK Patterns: A collection of open-source serverless patterns for AWS CDK: cdkpatterns.com
- Community Contributions: Explore here for community developed constructs, etc.

#### Further Reading
- AWS CDK simplifies cloud infrastructure management, use familiar programming languages and powerful abstractions
- AWS CDK Developer Guide: https://docs.aws.amazon.com/cdk/v2/guide/home.html
- AWS CDK API Reference


## Practice Questions
Question 1
Which of the following is NOT a component of AWS SAM?

Responses
SAM Template
SAM CLI
SAM Debugger
Policy Templates


Question 2
How can idempotency be achieved in Lambda's design?

Responses
Increase the execution time of the Lambda function
Use UUIDs for tracking requests to prevent duplicate processing - correct
Use a stateful approach for all functions
Always use POST method in APIs


Question 3
Which statement best describes the Serverless Application Model (SAM) provided by AWS?

Responses
SAM is an AWS service for monitoring serverless applications.
SAM is a proprietary tool used to package AWS applications.
SAM is an open-source framework for building serverless applications on AWS. - correct
SAM is an open-source framework for deploying applications on AWS.


Question 4
Which of the following is NOT an architectural pattern discussed in relation to AWS Lambda?

Responses
Layered
Client-server
Round-robin - correct
MVC


Question 5
Which of the following statements is true regarding AWS SDKs and APIs?

Responses
The AWS SDKs do not handle rate limiting for you.
AWS does not offer direct API access to their services.
SDKs allow developers to interact with AWS services programmatically. - correct
AWS services can only be accessed through the web console.