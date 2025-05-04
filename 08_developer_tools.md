# 8. Developer Tools
- These are the services that don't exactly fit in a CI/CD pipeline
- Development and Deployment Pipeline
- Software release processes

## 8.1 AWS Amplify
#### Background and Context
- Set of tools and services for building scalable and secure cloud-powered applications
- "Easy Button"
- "Build full-stack web and mobile apps in hours.  Easy to start, easy to scale."
- Amplify command line interface
#### What is AWS Amplify
- Development platform for building full-stack web and mobile applications with a focus on simplicity and ease of use
- **Purpose**: Helps developers create and deploy scalable, secure applications in the cloud, backed by AWS services
- **Key Features**: Amplify Console, Amplify CLI, Amplify Libraries and Amplify UI Components
- *"Can get an app up and running in minutes (but very important to understand what it is doing)"*
#### Features
- **Unified Workflow**: Amplify provides a single workflow for frontend and backend development, deployment, and testing
- **Reusable Components**: Amplify provides a set of pre-built UI components and libraries that can be easily integrated into your application
- **Backend Services**: Amplify provieds a set of pre-configured backend services, such as authentication, API, storage, and analytics, that can be easily integrated with your frontend application
- **Scalability**: Amplify provides a scalable and serverless backend architecture that automatically scales based on demand.
- **Security**: Amplify provides a secure development environment that ensures data privacy and compliance with industry standards.
#### Amplify Architecture
- **Frontend**: Amplify supports multiple frontend frameworks, such as React, Angular, Vue, and React Native, and provides a set of pre-built UI components and libraries
- **Backend**: Amplify provides a serverless backend architecture based on AWS Lambda, AWS API Gateway, AWS AppSync (GraphQL for storing and retrieving data), AWS DynamoDB, AWS S3, and other AWS services.
- **Amplify CLI**: CLI enables developers to create and configure backend services, deploy frontend applications, manage the entire development lifecycle.
  - **Interface**: Interact with Amplify services and manage your applications's backend resources
  - **Integration**: Seamlessly integrate with AWS services, such as AWS AppSync, Amazon S3, and AWS Lambda
  - **Configuration**: Easily configure and manage your application's resources, authentication, and authorization
- **Amplify Console**: Web-based console
  - Enables continuous deployment and hosting of your frontend and backend applications
  - Features: Automatic deployments, Custom domains, SSL certificates, Version control
  - Provides quick and easy deployment and management of your application
#### Authentication and Authorization
- Secure by default: Amplify provides build-in support for secure authentication and authorization
- Integration: Connect with popular identiy providers, such as Amazon Cognito, Facebook, and Google
- Role-based Access Control: Define and enforce fine-grained access control policies for your applications's resources
#### Amplify Libraries
- **Framework Support**:
  - Many popular web and mobile frameworks:
    - Swift, Android, Java, Kotlin, JavaScript, React Native, Flutter, Angular, Vue, Hugo, Jekyll, Gatsby
  - **Authentication**: Add secure sign-up and sign-in to your applications using pre-build components
  - **API Integration**: Connect your application to serverless functinos, RESTful APIs, or GraphQL endpoints with ease
- **Storage**:
  - Backend service provided by Amplify
  - Enables secure and scalable storage for your application data
  - Supports various storage options: **S3**, **AWS DynamoDB**, **AWS Aurora**
  - Provides a simple and unified API for storage management
#### Amplify UI
- **Pre-built Components**: Use pre-built UI components for common application features, such as authentication and file uploads
- **Customizable**: Easily customize the look and feel of the UI components to match your application's design
- **Cross-platform**: Amplify UI components work seamlessly across web and mobile platforms
#### Amplify Analytics
- Backend service provided by Amplify that enables real-time analytics and user engagement tracking in your application
- Supports/Provides
  - Amazon Pinpoint: Track user engagement and usage patterns iwth Amazon Pinpoint
  - Custom Metrics: Capture custom application metrics and analyze user behavior to improve your application
  - Performance Monitoring: Monitor your application's performance and identify areas for optimization
#### Further Reading
- https://docs.amplify.aws/
- *"Not going to be tested in depth on this, but it is good to be familiar"*

## 8.2 Demo
- ```sudo npm install -g @aws-amplify/cli```


## 8.3 AWS Cloudshell
- Blowser-based shell environmnet, Simply Linux system running in the browser
- Use it if you don't want to mess with CLI stuff or need a more secure interface (more secure than SSH keys??)
- Basically - Some software running on a container with permissions to interact with your AWS account
- Provides direct access to AWS services and resources
- Permissions shared via role; IAM policies control access to AWS CloudShell
#### Features
- 1G per persistent storage, Supports Python, Node.js and Ruby
- AWS CLI, git, python, nodeJS, etc are all pre-installed

## 8.4 AWS CodeGuru
- AI powered service that helps you identify and fix code issues and optimize the perfomrance of your applications
- Machine Learning powered service
#### Key Features
- CodeGuru Reviewer
- CodeGuru Profiler
#### Currently Supports
- Java, Python, more coming
- Django, Flask, AWS Lambda, Amazon ECS, Amazon 
#### Access Control
- Use AWS IAM
- Using through code commit is seamless
![alt text](../../___media/training/aws-cert-dev/8_devloper_tools.md/image.png)

