# Preparing Application Artifacts to be Deployed to AWS

## 12.1 Cloud Formation
- A service that helps you model, provision, and manage your AWS infrastructure as code
- *"Speed up cloud provisioning with infrastructre as code"*
- Simplify the process of creating and managing AWS infrastructure, reducing manual effort and ensuring consistency
- ***Key Features***: Infrastructure as COde, Change Management, Reusable Templates, Custom Resources

#### Infrastructure as Code
- Not something you are going to repeat often
- Define your AWS infrastructre using code in the form of CloudFormatino templates
- Language: YAML or JSON
- Benefits: Version Control, Collaboration, Repeatability, Automation
- Template-based creation and deletion of resources
- Collection of resources: Stack
- Leverage: EC2, Amazon Elastic Block Store, Amazon SNS, Elastic Load Balancing, Auto Scaling
- Underlying AWS infrastructure created for you
- IAM Access Controlled
#### Concepts
- ***Templates***: JSON or YAML text file, Blueprint for the Stack, Reusable
- ***Stacks***:
- ***Change Sets***:
#### Custom Resources
- Extend CloudFormation by creating custom resources that represent AWS or third-party resources
- ***AWS Lambda***: Use AWS Lambda functions to define custom resource behavior
- ***Integration***: Custom resources are treated like any other AWS resource within CloudFormation
#### Parameters and Outputs
- ***Parameters***: Define inputs for your CloudFormatino templates to customize infrastructure deployment
- ***Outputs***: Export values from your CLoudFormation stacks to share information between stacks or with external systems
#### Change Management
- CloudFormation simplifies the process of updating and managing your infrastructure
- ***Change Sets***: Preview and validate changes before applying them to your infrastructure
- ***Roll Backs***: Automatically roll back to the previous state in case of errors during stack updates
#### CloudFormation - Stacks
- Collection of resources managed as a single unit
- Create, update, and delete Stacks
- All resources defined by the stack's AWS CloudFormation template
- Create Stack: Submit template > AWS CloudFormatoin provisions all resources
- Managed via: Console, API, CLI
#### CloudFormation - Change Sets
- Summary of your proposed changes to update a stack
- Shows how your changes might impact your running resources before implementation
#### CloudFormation - Designer
- Provides graphic representations fo rthe resources in your template
- Simplifies template authoring and editing
- Enforces some basic relationships between resources
- Provides GUI and Text at the same time
#### Drift Detection
- Detect configuration drift by comparing the actual stack resources to the expected stack resources defined in the template
- Maintain consistency and ensure infrastructure is in the desired state
- Remediation: Manually update drift resources or update the CloudFormation stack to bring resources back to the desired state
#### Cloud Formation Best Practices
- Use IAM to control access
- Reuse templates to replicate Stacks in multiple environments
- Use nexted Stacks to reuse common template patterns
- "Cloud Formation is particularly powerful"
- Do not embed credentials in your templates
- Use AWS-specific parameter types
- Use parameter constraints
- Use AWS::CloudFormation::Init to deploy software applications on Amazon EC2 Instances
- Validate templates before using them
- Manage all resources through AWS CloudFormation
- Create change sets before updating your Stacks
- Use AWS CloudTrail to log AWS CloudFormation calls
- Use revision controls to manage templates
- Update your Amazon EC2 Linux and Windows instances regularly
- CloudFormation will not *maintain* the environment, it deploys the environmnet

## 12.2 Cloud Formation Demo

## 12.3 System Manager
- https://aws.amazon.com/systems-manager/
- A service that helps you manage your AWS resources and applications in a single, unified interface
- *"Manage your resources on AWS and in multicloud and hybrid environments"*
- Simplify and centralize AWS resource management, improve visibility, and automate common operational tasks
#### Key Features
- Inventory and configuration
- Automation
- Patch Manager
- Run Command
- Parameter Store
#### Inventory and Configuration
- Collect and analyze metadata about your AWS resources to maintain an up-to-date inventory
- ***Resource Groups***: Organize resources by applications, environments, or other criteria
- ***Config Compliance***: Detect and remediate non-compliant resources using AWS Config rules
#### Run Command
- Remotely and securely execute commands and scripts on your managed instances
- ***Use Cases***: Updating software, joining instances to a domain, running custom scripts
- ***Benefits***: Simplify remote management, enforce configuration consistency, reduce manual effort
#### AUtomation
- Automate common operational tasks and processes to reduce manual effor and human error
- ***Use Cases***: Create and update Amazon Machine Images (AMIs), Apply pathces, Rotate secrets
- ***Benefits***: Save time, Improve reliability, Maintain consistent configurations
#### Parameter Store
- Securely store and mange configuration data and secrets such as passwords, database strings, and license codes
- Integration: Retrieve paramters from Parameter Store in your scripts, code or CloudFormation templates
- Benefits:
  - Centralize configuration management
  - Improve security
  - Simplify paramter updates
