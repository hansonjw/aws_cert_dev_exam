# 4. Managing Sensitive Data in Application Code

## 4.1 Data Classification and Secure Credential Handling
- Data needs to be treated according to sensitivity of content
- Be aware of regulatory requirements (HIPA, etc.)

#### Serivces for Secure Credentail Handling in AWS
- **AWS Secrets Manager**: Manage and rotate secrets
- **AWS Key Management Service (KMS)**: Create, manage, and control encryption keys
- **AWS Identity and ACcess Management (IAM)**: Implement fine-grained access control for AWS resources
- **AWS Security Token Service (STS)**: Provide temporary security credentials for short-term

## 4.2 Environment Variables and Secrets Management
- Most programming languages provide a means for accessing ***Environment Variables*** that existed with the program was executed
- AWS services support ***Environment Variables*** (Lambda, ECS, Elastic Beanstalk, App Runner, etc.)
- ***Environment Variables*** Simplifies application configuration, enables seperation of code and configuration
#### Best Practices for Environment Variables
- Seperate Code and Configuration - Avoid hard coding configuration in Code
- Version Control - Track environment variables using configuration files or parameter stores
- Environment specific settings - Use different variable values for dev, staging, and prod
- Security - Do not store sensitive information in ***Environment Variables*** (use other tools such AWS secrets manager)
#### AWS Secrets Manager Fetures
- Secure Storage
- Rotation
- Integration
- Auditng and Monitoring
#### Accessing Secrets in AWS Applications
- AWS SDKs and CLI
- IAM Roles
- AWS Systems Manager Parameter Store




## Practice Questions

Question 1
Which of the following is NOT a recommended best practice for environment variables?

Responses
Separating code and configuration.
Using different variable values for deployment, staging, and production.
Storing sensitive information such as passwords in environment variables. - correct
Version controlling your environment variables.


Question 2
What is a key best practice when handling credentials in application development?

Responses
Storing keys directly in the code.
Using the same key for multiple applications.
Distributing keys via email to team members.
Not embedding keys in the code and using roles or services like Secrets Manager. - correct


Question 3
Which of the following AWS services can be used for secure credential handling, specifically for storing secret information?

Responses
AWS Config
AWS Organizations
Secrets Manager - correct
AWS Artifact


Question 4
What are environment variables in the context of applications?

Responses
Key-value pairs that provide data to applications without hardcoding.
Commands that execute the application.
Physical factors affecting the server's performance.
Specific regions where applications are hosted.


Question 5
What is the purpose of AWS Secrets Manager?

Responses
To provide access to environment variables.
To track changes to AWS infrastructure.
To provide a graphical interface for managing AWS resources.
To store, manage, and rotate sensitive information securely. - correct