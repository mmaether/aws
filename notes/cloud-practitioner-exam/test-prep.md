# AWS Certified Cloud Practitioner Exam Preparation

## IT

AWS Service Catalog: Using cloud resources, it can be frustrating making sure everyone has appropriately levels of access. This helps IT administrators organize, govern, and distribute application stacks or products using CloudFormation templates.

AWS Cloud Adoption Framework (CAF): help organizations design and travel an accelerated path to successful cloud adoption

## Databases

Amazon Aurora: Amazon flavor of MySQL-type databases, optimized for the cloud. 

Amazon Aurora is a MySQL and PostgreSQL compatible relational database built for the cloud, that combines the performance and availability of high-end commercial databases with the simplicity and cost-effectiveness of open source databases. Aurora is up to five times faster than standard MySQL databases and three times faster than standard PostgreSQL databases. It provides the security, availability, and reliability of commercial-grade databases at 1/10th the cost. Aurora is fully managed by Amazon Relational Database Service (RDS), which automates time-consuming administration tasks like hardware provisioning, database setup, patching, and backups.

Amazon Neptune: A graph database service.

Read Replica

Multi-AZ Deployment

--------

Amazon Simple Email Service (SES): Flexible, affordable, and highly-scalable email sending and receiving service for businesses and developers.

AWS Storage Gateway: The AWS Storage Gateway is a service connecting an on-premises software appliance with cloud-based storage to provide seamless and secure integration between an organization's on-premises IT environment and AWS's storage infrastructure.

EFS

Amazon ECS: Amazon Elastic Container Service (ECS) is a compute service that is used to run containerized applications on AWS.

EBS
CloudFormation - Terraform-like?
AWS Direct Connect
Amazon Cognito


CloudEndure

**CloudFront**: Amazon CloudFront is a content caching service provided by AWS that uses Edge Locations (which are AWS data centers located all around the world) to reduce network latency when delivering content to end users.

Edge Locations are used by CloudFront to distribute content to end users with low latency.

CloudWatch
CloudTrail
AWS TCO 
aws elasticity - grow or shrink
AWS artifact

## Big Data

Amazon EMR: Amazon Elastic MapReduce (EMR) is a web service that enables businesses, researchers, data analysts, and developers to easily and cost-effectively process vast amounts of data across dynamically scalable Amazon EC2 instances.


Which of the following EC2 instance purchasing options supports the Bring Your Own License (BYOL) model for almost every BYOL scenario?

Dedicated Hosts are most cost effective when the host is highly utilized and in a steady, non-variable state. A Dedicated Host will support the BYOL scenarios outlined in this FAQ and provide customers with more control and visibility over how their instances are placed, which is useful for minimizing risk and licensing costs in a BYOL scenario. Additionally, Dedicated Hosts support per-socket, per-core, VM, and CAL based licenses. Windows is the most common product brought to Dedicated Hosts.

Amazon EC2 Dedicated Hosts allow you to use your eligible software licenses from vendors such as Microsoft and Oracle on Amazon EC2, so that you get the flexibility and cost effectiveness of using your own licenses, but with the resiliency, simplicity and elasticity of AWS. An Amazon EC2 Dedicated Host is a physical server fully dedicated for your use, so you can help address corporate compliance requirements.

https://aws.amazon.com/ec2/dedicated-hosts/


Sarah has deployed an application in the Northern California (us-west-1) region. After examining the application’s traffic, she notices that about 30% of the traffic is coming from Asia. What can she do to reduce latency for the users in Asia?
Create a CDN using CloudFront

## Compute

Application Load Balancer is best suited for load balancing of HTTP and HTTPS traffic.

AWS Network Load Balancer is best suited for load balancing of TCP and TLS traffic.



## Networking

AWS Direct Connect: AWS Direct Connect is used to establish a dedicated network connection from your premises to AWS. Using AWS Direct Connect, you can establish private connectivity between AWS and your data center, office, or co-location environment, which in many cases can reduce your network costs, increase bandwidth throughput, and provide a more consistent network experience than Internet-based connections.

Network ACLs is used to control traffic at the subnet level.

## Security

AWS WAF: AWS WAF is a web application firewall that helps protect your web applications or APIs against common web exploits that may affect availability, compromise security, or consume excessive resources. AWS WAF gives you control over how traffic reaches your applications by enabling you to create security rules that block common attack patterns, such as SQL injection or cross-site scripting, and rules that filter out specific traffic patterns you define.


## Reading

[AWS Well-Architected](https://aws.amazon.com/architecture/well-architected/)

1. Operational Excellence: The operational excellence pillar includes the ability to run and monitor systems to deliver business value and to continually improve supporting processes and procedures.

2. Security: The security pillar includes the ability to protect information, systems, and assets while delivering business value through risk assessments and mitigation strategies.

3. Reliability: The reliability pillar includes the ability of a system to recover from infrastructure or service disruptions, dynamically acquire computing resources to meet demand, and mitigate disruptions such as  misconfigurations or transient network issues.

4. Performance Efficiency: The performance efficiency pillar includes the ability to use computing resources efficiently to meet system requirements and to maintain that efficiency as demand changes and technologies evolve.

5. Cost Optimization: The cost optimization pillar includes the ability to avoid or eliminate unneeded cost or sub-optimal resources.


IaaS vs PaaS vs SaaS 
SaaS examples: BigCommerce, Google Apps, Salesforce, Dropbox, MailChimp, ZenDesk, DocuSign, Slack, Hubspot.

PaaS examples: AWS Elastic Beanstalk, Heroku, Windows Azure (mostly used as PaaS), Force.com, OpenShift, Apache Stratos, Magento Commerce Cloud.

IaaS examples: AWS EC2, Rackspace, Google Compute Engine (GCE), Digital Ocean, Magento 1 Enterprise Edition*.


## To Learn

- Clusters
- Big Data
- Shared responsibility
- Amazon Inspector
- AWS Config
- AWS Batch
- Network Access Control Lists (NACL)
- ECR
- ECS
- AWS SWF
- CloudFront
- 

## Support

AWS Technical Account Manager (TAM): A Technical Account Manager (TAM) is your designated technical point of contact who provides advocacy and guidance to help plan and build solutions using best practices and proactively keep your AWS environment operationally healthy. TAM is available only for the Enterprise support plan.

APN Consulting Partners: APN Consulting Partners are professional services firms that help customers design, architect, build, migrate, and manage their workloads and applications on AWS. Consulting Partners include System Integrators, Strategic Consultancies, Agencies, Managed Service Providers, and Value-Added Resellers. AWS supports the APN Consulting Partners by providing a wide range of resources and training to support their customers.

AWS Professional Services: AWS Professional Services shares a collection of offerings to help you achieve specific outcomes related to enterprise cloud adoption. AWS Professional Services also trains your team with specialized skills and provides global specialty practices to support your efforts in focused areas of enterprise cloud computing.

APN Technology Partners: APN Technology Partners provide software solutions that are either hosted on, or integrated with, the AWS platform. APN Technology Partners include Independent Software Vendors (ISVs), SaaS, PaaS, Developer Tools, Management and Security Vendors.



Question 29
Question 33