#### Patch Manager
- Automate the process of patching managed instances with security-related updates
- Patch Baselines: Define rules for automatically approving and applying patches
- Patch Compliance: Monitor the patch status of your instances and ensure compliance with your patching policies
#### Maintenance Windows
- Scheulde and automate routine maintenance tasks during prediefined maintenance windows
- Use Cases: Patching, Updateing software, performing backups
- Benefits:
  - Minimize disruption
  - Maintain service availability
  - Reduce operational overhead
#### Session Manager
- Securely access and managed instances without requiring bastion hosts or opening inbound ports
- Features: Encrypted Session data, Granular access control, Detailed session logs
- Benefits: Improve security, Simplify instance management, Streamline auditing
#### AWS Systems Manager Summary
- AWS Systems Manager simplifies and centralizes AWS resource managment, helping you maintain visibility, automate common tasks, and improve security

## 12.4 AppConfig
- Feature of Systems Manager
- AWS AppConfig helps you manage and deploy application configurations quickly, safely, and efficiently
- *"Configure, validate, deploy feature flags and application configuration"*
- AWS AppConfig is a managed service that simplifies the deployment, management, and rollback of application configurations
- Purpose: Enable faster, safer, and more controlled deployment of configurations to applications at runtime
- Key Features: Configuration versioning and validation, Gradual rollouts and rollbacks, Integration with AWS services
#### Configuration Versioning and Validation
- Store and manage multiple versions of you application configurations
- ***Versioning***: Maintain a history of configuration changes to track updates and revert if necessary
- ***Validation***: Ensure configurations are syntactically and semantically correct before deployment
#### Gradual Rollouts and Rollbacks
- Deploy configuration changes incrementally to minimize risk and impact on your application
- ***Deployment Strategies***: Choose between predefined strategies (e.g. linear, all-at-once) or create custom strategies
- ***Rollbacks***: Automatically revert to a previous configuration if issues are detected during deployment 
#### Integration with AWS Services
- Examples:
- AWS CodeDeploy - Deploy appliation revisions with AppConfig
- AWS Lambda - Trigger Lambda functions based on configuration changes
- Amazon S3 - Store and retrieve configuration files in S3 buckets
#### Use Cases for AWS AppConfig
- Feature flag managment
- Dynamic tuing of applicatoin performance
- Configuration based A/B testing
- Rapid response to operations isssues
#### Security and Access Control
- Secure your AppConfig resources and control access to configurations
- AWS Identity and Access Management (IAM) - Use IAM policies to grant permissions for AppConfig actions
- Encryption - Encrypt configuration data at rest and in transit


## 12.5 AppConfig Demo

## 12.6 Secrets Manager
- https://aws.amazon.com/secrets-manager/
- *"A service that helps you protect and manage secrets such as database credentials, API keys, and other sensitive information"*
- *"Centrally manage the lifecycle of secrets"*
- A service that enables you to securely store, manage, and retrieve secrets in AWS
- Purpose: Protect sensitive information, automate secret rotation, and improve security and compliance
- Key Features: Centralized secret storage, Fine-grained access control, Automatic secret rotation, Auditability
#### Centralized Secret Stoage
- Store and manage secrets in a secure, centralized location
- ***Encryption***: Secrets are encrypted at rest using AWS Key Management Service (KMS) keys
- ***Access***: Retrieve secrets programmatically using AWS SDKs or CLI
#### Automatic Secret Rotation
- Automate the process of rotating secrets to improve security and reduce the risk of data breaches
- Integration: Support for Amazon RDS, Amazon Document DB, and Amazon Redshift databases
- Custom Rotation: Define custom Lambda functions for rotating secrets for other datases or services
#### Fine-grained Access Control
- Control access to secrets using AWS Identity and Access Management (IAM) policies
- Least Privilege: Grant the minimal set of permissions needed ofr users and applications to access secrets
- Resource Policies: Define policies directly on secrets to control access across AWS accounts
#### Auditability and Monitoring
- Track and monitor access to secrets for auditing and compliance purposes
- ***AWS CloudTrail***: Record API calls made by or on behalf of Secrets Manager
- ***Amazon CloudWatch***: Monitor and set alarms for Secrets Manager events and metrics
#### Migrating to Secrets Manager
- Migrate existing secrets from other secret storage solutions to AWS Secrets Manager
- ***Migration Strategies***: Import existing secrets, replace hardcoded secrets in applications, and transition from Parameter Store
- ***Benefits***: Improve security, automate secret rotation, and centralize secret management

