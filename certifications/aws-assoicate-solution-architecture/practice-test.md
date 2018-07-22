# Official Study Guide
## Instruction
*  Q1. What type of AWS Elastic Beanstalk environment tier provisions resources to support a
web application that handles background processing tasks?

```
> Worker environment tier

> An environment tier whose web application runs background jobs is known as a
worker tier. An environment tier whose web application processes web requests is
known as a web server tier. Database and batch are not valid environment tiers.
```

* Q2. Which of the following is true if you stop an Amazon Elastic Compute Cloud (Amazon
EC2) instance with an Elastic IP address in an Amazon Virtual Private Cloud (Amazon
VPC)?

```
> The instance remains associated with its Elastic IP address.
```

## S3
* Q1. Your application stores critical data in Amazon Simple Storage Service (Amazon S3), which must be protected against inadvertent or intentional deletion. How can this data be protected? (Choose 2 answers)

```
> C. Enable versioning on the bucket.
> E. Enable MFA Delete on the bucket.
```

* Q2. Which statements about Amazon Glacier are true? (Choose 3 answers)

```
> C. Amazon Glacier archives take three to five hours to restore.
> D. Amazon Glacier vaults can be locked.
> E. Amazon Glacier can be used as a standalone service and as an Amazon S3 storage class.

Amazon Glacier stores data in archives, which are contained in vaults. Archives 
are identified by system-created archive IDs, not key names.
```

## EC2 and EBS
* Q1. Your order-processing application processes orders extracted from a queue with two Reserved Instances processing 10 orders/minute. If an order fails during processing, then it is returned to the queue without penalty. Due to a weekend sale, the queues have several hundred orders backed up. While the backup is not catastrophic, you would like to drain it so that customers get their confirmation emails faster. What is a cost-effective way to drain the queue for orders?

```
A. Create more queues.
>>>>B. Deploy additional Spot Instances to assist in processing the orders.
C. Deploy additional Reserved Instances to assist in processing the orders.
D. Deploy additional On-Demand Instances to assist in processing the orders.
```

* Q2. You have purchased an m3.xlarge Linux Reserved instance in us-east-1a. In which way can you modify this reservation? (Choose 2 answers)

```
>>>>A. Change it into two m3.large instances.
B. Change it to a Windows instance.
>>>>C. Move it to us-east-1b.
D. Change it to an m4.xlarge.

You can change the instance type only within the same instance type family, or 
you can change the Availability Zone. You cannot change the operating system nor the instance type family
```

Q3. Which of the following are features of enhanced networking? (Choose 3 answers)

```
>>>>A. More Packets Per Second (PPS)
>>>>B. Lower latency
C. Multiple network interfaces
D. Border Gateway Protocol (BGP) routing
>>>>E. Less jitter
```

Q4. Which of the following are true of instance stores? (Choose 2 answers)

```
A. Automatic backups
>>>>B. Data is lost when the instance stops.
>>>>C. Very high IOPS
D. Charge is based on the total amount of storage provisioned.
```

Q5. You are restoring an Amazon Elastic Block Store (Amazon EBS) volume from a snapshot. How long will it be before the data is available?

```
A. It depends on the provisioned size of the volume.
>>>>B. The data will be available immediately.
C. It depends on the amount of data stored on the volume.
D. It depends on whether the attached instance is an Amazon EBS-optimized instance.

The volume is created immediately but the data is loaded lazily. This means that the
volume can be accessed upon creation, and if the data being requested has not yet been
restored, it will be restored upon first request.
```

Q6. You have a workload that requires 1 TB of durable block storage at 1,500 IOPS during normal use. Every night there is an Extract, Transform, Load (ETL) task that requires 3,000 IOPS for 15 minutes. What is the most appropriate volume type for this workload?

```
A. Use a Provisioned IOPS SSD volume at 3,000 IOPS.
B. Use an instance store.
>>>>C. Use a general-purpose SSD volume.
D. Use a magnetic volume.
```

## VPC
Q1. Which of the following will occur when an Amazon Elastic Block Store (Amazon EBS)- backed Amazon EC2 instance in an Amazon VPC with an associated EIP is stopped and started? (Choose 2 answers)

```
A. The EIP will be dissociated from the instance.
>>>>B. All data on instance-store devices will be lost.
C. All data on Amazon EBS devices will be lost.
D. The ENI is detached.
>>>>E. The underlying host for the instance is changed.
```
