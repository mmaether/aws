# AWS CLI Cheatsheet

This document's purpose is to provide quick access to common commands that I will often reuse.

Command | Result
------- | ------
`ssh -i /path/my-key-pair.pem ec2-user@ec2-198-51-100-1.compute-1.amazonaws.com` | Log into EC2 machine
`aws configure` | Run through and enter your Access Key ID and Secret Access Key in the CLI to gain access.
`aws configure --profile my-other-aws-account` | Create another profile that you can use for credentials via CLI.
`aws s3 ls --profile my-other-aws-account` | Runs an AWS command with the other profile.
`aws ec2 run-instances --dry-run --image-id ami-123456789 --instance-type t2.micro` | Do a test dry run to see if you can create an EC2 instance.
`decode-authorization-message --encoded-message <value>` | If there is an error message, you may need to run this command to decode it.

## AWS EC2 Instance Metadata

AWS EC2 Instance Metadata allows instances to learn about themselves without using an IAM role. The URL is [http://169.254.169.254/latest/meta-data/](http://169.254.169.254/latest/meta-data/).

1. SSH into EC2 instance.
2. Run `curl http://169.254.169.254/latest/meta-data/`
3. View details such as IP address.
