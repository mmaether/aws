# AWS CLI Cheatsheet

This document's purpose is to provide quick access to common commands that I will often reuse.

Command | Result
------- | ------
`ssh -i /path/my-key-pair.pem ec2-user@ec2-198-51-100-1.compute-1.amazonaws.com` | Log into EC2 machine
`aws ec2 run-instances --dry-run --image-id ami-123456789 --instance-type t2.micro` | Do a test dry run to see if you can create an EC2 instance.
