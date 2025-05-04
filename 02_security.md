# Security
## 2.1 IAM Fundamentals

#### IAM Fundamentals: Users, Groups, Roles, Policies
- **I** dentity - Who are you?
- **A** ccess - What can you do?
- **M** anagement - What can you do it to?
- PCI - Payment Card Compliant
- IAM is free (Security if free, general idea)

#### Principle of Least Priviledge
- Granting users the minimum permissions necessary to perform their tasl
- Minimize potential impact of compromized credentials
- Review and adjust policies regularly

### Users
- An individual entity with a defined username (human, or code)
- Access Types:
  1. Programmatic Access
  2. AWS Management Console Access

- ***Root User***:
  - Initial account to set up the AWS Account
  - Best practice - don't use this account for normal operations, set-up administrator account

### Groups
- A collection of Users
- Defined by a Group Name - Note: Group name can be changed at any time
- Have a ***Policy*** attached

### Roles
- AWS identity with permission policies
- Can be assumed by anyone/anything that needs it (and is permitted to)
- Use: Delegate access to users, applications, or services that don't normally have access to your AWS resource

### Policies
- A set of permissions
- Effect, Action, Resource
- Created by: 1. Copy of AWS Policy 2. Policy Wizard 3. Self-defined
- JSON (JavaScript Object Notation) document
- ***Policies*** can be applied to **users**, **groups**, **roles** and **resources**
- **Policies Define:** (1) Who can access what (2) What actions they can perform
#### 1. Managed Policies:
  - Standalone
  - Only assignable to identities, not resources
  - Assignable to users/groups/roles
  - ***Same policy can be used on multiple entities***
#### 2. Inline Policies:
  - Embedded in the target user/group/role
  - ***Policy is not "reusable"***
  - Can edit inline policies
#### Identity vs. Resource based Assignment
- Permissions can be assigned in two ways:
  1. Identity based:
     - Assiend to: users/groups/roles
     - Specifies what **X** can do
  2. Resources based:
     - Assiend to a resource such as and S3 bucket, etc.
     - Specifies who has access and what they can do

#### Example - Identity vs Resource based:
![alt text](image.png)

#### Example Policy:
![alt text](image-1.png)

#### IAM Best Practices
- Regularly review and update IAM policies
- Enable AWS CloudTrail for auditing and monitoring
- Use IAM roles for EC2 instances and AWS services
- Rotatel access keys and other credentials regularly
- Use groups for easier management
- Enable multi-factor authentication (MFA)
- Create strong password policies
- ***Least Privilege*** (Implement this concept)

#### IAM General Comments
- IAM is essential for securing access to your AWS resources
- Further reading: AWS IAM documentation, AWS Well-Architected Framework
- Don't put keys in code

## 2.3 Federated Identities
#### Implementing Authentication and/or Authorization
- IAM - ***IdP*** (Identity Providers)
- Integrate external identity database
- Can assign permissions to users in that external IdP
- Example: Corporate User Directory
#### Compatible IdPs
- OpenID Connect (OIDC)
- Security Assertion Markup Language 2.0 (SAML)
#### Federated Identities - Benefits
- Simplify access management
- Reduce administrative overhead
- Enhance security
#### OIDC
- **OIDC**: An authentication layer build on top of OAuth 2.0 for identity verification
- Configure OIDC identity providers in AWS IAM
- Role-based Access: Assign IAM roles to federated users for accessing AWS resources
#### Single Sign-on with SAML
- **AWS SSO**: A centralized service that manages SSO access to AWS accounts and applications
  - Allows one to authenticate to one thing and be authenticated to multiple things
- **SAML 2.0**: A standard for *exchanging* authentication and authorization data between parties
- **SAML Providers**: Configure SAML providers in AWS IAM for SSO using external IdPs like ADFS, Okta, or PingFederate
- **SSO Process**: Users authenticate with IdP, and then access AWS resources using SAML assertions
#### AWS Security Token Service
- Create. provide trusted users with temporary sercurity credentials -> access your AWS resources
- Issue short-term creentials for federated users, IAM roles, and other scenarios
- Almost identical to long-term creds:
  - STS cerd are *short-term*
  - Configurable expiration, minutes to hours
  - Expired? Unknown, denied
  - Dynamically generated upon request
  - User/app can request new creds before expiration
#### IAM - Cognito Federated Identities
- Web Identity Federation: Login with Amazon, Facebook, Google, Apple, etc.
- Amazon Cognito user pools
- Open ID Connect providers
- SAML identity providers
- Developer authenticated identities
#### Federated Identity Best Practices
- Use AWS SSO for centralized access management solution
- Follow the ***Principle of Least Privilege*** for federated users
- Monitor and audit federated user access using AWS CloudTrail and Amazon CloudWatch
- Use multi-factor authentication (MFA) - Something you have, something you know
- Use strong password policies for external identity providers


