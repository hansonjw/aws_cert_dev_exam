# 14 Automating Deployment Testing

## 14.1 - API Gateway Stages
- Stages represent different environments in the API lifecycle (dev, test, prod)
- Simplify deployment, monitoring, and versioning of your APIs
- Cusom domanin names, stage variables, chaching, and logging
- Deploy APIs to different stages to support various development and testing environments
#### Deploying APIs to Stages
- Deploy your API to a stage to make it publicly accessible
- Create a new stage or update and existing stage when you deploy your API
- Associate each stage with a specific version of your API
#### Custom Domain Names and Base Path Mappings
- Assign custom domain names to your API stages
- Use AWS Certificate Manager to obtain and manage SSL certificates for your custom domain names
- Map custom domain names to specific stages and base paths of your API
#### Stage Variables and Caching
- Use stage vaiables to parameterize your API integration nad manage environment specific configurations
- Caching: Enable caching at the stage level to improve performanace and reduce the latency of your API requests
- Cache Settings: Configure cache settings, such as cache capacity, time to live (TTL) and cache encryption

## 14.2 - Branches and ACtions for CI/CD
- ***CI/CD***: Continuous Integration (CI) and Continuous Deployment (CD)
- Development practices that automate the build, test, and deployment processes
- Improve code quality, reduce development cycle time, and increase depoyment reliability
- Common AWS Services: *AWS CodeCommit*, *AWS COdeBuild*, *AWS CodeDeploy*, *AWS CodePipeline*
#### CodeCommit Branches
- Branches represent different versions or stages of your codebase in a repository
- Simplify parallel development, feature testing, and verison control
- Use feature branches for individual features or bug fixes, and merge them into the main branch upon completion
#### AWS CodePipeline Actions
- Actions are tasks performed on your code or infrastructure during the CI/CD process
- Types of Actions: Source, Build, Test, Deploy, Invoke
- AWS Services Integration: CodeCommit, CodeBuild, CodeDeploy, Lambda
#### Branches and Actions for CI/CD
- Branches represent different versions or stages of your codebase in a repository
- Simplify parallel development, feature testing, and version control
- Use feature branches for individual features or bug fixes...
- ...and merge them inot the main branch upon completion
- Example Stages: Source, Build, Test, Deploy
- CodeCommit is a fully git compliant tool

## 14.3 - Unit and Mock Automated Testing
- ***Unit Testing*** - Testing individual units or components of your application to ensure they function as expected
- ***Mock Testing*** - A type of unit testing where dependencies or external services are replaced with mock objects to isolate the component being tested
- Improve code quality, reduce bugs, and enhance application reliability
#### AWS Services for Automated Testing
- ***AWS CodeBuild*** - A fully managed build service that supports running unit and mock tests as part of your build process
- ***AWS CodePipeline*** - A continuous delivery service that automates the release process, integrating testing stages into your CI/CD pipeline
- ***AWSL Lambda*** - A serverless compute service that can be used to exicute cusome testing scripts
#### Implementing Unit and Mock Testing in AWS CodeBuild
- Configure COdeBUild to run unit and mock test using buildspec.yml
- Test Frameworks - Integrate popular testing frameworks (JEst, Mocha, JUnit)
- Test Reporting - Enable test reporting in CodeBuild to collect and analyze test results
#### Using AWS Lambda for Custom Testing Scripts
- Execute custom testing scripts using Lambda functions
- Integration - Trigger Lambda functions from CodePipeline or CodeBuild
- Use Case - Perform advanced testing scenarios or run tests using custom tools and libraries
#### Monitoring and Notifications
- AWS Services - AWS CloudWatch, Amazon SNS
- Best Practices: Set up alarms, metrics, and notifications to stay informed about your testing pipeline's performance and status
- Notifications: Confrigure notifications for test failures, piepline status changes, or other important events


## Practice Questions


Question 1
What is the purpose of stage variables in AWS API Gateway?

Responses

They enable dynamic configuration and parameterization of API behavior per stage. - correct
They are used to define custom domain names for API endpoints.

They provide transport layer security for API communications.
They allow you to version control Lambda functions within an API.


Question 2
What is the primary purpose of API Gateway stages in AWS?

Responses

To provide transport layer security for API endpoints.
To manage and deploy Lambda functions within an API.
To create and maintain custom domain names for APIs.
To version control and represent different environments in the API lifecycle. - correct


Question 3
What is the purpose of CI/CD in software development?

Responses

To manage code repositories and handle version control.
To automate the build, test, and deployment processes of development. - correct
To optimize user interface design and user experience.
To improve server infrastructure and scalability.


Question 4
Which AWS service is commonly used for automating the build and deployment stages in a CI/CD pipeline?

Responses

AWS CodeBuild - correct
AWS Lambda
Amazon EC2
Amazon S3


Question 5
What is the primary purpose of unit testing in software development?

Responses

To ensure that the application meets all functional requirements.
To test individual units or components of the application for expected functionality. - correct
To test the entire application as a whole.
To validate the application's performance under load.