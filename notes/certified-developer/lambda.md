# Lambda

Serverless: developers don't have to manage servers anymore. They just deploy code, aka functions. 

- Limited by time - short executions
- Run on demand
- Scaling is automated


## Serverless Functions

- Lambda
- DynamoDB
- AWS Cognito
- API Gateway
- S3
- SNS & SQS
- Kinesis
- Aurora Serverless

## Lambda Integrations

- API Gateway
- Kinesis
- DynamoDB
- S3
- IoT
- Cloudwath Events
- CloudWatch Logs
- SNS
- SQS
- Cognito

## Benefits

- Easy pricing, pay per request and compute time.
- Free tier of 1,000,000 Lambda requests and 400,000 GBs of compute time.
- Integrated with the whole AWS stack.
- Integrated with many programming languages.
- Easy monitoring through CloudWatch
- Easy to get more resources per function (up to 3gb of RAM)
- Increasing RAM will also improve CPU and network.

## Languages

- Node.js
- Python
- Java
- C# (.NET Core)
- Goland
- C# / Powershell

## Pricing

[See AWS Lambda Pricing](https://aws.amazon.com/lambda/pricing)

- Pay per calls
  - First 1 million requests are free
  - $0.20 per 1 million requests thereafter
- Pay per duration (in increments of 100ms)
  - 400,000 GB seconds of compute time per month if free
  - == 400,000 seconds if function is 1gb RAM
  - == 3,200,000 seconds if function is 128 MB RAM
  - After that $1.00 for 600,000 GB-seconds.

## Retries and DLQ

- If a Lambda function asynchronous invocation fails, it will be retried twice.
- After all retries, unprocessed events go to the Dead Letter Queue
- DQL can be a SNS topic or SQS queue.
- The original event payload is sent to the DQL.
- This is an easy way to debug what's going wrong with your functions in production without changing the code.
- Make sure the IAM execution role is correct for your Lambda function.

Updates:

- "Debugging and error handling" has been replaced by "AWS X-Ray"
- DQL is now located under Asynchronous Invocation.

## Logging, Monitoring, and Tracing

- CloudWatch
  - Lambda execution logs are stored in CloudWatch Logs
  - Lambda metrics are displayed in CloudWatch Metrics
  - Make sure the Lambda function has an execution role with an IAM policy that authorizes writes to CloudWatch.
- X-Ray
  - You can Trace Lambda with X-Ray
  - Enable in Lambda configuration
  - Ensure Lambda function has correct IAM execution role.

Can be viewed on the Monitoring tab when looking at a Lambda function.

## Lambda Limits

- Execution
  - Memory allocation: 128mb - 3008mb (64mb increments)
  - Maximum execution time: 300 seconds (5 minutes). Note: now 15 minutes but the exam assumes 5.
  - Disk capacity in the function container in /temp: 512mb
  - Concurrency limits: 1000
- Deployment
  - Lambda function deployment size (compressed .zip): 50mb
  - Size of uncompressed deployment (code + dependencies): 250mb
  - Can use the /tmp directory to load other files at startup
  - Size of environment variables: 4kb

## Lambda Versions

- When you work on a Lambda function, we work on `$LATEST`
- When we're ready to publish a Lamdba function, we create a version.
- Versions are immutable.
- Versions have increasing version numbers.
- Versions get their own ARN.
- Version = code + configuration (nothing can be changed - immutable)
- Each version of the Lambda function can be accessed.

## Lambda Aliases

- Aliases are pointers to Lamdba function versions.
- We can define a dev, test, prod aliases and have them point at different Lambda versions.
- Aliases are mutable.
- Aliases enable stable configuration of our event triggers / destinations

## Function Dependencies

If your Lambda functions depend on external libraries, for example X-Ray SDK, Database Clients, etc., you will need to install the packages alongside your code and zip it together.

- For Nod.js, use `npm` and `mode_modules` directory
- For Python, use pip `--target` options
- For Java include the relevant `.jar` files

- Upload the zip straight to Lambda if less than 50mb, else to S3 first.
- Native libraries work, they need to be compiled on Amazon Linux.

## /temp

If your function needs to download a big file to work, you can use the /tmp directy. Max size is 512MB. It is not permanent. If you need permanent, use S3.

## Best Practices

- Perform heavy duty work outside of your function handlers.
  - Connect to databases outside of your function handler.
  - Initalize the AWS SDK outside of your function handler
  - Pull in dependencies or datasets outside of your function handler.
- Use environmental variables for:
  - Database connection strings, S3 buckets, etc. Do not put these values directly in your code.
  - Passwords, sensitive values, they can be encrypted using KMSes.
- Minimize your deployment package size to its runtime necessities
  - Break down the functions if need be
  - Remember the AWS Lambda limits
- Avoid using recursive code, never have a Lambda function call itself.
- Don't put your Lambda function in a VPC unless you have to.