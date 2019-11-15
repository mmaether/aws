# EBS Volumes

* An EC2 machine loses its root volume (main drive) when it is manually terminated.
* Unexpected terminations might happen from time to time.
* Sometimes you need a way to store your instance data somewhere.
* An EBS (Elastic Block Store) Volume is a network drive you can attach to your instances while they run.
* It allows your instances to persist data.

What are EBS Volumes?

* It's a network drive (i.e. not a physical drive).
  * It uses the network to communicate the instance, which means there might be a bit of latency.
  * It can be detached from an EC2 instance and attached to another one quickly.
* It's locked to an Availability Zone (AZ).
  * An EBS Volume in us-east1a cannot be attached to us-east-1b.
  * To move a volume across, you first need to snapshot it.
* Have a provisioned capacity (size in GBs, and IOPS).
  * You get billed for all the provisioned capacity.
  * You can increase the capacity of the drive.

## EBS Volume Types

* GP2 (SSD): General purpose SSD volume that balances price and performance for a wide variety of workloads.
* IO1 (SSD): Highest-performance SSD volume for mission critical low-latency or high-throughput workloads.
* STI (HDD): Low cost HDD volume designed for frequently accessed, throughput-intensive workloads.
* SCI (HDD): Lowest cost HDD volume designed for less frequently accessed workloads.

## EBS Volume Resizing

You can resize the EBS volumes:

* Size (any volume type)
* IOPS (only in IO1)

After reizing an EBS volume, you need to repartition your drive.

## EBS SNapshots

* EBS Volumes can be backed up using snapshots.
* Snapshots only take the actual place of the blocks on the volume.
* If you snapshot a 100GB drive that only has 5GB of data, then your EBS snapshot will only be 5GB.
* Snapshots are used for:
  * Backups: ensuring you can save your data in case of catastrophe.
  * Volume migration:
    * Resizing a volume down.
    * Changing the volume type.
    * Encrypt a volume.

## EBS vs Instance Store

Some instances do not come with Root EBS volumes. Instead they come with "Instance Store." Instances store is physically attached to the machine.

Pros:

* Better I/O Performance.

Cons:

* On termination, the instance store is lost.
* You can't resize the instance store.
* Backups must be operated by the user.

Overall, EBS-backed instances should fit most applications workloads.

## Brain Dump

* EBS can be attached to only one instance at a time.
* EBS are locked at the AZ level.
* Migrating an EBS volume across AZ means backing it up (snapshot), then recreating it in the other AZ.
* EBS backups use IO and you shouldn't run them while your application is handling a lot of traffic.
* Root EBS Volumes of instances get terminated by default if the EC2 instance gets terminated (you can disable that).