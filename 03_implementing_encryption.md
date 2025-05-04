# 3. Implementing Encryption

## 3.1 At-rest vs In-transit Encryption; Client-side vs Server-side Encryption
#### At-rest Encryption
- Protecting data when it is stored on disk or other storage devices
- Prevent unauthorized access to sensitive infomration in case of data breaches or physical theft
- Used by default in many AWS services (option in many others)
- AWS Key Management Service (KMS) for managin encryption keys
- Implementing in AWS: Depends onf the service (*S3, EBS, RDS, Redshift, DynamoDB, etc.*)
#### In-transit
- Protecting data while it is being transmitted between systems or services (as data is moving)
- Prevent data interception, eavesdropping, or tampering during transmission
- **Protocols**: TLS/SSL, HTTPS, and other secure communication protocols
- All communication with AWS Services is encryptied in-flight
- Quote form AWS documentation/whitepaper:
>>>*"All network traffic between AWS data centers is transparently encryptied at the physical layer"*
- Implementing in AWS: Depends on the service (Amazon API Gateway, AWS Transfer Family, Amazon VPC, Amazon RDS, etc.)
- API/CLIL All communication is encrypted using standard TLS encryption

<img src="image-3.png" width="500">

#### Best Practices
- Both at-rest and in-transit encryption are crucial for securing you data in AWS
- Implement encryption for data storage and transmission using AWS services and key management tools
- Follow best practices for encryption key management, access control, and monitoring to ensure data confidentiality and compliance
#### Further Reading: 
1. AWS Security Best Practices
2. AWS Well-Architected Framework
3. AWS Encryption SDK
## 3.2 AWS Certificate Manager (ACM)
- TLS: https://en.wikipedia.org/wiki/Transport_Layer_Security
- Public Key and Private Key
- AWS Certicate
#### Features
- Provisioning
- Automatic Renewals
- Private Certificates
- Integration with AWS services
- Secure and compliant - Industry Standards
#### ACM Certificate Lifecycle
>**Request => Validation => Deployment => Monitoring => Renewal**
- **Request**: Request a public or private SSL/TLS certificate through the ACM console, API, or CLI
- **Validation**: For public certificates, domain ownership must be validated through email, DNS, or CNAME records
- **Deployment**: Integrate the certificate with AWS services, such as CloudFront, Elastic Load Balancing
- **Monitoring**: Use Amazon CloudWatch and AWS CloudTrail to monitor certificate-related events and metrics
- **Renewal**: ACM automatically handles the renewal of public certificates, while private certificate renewals are user-managed
#### ACM Benefits
- Cost Effective: Public SSL/TLS certificates from ACM are provided at no additional cost
- Time-saving: Reduces overhead of managing certificates
- Improved security: Automatic certificate renewals reduce the risk of certificate expiration and downtime
- Enhanced compatibility - with modern browsers and clients
- Simplified Management
#### Getting Started
1. Sign into the AWS Management Console and navigate to the ACM service
2. Request or import and SSL/TLS certificate
3. Validate domain ownership (for public certificates).
4. Integrate the certificate with the desired AWS services.
5. Monitor certificate usage and performance through CloudWatch and CloudTrail

## 3.3 Key Management Service (KMS)
- **Purpose**: Manage encryption keys for data protection and compliance
- **Features**: Key creation, rotation, management, and access control
- Integrations: works seamlessly with many AWS services used in Dev work
- Compliance: Supports FIPS 140-2 validated security hardware modultes
#### KMS Concepts
- Envelop encryption: A process of encrypting plaintext data with a data key, and then encrypting the data key itself with a CMK
- Key policies: JSON documents that define permissions and controls for a CMK
#### Creating and Managing CMKs
- **Create CMKs**: Generate CMKs using the AWS management console, SDKs, or CLI
- **CMK Types**: AWS managed CMKs, customer managed CMKs, and custom key stores
- **Key Rotation**: Enable automatic key rotation to enhance security
- **Alias and Tags**: Assign aliases and tags to CMKs for easier identification and management
#### Access Control and Permissions
- **IAM Policies**: Attach policies to IAM users, groups, or roles to grant permissions for CMKs
- **Key Policies**: Define permissions and controls for a specific CMK
- **Grants**: Delegate specific permissions to other AWS accounts or AWS services
#### KMS Best Practices
- Seperate keys per applicatin or environment
- Enable key rotation and rotate regularly
- ***Principle of Least Privilege***
- Use CloudTrail and CloudWatch
- **KMS Further Reading**: KMS documentation, Well-Architected Framework, Security Best Practices



## Practice Questions

Question 1
Which of the following is NOT a type of at-rest encryption key?

Responses
AWS-managed keys
Customer-generated keys
AWS-owned keys
Server-side encryption keys - correct


Question 2
What is the primary purpose of AWS Certificate Manager (ACM)?

Responses
Network traffic monitoring.
Storage of large files on AWS.
Machine learning model deployment.
Provisioning and management of TLS certificates. - correct


Question 3
How does ACM verify the ownership of a domain for which a certificate is requested?

Responses
By requesting a text record via DNS. - correct
By validating the website content.
By sending an email to the domain owner.
By checking the IP address associated with the domain.


Question 4
Which of the following statements regarding AWS Key Management Service (KMS) is NOT true?

Responses
Envelope encryption involves encrypting the data key with a customer master key and encrypting the contained data.
KMS supports both asymmetric and symmetric key cryptography.
The AWS services such as S3, EBS, RDS, and Lambda can integrate with KMS for encrypting data at-rest.
KMS is primarily used for data migration between AWS services. - correct


Question 5
Which of the following accurately describes the difference between at-rest and in-transit encryption?

Responses
At-rest encryption is the encryption of data while it is stored and not being accessed, while in-transit encryption pertains to the encryption of data as it is being transferred between locations. - correct
At-rest encryption is the encryption of data as it is moving, while in-transit encryption is the encryption of data while it is stored.
At-rest encryption involves tapping into network cables to listen to data transfer, while in-transit encryption is about securing data from eavesdropping.
At-rest encryption and in-transit encryption both refer to the encryption of data while it is being manipulated.