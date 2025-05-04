# Containers

## 11.1 Amazon Elastic Container Service (ECS)
- https://aws.amazon.com/ecs/
- A fully managed container orchestration service makes it easy to run, manage, and scale Docker containers on ECS
- Simplify the process of deploying, managing and scaling containerize applicatoins on AWS
- Key Features: Managed orchestration, Integration with AWS services, Flexible deployment options
- Scalable, fast container management
- Run, stop and manage containers on a cluster
- Containers defined in a task definition, run as a task or service
  - Service: configuration that you use to run and maintain tasks simultaneously in a cluster
- Serverless Option: Fargate
- Run your tasks and services on a cluster of Amazon EC2 instances, managed by you
#### Fargate
- https://aws.amazon.com/fargate/
- You don't need to manage servers
- Hands-off capacity planning
- Security isolation handled
- Infrastructure managmeent by Fargate
- Container replacement scheduling based on: Resource needs, Isolation policies, Availability requirements
#### ECS
- https://aws.amazon.com/ecs/
- Integrated with IAM
- Containers recieve permissions via IAM roles
- Integrated with Amazon Elastic Container Registry (ECR) and Docker
- ***Build apps, not the environment***
- Integrated with CloudWatch - Get logs here instead of in container, save disk space
#### CI/CD Pipeline with ECS Example
- Monitor changes to a source code repository
- Build a new Docker image from that source
- Push image to an image repository such as Amazon ECR or Docker Hub
- Update ECS services to use the new image in your application
#### ECS Launch Types
- Fargate Launch Type
  - This is a serverless pay-as-you-go option
  - You can run containers without needing to manage your infrastructure
  - Why/When **Fargate**?
    - Large workloads that need to be optimized for low overhead
    - Small workloads that have occsoional burst
    - Tiny workloads
    - Batch workloads
- EC2 Launch Type
  - COnfigure and deploy EC2 instances in your cluser to run your containers
  - Why/When **EC2**?
    - Workloads that require consistenlty high CPU core and memory usage
    - Large workloads that need to be optimized for price
    - Your applications need to access persistent storage
    - You must directly manage your infrastructure
#### ECS Container Instances
- Amazon EC2 instance running the Amazon ECS container agent is a *Container Instance*
- Must be registered into an Amazon ECS cluster
- When tasks are executed with Amazon ECS, tasks are placed on active container instances
- Container Instances must run the agent
#### ECS Container Agent
- Allows container instances to connect to a cluster
- Is included in Amazon ECS-optimized AMIs
- Can install on any Amazon EC2 instance that supports the Amazon ECS specification
- Is supported on Amazon EC2 instances and external instances, can be on-prem
- Agent is open-source
#### ECS Developer Tools
- **Web Console**: Standard web-based AWS administration
- **AWS CLI**: Interaction with ECS API via command-line, useful in DevOps/scripting environments
  - https://aws.amazon.com/cli/
- **AWS CloudFormation**: Define and deploy via templates, infrastructure as code
  - https://aws.amazon.com/cloudformation/
- **Copilot**: All-in-one tool enabling deployment and operation of containerized direclty from source code
- **AWS App2Container**: Command line tool for migrating .NET and Java apps into containerized apps
- **Docker Desktop**: Integrated with ECS
- **AWS CDK**: Open source software development framework, enables modeling/provision cloud application resources using common programming languages
- **AWS SDKs**: Support for programmatic interactions with ECS API
- **AWS CloudWatch Alarms**: Alarm and act when threshold violated - if EC2 launch type, can scale in/out instances based on a metric
- **AWS CloudWatch Logs**: Store and access log files from containers - Use awslogs log driver in task definition
#### ECS Best Practices
- Make container images static
- Keep images as small as possible
- Limit images to one process
- Log to STDERR and STDOUT
- Use dedicated IAM roles per task definition family
- Allow internet access in/out only if needed
- Monitor with: CloudWatch Container Insights, X-Ray, VPC Flow Logs
- Follow Share Responsibility Model (security of the cloud, security in the cloud)
- Use KMS to encrypt Fargate ephemeral storage
- Remove extra binaries from images for security
- Scan images for vulnerabilities - built into ECS, uses Clair
- Use non-root users
- Best Practices Guide for ECS: https://docs.aws.amazon.com/AmazonECS/latest/developerguide/ecs-best-practices.html
## 11.2 ECS Demo
- "Run our containers in a cluster, or in Fargate"

