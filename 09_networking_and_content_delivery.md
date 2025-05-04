# Networking and Content Delivery

## 9.1 API Gateway
#### Network and Content Delivery
- Fully managed services for creating, publishing, maintaining, and securing APIs
- ***API***: Application programming interface
- App Developer: Builds applications that call AWS services using the API Gateway
- API Developer: Creates the API Gateway, Does need an IAM user account with with appropriate permissions
#### API Gateway
- AWS API Gateway simplifies API management, allowing developers to focus on building applications
- A fully managed service for creating, publishing, maintaining, and securing APIs
- Enables developers to define, secure, and monitor APIs that expose their application's functionalities
- Key features: API Creation, Logging, Custom Domains, Caching, Security
#### API Types
- RESTful APIs: Support for creating RESTful APIs with HTTP/HTTPS requests and JSON payloads
  - Statndard RESTful methods: Get, Post, Put, etc.
- WebSocket APIs: Build real-time APIs with WebSocket protocol for bidirectional communication
- HTTP APIs: SImplified, high performance APIs for low-latency workloads and straightforwards integrations
  
![alt text](../../___media/training/aws-cert-dev/9_Networking_and_Content_Delivery.md/image.png)

#### Features and Highlights
- API Gateway is part of AWS Serveless Infrastructure
- Tight integration with AWS Lambda
- API Gateway is the app-facing part of the AWS Serverless Infrastructure
- Lambda can be used to affect the intent of an app's API call
#### API Lifecycle Management
- Create, deploy, and manage APIs throughout their lifecycle
- Versioning and Stages - Manage multiple versions and deployment stages for your APIs
- Throttling and Quotas - Set request rate limits and quotas to control access and protect backend services
#### Integrations
- Integrates each API method with a backend endpoint
- Each backend endpoint is associeates with an integration type:
##### Lambda, HTTP, Private, Mock:
- Proxy:
  - Preferred method, Simple: Just the API at a functions, AWS configures the rest
  - Input expressed as any combination of: `Request Headers, Query String Parameters, Path Variables, Body`
- Custom:
  - Legacy, greater developer involvement
  - Can be used to pre-process request data
- Used to expose HTTP/HTTPS resources in an Amazon VPC for access by clients outside of the VPC
- API with private integration can be used for open access or controlled access to private VPC resources
- Contolled Access: IAM permissions, Lambda authorizer, Amazon Cognito user pool
- Mock Integration: 
#### API Gateway - Controlling Access:
- Amazon API Gateway Resource Policies
- IAM Permissions
- CORS
- Lambda Authorizers
- Amazon Cognito User Pools
- CLient-Side SSL Certificates, Backend Authentication
- API Gateway Usage Plans
- API Keys
#### API Gateway - Invocation:
- URL to Invoke - Obtain and API's Invoke URL in the API Gateway
- API Gateway Console > Method Test
- Postman
- Generated SDKs
- AWS Amplify JavaScript Library
- Trace API Managment and Invocation - CloudWatch
#### Caching and Performance
- Cache Integration - Enable caching to reduce latency and decrease the load on backend services
- Cache Encryption - Secure cache data with encryption at rest using AWS Key Management Service (KMS)
- Cache Capacity - Customize cache capacity to match your API's performance requirements
#### API Gateway - Generate an SDK
- API Gateway can generate SDKs for your API
- Java SDK, Andriod SDK, JavaScript SDK, Ruby SDK, iOS SDK (Objective-C or Swift)
#### Custom Domains and SSL Certificates
- Custom Domain Names - Use custom domain names for your APIs to match your application's branding
- AWS Certificate Manager (ACM) - Obtain and manage SSL/TLS certificates for your custom domains with ACM
- Route 53 - Configure custom domain names and routing using Amazon Route 53
#### Logging and Monitoring
- Amazon CloudWatch - Monitor API metrics and logs in real-time with Amazon CloudWatch integration
- AWS CloudTrail - Track API usage and changes with AWS CloudTrail
- Access Logs - Generate detailed access logs for your APIs to analyze client behavior

## 9.2 DEMO - API Gateway API Creatino With Swagger
- Wow, looks pretty straight forward - maybe play with this some more at home?

## 9.3 DEMO - Lambda Proxy Integration with API Gateway
- Lambda is not allowed to access anything unless it is explicitly give permission
- API Getway needs to be proxied over to the Lamdba function