## 12.7 Parameter Store
- A service within Systems Manager
- Securely manage configuration data such as database connection strings, API keys, and other configuration information
- Purpose: Centralize configuration management, improve security, and simplify updates to application configurations
- Features: Hierarchical storage, Versioning, Fine-grained access control, Integration with AWS services
#### Hierarchial Storage
- Organize parameters using hierarchical paths that resemble direcotry structures
- Naming Conventions: Define a consistement naming strategy for easy management and retrieval
- Tagging: Assign metadata to parameters for improved organizatino and access control
#### Parameter Versioning
- Automatically track changes to parameter values with versioning
- Benefits: Maintain configuration history, simplify updates, enhance security
#### Parameter Store Types
- Store different types of parameters based on needs
  - `String`, `StringList`, `SecureString`, `Integer`, `Boolean`, `MapList`, `StringMap`
- SecureString: Encrypt sensitive data using AWS Key Management Service (KMS) keys
#### Service Integration
- *Parameter Store* seamlessly integreates with other AWS services, e.g.
- *AWS Lambda*, *AWS CloudFormation*, *AWS CodePipeline*

## 12.8 CodeBuild and CodeDeploy YAML
#### `buildspec.yml`
- A YAML file containing build commands and related settings used by AWS CodeBuild
- Defines build setting and commands for CodeBuild to execute
- Key Components: Version, Phases, Artifacts, Cache
#### CodeDeploy
- A fully managed deployment service that automates software deployments to various compute services
- Automate the deployment phase of your CI/CD pipeline, reducing errors and improving deployment speed
- Centralized control, deployment tracking, and support for muliptle deployment strategies
#### `appspec.yml`
- A YAML file containing deployment instruction for AWS CodeDeploy
- Defines deploymnet settings and lifecycle event hooks for CodeDeploy
- Version, OS, Files, Hooks, Permissions
#### Best Practices
- Validate YAML syntax before committing
- Use environment variables for sensitive data
- Test your buildspec.yml locally using the CodeBuild agent
#### Integrating CodeBuild and CodeDeploy
- Combine CodeBuild and CodeDeploy to create a seamless CI/CD pipeline
- ***AWS CodePipeline***: Use CodePipeline to automate the end-to-end release process, including CodeBuild and CodDeploy
- ***IAM Roles***: Ensure appropriate IAM roles are in place for CodeBuild and CodeDeploy to interact
#### Summary
- AWS CodeBuild and CodeDeploy YAML simplify the management of your CI/CD pipeline




## Practice Questions
Question 1
When using AWS CloudFormation, what is a "drift"?

Responses
A special type of AWS instance designed for high-compute tasks.
The migration of data from one AWS region to another.
A mismatch between the CloudFormation template's expected resources and the actual existing resources. - correct
A change in cost due to fluctuating AWS service prices.


Question 2
AWS Systems Manager offers a variety of services to help manage and oversee AWS resources and applications. Which of the following options accurately defines the "Session Manager" feature of AWS Systems Manager?

Responses
It enables secure access and management of instances without requiring bastion hosts or opening inbound ports. - correct
It provides automated sessions to validate and update security patches across multiple EC2 instances.
It allows users to allocate sessions for data migration between on-premises and AWS databases.
It facilitates the storage of key-value data such as passwords, database connection strings, and license codes.


Question 3
What is AWS CloudFormation primarily used for?

Responses
To monitor AWS services and provide alerts.
To deploy machine learning models on AWS.
To store large data sets in a scalable manner.
To model, provision, and manage AWS infrastructure as code. - correct


Question 4
Which of the following best describes the purpose of using AWS CloudFormation "change sets"?

Responses
To migrate resources from one AWS region to another.
To monitor and log access to AWS resources.
To obtain a summary of proposed changes to a stack before applying them. - correct
To automatically update all resources within a CloudFormation stack.


Question 5
AWS Systems Manager provides a suite of tools to help manage and automate tasks for AWS resources and applications. Which of the following statements best describes one of the features of AWS Systems Manager?

Responses
It provides the capability to run a single command across multiple EC2 instances simultaneously without having to individually access each instance. - correct
It helps in data migration from on-premises databases to Amazon RDS without any manual intervention.
It allows you to automatically rotate access keys for all IAM users in an AWS account.
It offers a unified interface for real-time monitoring of AWS Lambda functions and API Gateway endpoints.