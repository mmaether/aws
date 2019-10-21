# EC2

## AWS Regions

AWS has regions all around the world (us-east-1).

Each region has **availability zones** (AZ) (us-east-1a, us-east-1b...). Can go up to 6 currently, most are upwards 3.

* us-east-1a
* us-east-1b
* us-east-1c
* us-east-1d
* us-east-1e
* us-east-1f

Each availability zone is a **physical data center** in the region, but separate from one another (so that they're isolated from disasters).

![AWS Regions](images/aws_regions.png)

AWS Consoles are region scoped (except IAM and S3).