## 9.4 DEMO - API Gateway HTTP Integration

## 9.5 DEMO - Securing and API Gateway API

## 9.6 DEMO - CloudFront
- Allows you to define a local "instance" and distribute it globally
- Think website: deployed in an AWS Region, if CloudFront is enabled, then pushed to other regions
- CloudFront network, edge locations, smart networking
- Goal: improve content delivery performance
#### Key features:
- Cache Control, Cache Invalidation, Compression
- SSL/TLS, AWS Certificate Manager (ACM), AWS WAF, Amazon S3 Origin Access Identity (OAI)
- Origin Servers: Source of your data, original version of the files, S3 or own HTTP server

## 9.7 Elastic Compute Cloud and Elastic Load Balancing (EC2/ELB)
- Web service to create and run virtual servers in the cloud
- Everything from the operating system up is the user's responsibility
- Everything below the operating system is Amazon's responsibility
#### Pricing
1. On-Demand: Hourly, No long-term commitment, No up-front payments
2. Spot Instances: Bid on spare compute capacity, up to 90% discount
3. Reserved Instances: Reserves compute capacity for when needed, Up to 75% discount
4. Dedicated Hosts: Physic EC2 server dedicated for your use; Eases compliance and Server-bound licenses
#### Instance Types
- General Purpose, MEmory Optimized, Storage Optimized, Compute Optimized, Accelerated Computing
- Within types, there sizes
#### EC2 Operating Systems
- Linux
- MacOS
- Windows, SQL Server
#### EC2 Networking
- Instances are assigned a private RFC1918 address when provisioned
- Can assign public-routable IP address
- Standard network ocnventions apply
  - Subnet-to-subnet communication needs a "router", route tables
  - Hosts in same subnet can talk to each other, provided communication is permitted. Default Deny.
  - Further details on VPC Network is in the VPC section of this course
#### Security Group
- Security Groups are "Stateful"
#### AWS EC2 Nitro Enclaves
- Nitro Enclaves are isolated compute environments with Amazon EC2 instances, designed for secure processing of sensitive data
- Security - Hardware based isolation, data, and applications are protected from unauthorized access
- Use Cases:
  - Cryptographic Operations
  - Processing Sensitive Data
  - Confidential Computing
  - Secure Key Management
- ***Isolation***: Nitro Enclaves have no persistent sotrage, external network access, or user access, providing a secure environment for sensitive data
- ***Felxibility***: Create Nitro Enclaves with varying amounts of CPU and memory resources to suit your specific requirements
#### Elastic Load Balancing
- A service that automatically distributes incoming traffic across multiple EC2 instances
- Types:
  - Application Load Balancer (ALB) for layer 7
  - Network Load Balancer (NLB) for layer 4
  - Classic Load Balancer (CLB) for layer 4 and 7
- Benefits: improved availability, Fault tolerance, Scalability
#### Elastic IP Addressing
- Static, public IPv4 address that you can asssociate with your EC2 instances
- Use Cases: Running public facing websites, Remote access to applications, Failover scenarios
- Benefits: Improve reliability by enabling easy re-mapping of IP addresses to instances in case of failures

## 9.8 EC2 and ELB Demo

## 9.9 Virtual Private Cloud (VPC)
- A virtual network environment in the AWS cloud that allows you to isolate and manage your own network resources
- ***Purpose***: Proved secure, scalable, and customizable networking for your AWS resources
- Virtual network dedicated to your AWS account
- Logically isolated from other VPCs
- Some AWS Services are launched into or attached to a VPC
- Configurable: Subnet Ranges, Routing Tables, Gateways, Security
#### Networking (1918)
- Public & Private addresses
- Preserved across reboots
- Multiple IPs can be assigned to an instance
- Define and attach multiple network interfaces to one instance
- IPv6 supported
#### Security
- Security Groups (stateful)
- Network ACLs (stateless)
- Reassign groups on the fly
- Assign groups to VPC and EC2 instances
- Ingress and egress filtering
#### VPC Internet Access
- Access from VPC to Internet is via Internet Gateway (IGW)
- Access to/from Instance with public IP is via IG
- Instances with only Private IP address cannot access Internet but can talk to each other
- Alternate: NAT Gateway through IG for instances with only private IP addresses
- Default: VPC has no gateways
#### VPC Service Attachment - services can be attached to a VPC 
- AWS Data Pipeline,
- EC2
- Elastic Beanstalk
- Elastic Load Balancing
- ElastiCache
- AWS OpsWorks
- RDS
- Redshift
- Workspaces
#### VPC Pricing and Limits
- VPC: Free
- Charges Associated with: EC2 instances, NAT Gateways, VPN Connections
- Soft* Limits (you request increases to certain limits):
  - VPC/Region: 5
  - Subnets/VPC: 200
  - Elastic IP/Region: 5
  - Custom Gateways/Region: 5
  - Network ACLs/Region: 200
  - Rules/Network ACL: 20