## 11.3 Amazon Elastic Container Registry (Amazon ECR)
- ECR - Container Registry
- "Easily store, share, and deploy your container software anywhere"
- "A fully managed Docker and OCI compliant container registry for storing, managing, and deploying container images."
- **Purpose**: Provide a secure and scalable solution for storing and sharing container mages in the AWS ecosystem
- **Key Features**: High Availability, Scalable Storage, Fine-grained Access Control, Image Scanning (Clair)
- Images to be deployed into either a Cluster or Fargate
#### High-Availability and Scalability
- AWS ECR stores your images across multiple AWS Availability Zones for high availability and durability
- **Scalable Storage**: Automatically scales to meet your storage requirements, with no upfront provisioning needed
- **Performance**: Opitmized for a fast and reliable container image pulls
#### Fine-Grained Access Control
- Use AWS IDentity and ACcess Management (IAM) to control access to your container images
- ***IAM Policies*** - Create and attach policies to users, groups, or roles for granular access control.
- ***Resource Level Permissions*** Control access to specific repositories or images within a repository
- ***Image Scanning***: AWS ECR can automatically scan your container images for security vulnerabilities
- ***Amazon ECR Image Scanning***: Powered by the open-source tool *Clair*, it scans for know vulnerabilities in the image's software packages
- ***Notifications***: Receive notifications and view the scan results in the AWS Management Console
#### Integration with AWS Services
- AWS ECR integrates seamlessly with other AWS services, such as Amazon ECS, AWS Fargate, and AWS CodePipeline
- ***Deployment***: Use Amazon ECS and AWS Fargate to deploy containerized appications using images stored in ECR
- **CI/CD**: Use AWS CodePipeline to automate the build, test, and deploymnet of container images stored in ECR
#### Image Lifecycle Policies
- Automate the clean-up of old or unused container images with ECR Lifecycle Policies
- ***Policy Rules***: Define rules based on image age, tag status, or a combination of factors
- ***Cost Savings***: Reduce storage costs by automatically removing unused or outdated images
#### Secure Image Sharing
- Share container images securily across AWS accounts or publicly
- ***Cross-Account Sharing***: Share images with specific AWS accounts while maintaining access control
- ***Public Repositories***: Make images available publicly for braoder sharing and collaboration
#### Pricing and Cost Optimization
- ***Pay-as-you-go***: Pay only for the storage and data transfer used by your container images
- ***Cost Optimization***: Optimize costs by using ECR LIfecycle Policies to remove unused or outdated images
- ***Free Data Transfer***: Data transfer within the same AWS REgion between ECR and Amazon ECS or AWS Fargate is free
#### Summary & Demo
- AWS ECR provides a secure, scalable and highly available solution for storing, managing and deploying container images

## 11.4 AWS Copilot
- https://aws.amazon.com/containers/copilot/
- Command-line interface that simplifies containerized applicatino development, deployment, and management on AWS
- *"Command line interface for containerized applications"*
- ***Purpose***: SImplify the process of creating, releasing, and managing applications using AWS Fargate, Amazon ECS, and other AWS services
#### Key Features
- Application and service management
- Infrastructure-as-code
- Simplified deployment
#### Application and SErvice Management
- Copilot organizes applications into services that can be independently deployed and managed
- ***Services***: Define different components for your application, such as frontends, backends, and workers
- ***Environments***: Manage different deployment environments, such as test, staging, and production
#### Infrastructure-as-code
- Copilot generates AWS CloudFormation templates to define and provision AWS resources for your applications
- ***Benefits***: Version control, repeatability, and easy updates
- ***Customization***: Modify the generated templates to fit your specific requirements
#### Simplified Deployment
- Copiolot automates the deplyment process from building container images to updating and running services
- ***Pipelines***: Create continuous delivery pipelines to automatically deploy changes to your application
- ***Rollbacks***: Easily roll back to a previous version of your application in case of issues
#### Service Integrations
- Copilot integrates with various AWS services to simplify applicatin development and management
- ***AWS Services***: Amazon ECS, AWS Fargate, Amazon ECR, AWS App Runner, and more...
- ***Purpose***: Enable seamless coordination of various services to build, deploy, and manage containerized applications
#### Monitoring and Logging
- Copilot provides built in monitoring and logging capabilities for your applications
- ***Amazon CloudWatch*** - Monitor application performance and set up alarms for specific metrics
- ***Logging***: View logs for your services directly from the copilot CLI
#### Sercurity and Compliance
- ***Access Control***: Integrate copilot with AWS Identity and ACcess Management (IAM) to manage permissions
- ***Network Isolation***: Create VPCs and configure security groups to isolate your applications