## 8.5 AWS Cloud9
- Integrated Development Environment (IDE), on the cloud
- Eliminate need for local development environments; *"Known good environment"*
- Pre-configured environment; However, you are working through a web browser
- ***Architecture***: Browser, AWS Management Console, Cloud9 Environment, AWS Services
- ***Language Support***: Python, JavaScript, Java, Ruby, and more...
- *"Pretty full featured"* IDE

## 8.6 AWS CodeStar
- Project Management Tool
- "An Easy button for the creation of an application"
- Quickly develop, build, and deploy applications on AWS
- ***Key Features***: Project Templates, CI/CD Pipeline, Team Collaboration, Integrated Development Environment
- Sets up a fully managed CI/CD pipeline using AWS CodeCommit, AWS CodeBuild, AWS CodeDeploy, and AWS CodePipeline
- Codestar createst the YAML files for you (doing this manually can be fairly complicated)
- Project Management Tool, Highly scalable
- Redundant and durable architecture

## 8.7 AWS CodeCommit
- Git repository with tight integration to AWS services
- Store any file type, no repo size limits
- Works with existing Git tools and IDEs with Git support

## 8.8 AWS CodeBuild
- A fully managed build service that compiles your source code, runs tests, and produces artifacts for deployment
- `buildspec.yaml`
- Source Providers: S3, AWS CodeCommit, Bitbucket, GitHub, GitHub Enterprise
- Windows or Ubuntu

## 8.9 AWS CodeDeploy
- Takes packaged artifact and deploys to various compute services (Amazon EC2, AWS Lambda, on-premise)
- `appspec.yaml`
- AWS Service Integration: AWS CodePipeline, AWS CodeCommit, Amazon S3
- Takes code from S3 and puts it on a server

## 8.10 AWS CodePipeline
- CI/CD deployment of code
- Source, Build, Test, Deploy
![alt text](../../___media/training/aws-cert-dev/8_devloper_tools.md/image-1.png)

## 8.11 Demo
![alt text](../../___media/training/aws-cert-dev/8_devloper_tools.md/image-2.png)
- Various developer tools tied together with Codestar
- S3 is the artifact storage
- Code repository: Can use AWS CodeCommit or GitHub...very cool!
![alt text](../../___media/training/aws-cert-dev/8_devloper_tools.md/image-3.png)
- Terminate everything...in the codestar service > Projects, delete

## 8.12 Code Artifact
- Fully managed artifact repository service that enables you to store, publish, and share packages
- Centralized location for storing and sharing packages across teams and Projects
- Simplifies dependency management
#### Artifact ####
- Any file or set of files that are produced as part of the software development, build, or deployment processes
- Pay as you go service, will proxy, will cache
- Outputs of a process used in subsequent stages of devlopment, testing, or deployment
- Artifact Examples: Compiled Code, Configuration Files, Documentation, Scripts, Test reports or logs
- Part of the overall tool set in Developer Tools
#### Code Artifact Features
- ***Data Protection***: AWS CodeArtifact encrypts data at rest and in transit, ensuring the security of your packages and metadata
- ***Fine-grained Access Control***: Manage access to your repositories using AWS Identity and Access Management (IAM) policies
- ***Auditbility***: Track access and usage of your repositories with AWS CloudTrail logs
- ***Repository Replication***: Cross-region replication, disaster recover, data durability
- Support for popular package formats (Maven, Gradle, npm, yarn pip, twine)
#### CodeArtifact Benefits
- Centralized Pakcage Management provides centralized amnagement of packages and dependencies
- Cost effective Pay-as-you-go service
- Easily integrated with different tools and platforms, management of resources from a single location
- ***Security***: IAM based access control, Encryption of data at rest and in transit, support for private packages




## Practice Questions
Question 1
Which of the following statements about AWS Cloud9 is NOT true?

Responses
AWS Cloud9 integrates directly with other AWS services and has the command line interface pre-installed.
AWS Cloud9 provides a cloud-based integrated development environment accessed via a web browser.
*** AWS Cloud9 is primarily designed for mobile application development and is optimized for smartphone use. - correct
AWS Cloud9 supports collaborative features, allowing multiple developers to work on the same code base with real-time updates.



Question 2
Which of the following best describes AWS Amplify?

Responses
A web browser tool exclusive for deploying mobile applications.
An interface to interact with AWS Lambda functions only.
*** A developer tool for creating secure cloud-powered serverless applications. - correct
A security software to protect AWS instances.



Question 3
Which of the following best describes AWS CloudShell?

Responses
An enhanced version of AWS Lambda that provides in-browser code execution.
A built-in AWS service that helps in database migrations.
An AWS service exclusively for managing EC2 instances.
*** A service that provides a browser-based terminal to run and manage AWS commands without configuring SSH. - correct



Question 4
Which of the following statements best describes AWS CodeStar?

Responses
CodeStar exclusively focuses on machine learning application development.
*** CodeStar is a project management tool that simplifies the creation of an application within AWS, integrating services like CodeCommit, CodeBuild, CodeDeploy, and CodePipeline. - correct
CodeStar is primarily a continuous integration service focusing only on deploying applications.
CodeStar is a service for creating Lambda applications but doesn't support web application development.



Question 5
Which of the following best describes the primary function of Amazon CodeGuru?
Responses
A tool for generating visualizations of application metrics.
*** An AI-powered service designed to review and optimize code by providing ML-powered recommendations. - correct
A tool for monitoring the runtime of applications and presenting detailed reports.
An AWS service to provide data protection compliance checks such as SOC, ISO, and PCI DSS.