#### Virtual Private Cloud (VPC)
- ***VPC Flow Logs***: Capture information about the IP traffic going to and from network interfaces in your VPC
- ***Amazon CloudWatch***: Monitor VPC Flow Logs and other VPC metrics with Amazon CloudWatch integration
- Amazon VPC provides secure, scalable, and customizable networking for your AWS resources

## 9.10 VPC Demo

## 9.11 Route 53
- A managed DNS service that translates domain names into IP addresses
- ...routing user requests to AWS resources, scalable and highly available
- Domain Name system resolution, one of the first things that happens in a browser
- example: www.google.com ==> DNS resolution to IP addresses, etc
- Domain Name System (DNS)
- Route 53 enables developers to reliably route users to applications and resources in the AWS cloud
- Key Features: Domain Registration, Health Checks, DNS Routing, Traffic Flow Policies
- Stores name to IP mappings, PIv6 compliant
- Changes propogate worldwide within 60 seconds, but "time-to-live" is relevant
#### Key Features and Highlights
- Private DNS for VPC, DNS Failover, Health Checks and Monitoring
- Domain Registration, CloudFront and S3 Zone Apex Support, ELB Integration
- Anycast Routing, Global Infrastructure, High Availability
#### Summary
- Amazon Route 53 provides reliable and scalable DNS services, connecting user requests to AWS infrastructure

## 9.12 AWS WAF
- Web Application Firewall
- "Protect your web application from common exploits"
- Helps protect web applicatins from attacks by allowing you to configure rules
- Enables Administrators to allow, block, or monitor web requests based on conditions
#### Key Features
- Customizable web security rules
- AWS service integration
- Rate-based rules
- Real-time visibility and monitoring
- Managed rule groups
- Access control


## Practice Questions
Question 1
What is CloudFront primarily used for in AWS?

Responses

Storing data in a scalable and redundant manner.
Providing a global content delivery network to distribute content. - correct
Providing a global content delivery network to distribute content.
Generating and managing SSL/TLS certificates.
Creating virtual private networks for secure communication. 



Question 2
Which of the following statements is true regarding Amazon VPC?

Responses
Security groups are state-less, while Network Access Control Lists (NACLs) are state-ful.
Amazon VPC is a virtual network dedicated to your AWS account and is logically isolated from other VPCs, allowing overlapping address space between VPCs in the same region. - correct
EC2 Classic was a method that allowed launching EC2 instances outside of a VPC, and it's still available for new AWS accounts.
Within a VPC, two hosts on the same subnet cannot communicate with each other.



Question 3
Which of the following statements best describes the AWS Web Application Firewall (WAF)?

Responses
AWS WAF is a tool that primarily focuses on blocking malicious actors based on their geographical locations.
AWS WAF is a feature of AWS that specifically helps in monitoring the data stored in Amazon S3 buckets.
AWS WAF is a security feature in AWS that helps monitor and control web traffic, integrating with services like CloudFront and API Gateway, and allows administrators to create customizable security rules. - correct
AWS WAF is a service in AWS that solely manages access controls for other AWS services.



Question 4
Which of the following best describes the role of Amazon EC2 in AWS?

Responses
A database management service that allows for quick deployments.
A service that provides resizable compute capacity in the cloud, enabling users to launch and manage virtual servers. - correct
A storage solution specifically tailored for data archiving and long-term backup.
A platform service for developers to deploy and run applications without managing infrastructure.



Question 5
Which of the following statements is true regarding Amazon's Route 53?

Responses
Route 53 translates domain names into MAC addresses.
Route 53 can only be managed through the AWS web console.
Route 53 is named after the UDP Port 53 which is used for the DNS system. - correct
Route 53 is an application streaming service that allows users to access desktop applications from anywhere.