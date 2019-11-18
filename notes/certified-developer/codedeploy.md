# CodeDeploy

We want to deploy our application automatically to many EC2 instances.

* These instances are not managed by Elastic Beanstalk.
* This can be handled via Ansible, Terraform, Chef, Puppet, CodeDeploy, etc.

## How to make it work

* Each EC2 machine (or on-premise) must be running the CodeDeploy Agent.
* The agent is continuously polling CodeDeploy for work to do (should I deploy?).
* CodeDeploy sends **appspec.yml**
* Application is pulled from GitHub or S3.
* EC2 will run the deployment instructions.
* CodeDeploy Agent will report of success / failure of deployment on the instance.

## Other

* EC2 instances are grouped by development group (dev / test / production).
* Lots of flexibility to define any kind of deployments.
* CodeDeploy can be chained into CodePipeline and use artifacts from there.
* CodeDeploy can re-use existing setup tools, works with any application, auto scaling integration.
* Note: Blue / Green only works with EC2 instances (not on-premise).
* Support for Lambda deployments.
* Does not provision resources.

## Hooks

Hooks are a set of instructions to do to deploy the new version. Hooks can have timeouts. The order is:

* ApplicationStop
* DownloadBundle
* BeforeInstall
* AfterInstall
* ApplicationStart
* **ValidateService: really important, make sure application is working**

## Deployment Configuration

* Configs:
  * One at a time: one instance at a time, one instance fails => deployment stops.
  * Half at a time.
  * All at once: quick but no healthy host, downtime. Good for dev.
  * Custom: min healthy host = 75%.
* Failures:
  * Instances stay in failed state.
  * New deployments will first be deployed to "failed state" instances.
  * To rollback: redeploy old deployment or enable automated rollback for failures.

## Setting Up CodeDeploy

1. Create EC2 instance
1. SSH into it and configure it.
    1. `sudo yum update`
    1. `sudo yum install ruby`
    1. `wget https://aws-codedeploy-eu-west-3.s3.eu-west-3.amazonaws.com/latest/install`
    1. `chmod +x ./install`
    1. `sudo ./install auto`
    1. `sudo service codedeploy-agent status`
1. Add a tag to the EC2 instance, key="Environment", value="Dev"
1. Create a deployment group on CodeDeploy.
