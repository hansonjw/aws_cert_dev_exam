# Test Applications in Development Environments

## 13.1 CodeBuild Testing
- Implement unit testing in AWS CodeBuild to...
- ...validate code changes, catch errors early, and maintain code quality in your projects
- ***CodeBuild***: fully managed continous integration service that compiles, tests, and deploys your code
  - Automate the process of building, testing, and deploying applications in the cloud
  - BUild environments, custom build steps, integration with AWS services, support for popular tools
#### Unit Testing
- A software testing technique that verifies the correectness of individual units of code, such as functions or methods
- Carch errors early, validate code changes, and maintain code quality
- Faster development reduced socsts, easier debugging, and improved reliability
#### Configuring COdeBuild for Unit Testing
- Define build specificiations that include unit testing steps
- **buildspec.yml** A YAML file that specifies build commands, runtime versions, and other settings
- Configure the "test" phase in buildspec.yml to run unit tests using your preferred testing framework
#### Supported Testing Frameworks
- JUnit (Java), NUnit (C#), Pytest (Python), Jest (JavaScript), RSpec (Ruby)
- Install and configure additional testing frameworks as needed
#### Test Report and Artifacts
- Generate and store test reports and artifacts for further analysis
- Configure buildspec.yml to create and store test reuslts and artifacts in Amazon S3
- View test report summaries and details in the AWS CodeBuild console
#### Test Report and Artifacts
- Test Report File FOrmat Support:
  - Cucumber JSON (.json)
  - JUnit XML, NUnit XML, NUnit3 XML TestNG XML (...all .xml)
  - Visual Studio TRX (.trx)
#### Integration with AWS Developer Tools
- Seamlessly integrate AWS CodeBuild with other AWS developer tools
  - AWS CodePipeline - Use in a pipeline to automate the build and test process
  - AWS CodeCommit - Trigger CodeBuild projects when code changes are pushed to a repository
  - AWS CodeDeploy - Deploy applications after successful builds and tests
- Monitoring and Notifications
  - Amazon CloudWatch: Monitor build metrics, logs, and set alarms
  - AWS CodeStar Notifications: Set up notifications for build status changes through Amazon SNS or other supported channels
#### Best Practices for Unit Testing in CodeBuild
- Test Coverage - Aim high for test coverage
- Continuous Integration - Integrate unit testing into your CI/CD pipeline for faster feedback
- Test Isolation - Write independent, focused tests that can be executed in parallel

## 13.2 API Gateway Mock Endpoints
- AWS API Gateway fully managed service to create, publish, maintain, monitor, and secure APIs at any scale
- Connect applications to backend services such as AWS Lambda, Amazon S3, or any HTTP data source
- App Developer vs API Developer
- Mock endpoints provide a way to simulate API behavior without implementing backend logic
- Test and iterate on API design more quickly by mocking responses
- Easier Testing: Validate API behavior and client applications withou the need for alive backend
- Cost Effective: Reduce costs by avoiding unnecessary backend infrastructure during development and testing
#### Setting up Mock Endpoints in API Gateway
- Create mock endpoints unsing the API Gateway console, CLI, or SDK
- Integration Type: Choose "MOCK" as the integration type when createing a new API method
- Mock Integration: Define the API method's repsonse templates and status codes
#### Defining Mock Responses
- Customize the response templates and status codes for your mock endpoints
- JSON Templates: Use JSON based templates to define the structure and content of mock responses
- Mapping Templates: Use Apache Velocity Template Language (VTL) to manipulate and transform the response data
#### Testing Mock Endpoints
- Test mock endpoints using the API Gateway console, CLI, SDKs, or third party tools
- API Gateway COnsole: Use the built-in "Test" feature to test mock endpoints directly within the console
- Postman, Curl, etc.: Test mock endpoints using popular HTTP client tools like Postman or Curl
- AWS API Gateway mock endpoints enable you to simplify API development and testing
- Decouple "Front End" application development and "Back End" infrastructure developement

## 13.3 Lambda Versions and Aliases
- Versions and Aliases to manage deployments, improve testing and control versioning of your serverless functions
***Lambda***: "Run code without thinking about servers or clusters"
#### Versions
- Immutable copies of you function code and configuration
- Simplify function deployment, rollback, and versioning
- Pubulish a new version when you update your Lambda function code or configuration
- Each version is assigned a unique version number
#### Aliases
- amed pointers to sepcific Lambda function versions
- Simplify function invocation, enable blue/green deployments, and imporove testing
- Associate aliases with different stages of your development lifecycle (e.g. dev, test, prod)
- Updating Aliases to point to a different version when you are ready to promote changes
#### Implementing Traffic Shifting
- Gradually shift traffic between two Lambda function versions using aliases
- Test new function versions with a subset of users before full deployment
- Set up weighted aliases and adjust the weights over time to control the percentage of traffic going to each version


## Practice Questions


Question 1
The buildspec.yml file is a crucial file in AWS. Which of the following statements accurately describes the buildspec.yml file?

Responses
CodeStar always provides the only acceptable version of the buildspec.yml file.
The buildspec.yml only supports JavaScript and no other programming language.
The buildspec.yml contains phases like install, pre-build, post-build, and artifacts. - correct
The buildspec.yml file exclusively defines the testing commands and has no reference to building instructions.


Question 2
Which of the following is a key advantage of using mock integrations in API Gateway during the development process?

Responses
Immediate deployment of Lambda functions.
Enhanced security for API endpoints.
Real-time data synchronization with backend services.
Accelerated front-end development without backend dependencies. - correct


Question 3
Which of the following points is a recommended practice when using unit tests and AWS CodeBuild?

Responses
The outcome of unit tests should never influence the continuation or halting of a deployment.
Unit testing in CodeBuild helps maintain code quality, catch errors early, and streamline the testing process. - correct
The buildspec.yml file is only used for defining build commands and has no phase dedicated to testing.
A good practice is to group several significant changes into one unit test to save time.


Question 4
What is the primary purpose of mock endpoints in API Gateway?

Responses
To enforce IAM authentication for both app developers and API developers.
To automatically integrate with DynamoDB and return a list of results.
To directly expose Lambda functions to the internet.
To provide a way for app developers to test the API without the need for the backend logic. - correct


Question 5
What is the primary purpose of using versions and aliases in AWS Lambda?

Responses
To create a duplicate of a Lambda function for redundancy.
To enable real-time monitoring of Lambda function performance.
To manage AWS Lambda billing and cost optimization.
To control versioning and deployment stages of Lambda code. - correct