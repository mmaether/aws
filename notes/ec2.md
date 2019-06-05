# EC2: Elastic Compute Cloud

## Summary

Amazon's EC2 is perhaps their flagship product. It allows clients to create virtualized servers located in Amazon's datacenter. This allows for flexibility of spinning up and down servers without having to pay for dedicated hardware.

## EC2 Types

- On Demand: allows you to pay a fixed rate by the hour (or second) with no committment. 
  - Low cost and flexibility without long-term commitments. Short term, spiky, or unpredictable. Testing on Amazon for the first time.
- Reserved: provides you with a capacity reservation, and offer a significant discount on the hourly charge for an instance. 1 year or 3 year terms
  - Applications with steady state or predictable usage. Web servers. Make up-front payments to reduce the costs even further. 
  - Standard reserved instances (RIs) up to 75% off on-demand. 
  - Convertible RIs (up to 54% off on-demand) feature the capability to change the attributes of the RI as long as the exchange results in the creation of RIs of equal or greater value.
  - Scheduled RIs are available to launch within the time window you reserve. Allows you to match the capacity reservation to a predictable recurring schedule that only requires a fraction of a day/week/month.
- Spot: like the stock market. enables you to bid whatever price you want for instance capacity, providing for even greater savings if your applications have flexible start and end times.
  - Flexible start and end time. Only feasible at very low compute prices. Genome field, pharmaceutical, checmical companies use this for huge amounts of computing at 4am.
- Dedicated hosts: physical EC2 server dedicated for your use. dedicated hosts can help you reduce costs by allowing you to use your existing server-bound software licenses, e.g. Oracle, VMWare, SQL servers.
  - Useful for regulatory requirements that may not support multi-tenant virtualization, such as healthcare.
  - Great for licensing
  - Can be purchased on-demand (hourly)
  
  
## Instance Types

Amazon had originally released a set of instance types with the following. A way to remember this is by calling it **Dr. McGiftpx**, a nicer Scrooge McDuck gifting people pictures of Scotland.

- D for density
- R for RAM
- M for main choice for general purpose apps
- C for compute
- G for graphics
- I for IOPS
- F for FPGA
- T for cheap general purpose (think T2 micro)
- P for graphics (think Pics)
- X for extreme memory

As Amazon updates relentlessly, this is now out of date. Instead there's a new acronym: 

**Fight Dr. McPx**, which is a picture of Edward Norton from Fight Club kicking the shit out of this poor duck.

- F1: field programmable gate array, genomics research
- I3: high speed storage, NoSQL DBs, data warehousing
- G3: graphics intensive, video encoding, 3d application
- H1: high disk throughput, MapReduced workload, file systems
- T2: lowest cost/general purpose, web servers and small databases
- D2: dense storage, fileservers/data warehousing/hadoop
- R4: memory optimized (think as RAM)
- M5: general purpose, application servers
- C5: computer optimized, CPU intensive apps/dbs
- P3: graphics/general purpose GPU, machine learning and bitcoin
- X1: memory optimized, SAP HANA/Apache Spark

## EBS: Elastic Block Store
Elastic Block Store (EBS) allows you to create storage volumes and attach them to EC2 instances. Once attached you can create a file system on top of these volumes, run a database, or use them in any other way you would use a block device. EBS volumes are placed in a specific Availability Zone, where they are automatically replicated to protect you from the failure of a single component.

- EC2 = A virtual computer
- EBS = A virtual disk

### EBS Volume Types
- General Purpose SSD (GP2)
  - General purpose, balances price and performance.
  - Ratio of 3 IOPS per GB with up to 10,000 IOPS and the ability to burst up to 3000 IOPS for extended periods of time for volumes at 3334 GiB and above.
- Provisioned IOPS SSD (IO1)
  - Designed for I/O intensive applications such as large relational or NoSQL databases.
  - Use if you need more than 10,000 IOPS.
  - Can provision up to 20,000 IOPS per volume.
- Throughput Optimized HDD (ST1), magnetic storage volumes
  - Big data, data warehouses, log processing, cannot be a boot volume.
- Cold HDD (SC1)
  - Lowest cost storage for infrequently accessed workloads. Often file server, cannot be a boot volume.
- Magnetic (standard). Legacy, isn't shown much.
  - Lowest cost per gigabyte of all EBS volume types that is bootable. Magnetic volumes are ideal for workloads where data is accessed infrequently, and applications where the lowest storage cost is important.

## AMI
Amazon Machine Image (AMI) are the different types of EC2 images we can spin up. There are two types of virtualization: 

- HVM
- Paravirtual.

One subnet is always tied to one availability zone. The volume is the same as a hard disk. Root means where we're booting the OS.

- Security Group = Virtual firewall
- HTTP = Port 80

SSH URL: ec2-user@[public IP]

## Security Groups

With security groups, changes happen immediately. This is very important.

Security groups are STATEFUL: If you create an inbound rule allowing traffic in, that traffic is automatically allowed back out again.

- All inbound traffic is blocked by default.
- All outbound traffic is allowed by default.

You can have any number of EC2 instances within a security group. You cannot block specific IP addresses using Security Groups, instead use Network Access Control Lists.
  
The EC2 instance and the volume must exist in the same region. Think of like a desktop where they're tied in the same case.