## 2.4 Cognito
#### User Pools
- Store and manage user profiles for authentication
- ***A directory for all of your users***
- Directory to sign up and sign in users
- Store user profiles
- Customizable User Interface
- Integration with Social Identiy providers (Facebook, Google, Amazon, etc)
#### Identity Pools
- ***Access control for your resources***
- Control access to your AWS resources and APIs
- Map users to different roles and permissions and get temporary AWS credentials for S3, DynamoDB, Lambda, etc.
- Common user case: Web and mobile applicatoins that requre access to AWS resources
- Federate user identities and provide temporary AWS credentials for authorization
- **Role Mapping**: Define rules to map identities to different IAM roles based on user attributes or claims
- **Access Control**: Implment fine-grained access control for AWS resources using IAM policies
#### Hosted User Interface
- A fully managed, customizable authentication and authorization interface for web and mobile applications
#### Cognito Best Practices
- Use User Pools for authentication and Identity Pools for authorization
- Enable MFA (*"Something you have, Something you know"*)
- Strong Password Policy
- **Least Privilege Principle**
- Use AWS CloudTrail and AWS CloudWatch to monitor Cognito usage


## 2.5 Cognito - Hosted UI
#### Customizable UI
- Tailor the look and feel of the interface to mathc your applications branding (modify CSS, etc)
- Customize logo, background image and CSS
- Domain
- Advanced customization - ***Cognito Lambda triggers***
#### Built-in Security
- Includes features like MFA and password policy enforcement
#### Social Identity Providers
- Integrates with social media logins, such as Facebook, Google, and Amazon
#### Single Sign-On (SSO)
- Enables users to sign-in once and access multiple applications
#### OAuth 2.0 and OpenID Connect
- Supports industry standard protocols for secure authentication and authorization
#### Trade-offs
- Some limited customization, pre-built and customizable
- Don't need to manage another database
- Saves Time: Dev time and effort, 
- Improved Security
- Scalability
- Cost: Free for first 50k users
- Seamless integration - with other ASW services and 3rd party identity providers
- Consistent user experience
#### Get Started
1. Create a Congnito User Pool, configure sign-up and sign-in options
2. Set up social identity providers and/or SAML identity providers, if needed
3. Customize the appearance and behavior of the hosted UI
4. Configure the domain for the hosted UI
5. Integrate the Cognito hosted UI with your web or mobile application
#### Example sign in page
![alt text](image-2.png)

## 2.6 Cognito - Hosted UI Demo



## Practice Questions

Question 1
In the context of AWS, what is the purpose of the Security Token Service (STS)?

Responses

It stores files like the Simple Storage Service (S3).
It stores files like the Simple Storage Service (S3). - no response given

It provides authentication for SAML 2.0.
It provides authentication for SAML 2.0. - no response given

It integrates with Active Directory Federation Services, ADFS or Okta.
It integrates with Active Directory Federation Services, ADFS or Okta. - no response given

It is a foundational, fundamental service of IAM that generates temporary credentials that can expire.
It is a foundational, fundamental service of IAM that generates temporary credentials that can expire. - correct
Question 2
Which of the following services or standards are compatible with AWS for federated identities?

response - correct
Responses

OpenID Connect (OIDC)
OpenID Connect (OIDC) - correct

SAML 2.0
SAML 2.0 - correct

SAML 3.0
SAML 3.0 - no response given

Microsoft Office 365
Microsoft Office 365 - no response given
Question 3
What is the primary purpose of a Cognito user pool in AWS?

Responses

It is a database service for storing user-specific game scores and achievements.
It is a database service for storing user-specific game scores and achievements. - no response given

It is a feature that enables users to interact directly with AWS services without any authentication.
It is a feature that enables users to interact directly with AWS services without any authentication. - no response given

It offers a hosted user interface for application developers to display AWS services.
It offers a hosted user interface for application developers to display AWS services. - no response given

It serves as a directory to store, manage, and authenticate user profiles.
It serves as a directory to store, manage, and authenticate user profiles. - correct
Question 4
What should you NEVER do when using programmatic access with AWS?

Responses

Attach IAM roles to an EC2 instance.
Attach IAM roles to an EC2 instance. - no response given

Use the AWS Management Console.
Use the AWS Management Console. - no response given

Embed the access key and secret key directly in your code.
Embed the access key and secret key directly in your code. - correct

Use AWS CloudTrail for monitoring interactions.
Use AWS CloudTrail for monitoring interactions. - no response given
Question 5
Which of the following statements best describes the principle of least privilege in AWS?

Responses

Granting users maximum permissions necessary to get their job done.
Granting users maximum permissions necessary to get their job done. - no response given

Granting users the minimum permissions necessary to get their job done.
Granting users the minimum permissions necessary to get their job done. - correct

Assign permissions based on job titles without reviewing individual tasks.
Assign permissions based on job titles without reviewing individual tasks. - no response given

Allow users unlimited access to ensure they can complete all tasks.