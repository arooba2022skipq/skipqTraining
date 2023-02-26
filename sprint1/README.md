
# Deploying a "hello from lambda" Lambda Function using AWS CDK in TypeScript




## Prerequisites

Before you begin, you'll need to have the following:

- An AWS account
- Node.js installed on your local machine
- The AWS CLI installed on your local machine

## Steps
## Steps
## Steps
## 1. Install the AWS CDK and TypeScript globally
Run the following command in your terminal:

```
npm install -g aws-cdk typescript
```

## 2. Create a new directory for your CDK app and navigate into it
```
mkdir hello-world-lambda
cd hello-world-lambda
```
## 3. Initialize a new CDK app using the TypeScript template
```
cdk init --language typescript
```
## 4. Install the necessary AWS SDK packages
```
npm install @aws-cdk/aws-lambda @aws-cdk/aws-lambda-nodejs
```
## 5. Import the required modules
In the lib/hello-world-lambda-stack.ts file, add the following imports:
```
import * as cdk from 'aws-cdk-lib';
import * as lambda from 'aws-cdk-lib/aws-lambda';
import * as nodejs from 'aws-cdk-lib/aws-lambda-nodejs';
```
## 6. Create a new Lambda function
Add the following code to the `HelloWorldLambdaStack` class:

```
 const hello = new lambda.Function(this, 'HelloHandler', {
      runtime: lambda.Runtime.NODEJS_16_X,    // execution environment
      code: lambda.Code.fromAsset('lambda'),  // code loaded from "lambda" directory
      handler: 'hello.handler'                // file is "hello", function is "handler"
    });
```
## 7. Create a new file for the Lambda function code
Create a new directory called lambda in the root of your project, and create a new file called hello.js in that directory.


## 8. Write the Lambda function code
In the hello.js file, add the following code:

```
exports.handler = async function(event) {
    console.log("request:", JSON.stringify(event, undefined, 2));
    return "hello from lambda"
  };
```
## 10. Deploy your Lambda function to AWS
Run the following command:

```
cdk deploy
```
## 11. Test your Lambda function
Once the deployment is complete, you should see the Lambda function in the lambda console. 

You should receive a response that says "hello from lambda".

Congratulations! You've successfully deployed a Lambda function using AWS CDK in TypeScript.