## 11.5 AWS Copilot Demo
- AWS Copilot simplifies containerized application developmnet, deployment, and mangement on AWS
- Copilot - Many resources are created with the one copilot command - Use copilot to delete after deploying
- ...trying to delete everything on it's own is very difficult..."there are something like 20ish resources created"

## 11.6 Amazon Elastic Kubernetes Services (Amazon EKS)
- https://aws.amazon.com/eks/
- A fully managed Kubernetes service for deploying, managing, and scaling containerized applicatino using Kubernetes
- *"The most trusted wya to start, run, and scale Kubernetes"*
#### What is EKS?
- A fully managed Kubernetes service that makes it easy to run, manage, and scale containerized applications using Kubernetes on AWS
- Simplifies the process of deplying, managing, and scaling Kubernetes clusters on AWS infrastructure
#### Key Features
- Managed Kubernetes control plane
- Seamless integration with AWS services
- Simplified cluster management
#### Managed Kubernetes Control Plane
- AWS EKS manages the Kubernetes control plane for your clusters, including the API server, ect., and other core components
- ***High Availability***: EKS automatically distributes your control plane across multiple AWS Availability Zones for high availability and fault tolerance
- ***Upgrades***: EKS handles upgrades and patching for your control, plane, ensuring it stays up-to-date and secure
#### Integration with AWS Services
- EKS integrates seamlessly with other AWS services to provide a complete container management solution
- ***Key Integrations***: Amazon RDS, AWS Fargate, Amazon ECR, AWS Identity and Access Management (IAM), and AWS App Mesh
- ***Purpose***: Enable seamless coordination of varous services to build, deploy, and manage containerized applications
#### Simplified Cluster Management
- EKS simplifies Kubernetes cluster management by automating tasks such as patching, upgrades, and backups
- ***Managed Node Groups***: Deploy and manage worker nodes for your EKS cluster using managed node groups
- ***Cluster Autoscaler***: Automatically adjust the size of your worker node groups based on demand
#### Security and Compliance
- EKS provides a secure and compliant environment for running containerized applications
- ***IAM Integration***: Use AWS IAM to manage authentication and authroization for your Kubernetes clusters
- ***Private Networking***: Deploy your Kubernetes clusters in a private VPC for increased security and isolation
#### EKS Add-ons
- EKS Add-ones simplify the deployment and management of Kubernetes operations software
- ***Benefits***: AUtomatically install, manage, and update Kubernetes add-ons such as CoreDNS, kube-proxy, etc.
- ***Versioning***: EKS Add-ons support mulitple versions, enabling easy updates and rollbacks
#### Logging and Monitoring
- Use *Amazon CloudWatch* and *AWS X-Ray* to monitor the performance and health of your EKS clusters
- ***Metrics***: View key metrics such as CPU and memory utilizatino, pod counts, and network activity
- ***Logging***: Collect and analyze Kubernetes control plane logs using *Amazon CloudWatch* Logs
#### Demo and Summary
- AWS EKS simplifies Kubernetes cluster management and enables you tun , manage, and scale containerized application using Kubernetes on AWS





## Practice Questions
Which of the following statements about Amazon Elastic Container Service (ECS) is accurate?

Responses
Fargate is a serverless option for ECS that allows you to run containers without having to manage the underlying EC2 instances. - correct
ECS does not support integration with AWS Identity and Access Management (IAM).
ECS only supports running containers on EC2 instances.
ECS tasks are always long-running and cannot be used for short-lived operations.



In the context of AWS command-line tools, which of the following best describes the AWS Copilot tool?

Responses
It's used to easily create and manage CloudFormation templates.
It's a tool for managing EC2 instances.
It assists in the deployment of containerized applications within AWS. - correct
It provides an interface for the serverless application model.



Which AWS service employs the open-source tool 'Clair' to scan container images for known vulnerabilities?

Responses
AWS Elastic Beanstalk
AWS Elastic Container Registry (ECR) - correct
AWS Lambda
AWS CodePipeline



Which of the following best describes the Amazon Elastic Kubernetes Service (EKS)?

Responses
A platform for deploying single containerized applications in the cloud.
A managed Kubernetes control plane that simplifies cluster management in AWS. - correct
A tool for automatically updating and patching MySQL databases.
A specific AWS service for monitoring the health and performance of clusters.



What is the primary function of AWS's Elastic Container Registry (ECR)?

Responses
To provide a CI/CD pipeline for application development.
To run containers in a cluster for ECS or in Fargate.
To store and manage container images, facilitating scalable storage and high availability. - correct
To act as an open-source tool that scans container images for known vulnerabilities.