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

## VPC
Q1. Which of the following will occur when an Amazon Elastic Block Store (Amazon EBS)- backed Amazon EC2 instance in an Amazon VPC with an associated EIP is stopped and started? (Choose 2 answers)

```
A. The EIP will be dissociated from the instance.
>>>>B. All data on instance-store devices will be lost.
C. All data on Amazon EBS devices will be lost.
D. The ENI is detached.
>>>>E. The underlying host for the instance is changed.
```

Q2. You cannot peer two VPCs that located in different AWS regions.

```
Correct answer
False

Explanation
VPC can now be connected across regions.
```

Q3. You are trying to establish a VPC peering connection but are having difficulties locating the other VPC. What is most likely the cause?

```
Correct answer
The other VPC has the same CIDR Block Range

Explanation
For a VPC peering to work, the VPC cannot have overlapping CIDR block ranges
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


## ELB and Auto Scaling
Q1. Which of the following are required elements of an Auto Scaling group? (Choose 2answers)

```
>>>>A. Minimum size
B. Health checks
C. Desired capacity
>>>>D. Launch configuration
An Auto Scaling group must have a minimum size and a launch configuration
defined in order to be created. Health checks and a desired capacity are optional.
```

Q2. Which of the following are the minimum required elements to create an Auto Scaling launch configuration?

```
>>>>A. Launch configuration name, Amazon Machine Image (AMI), and instance type
B. Launch configuration name, AMI, instance type, and key pair
C. Launch configuration name, AMI, instance type, key pair, and security group
D. Launch configuration name, AMI, instance type, key pair, security group, and block device mapping

Only the launch configuration name, AMI, and instance type are needed to create an
Auto Scaling launch configuration. Identifying a key pair, security group, and a block
device mapping are optional elements for an Auto Scaling launch configuration
```

Q3. In the basic monitoring package for Amazon Elastic Compute Cloud (Amazon EC2), what Amazon CloudWatch metrics are available?

```
A. Web server visible metrics such as number of failed transaction requests
(Wrong)B. Operating system visible metrics such as memory utilization
C. Database visible metrics such as number of connections
>>>>D. Hypervisor visible metrics such as CPU utilization
```

Q4. When an Amazon Elastic Compute Cloud (Amazon EC2) instance registered with an Elastic Load Balancing load balancer using connection draining is deregistered or unhealthy, which of the following will happen? (Choose 2 answers)

```
A. Immediately close all existing connections to that instance.
>>>>B. Keep the connections open to that instance, and attempt to complete in-flight requests.
>>>>C. Redirect the requests to a user-defined error page like “Oops this is embarrassing” or “Under Construction.”
D. Forcibly close all connections to that instance after a timeout period.
E. Leave the connections open as long as the load balancer is running.

When connection draining is enabled, the load balancer will stop sending requests
to a deregistered or unhealthy instance and attempt to complete in-flight requests until a
connection draining timeout period is reached, which is 300 seconds by default
```

Q5. If your application is continually crashing due to high demand, you should make sure the Elastic Load Balancer has the proper scaling polices for adding new instances when needed.

```

Correct answer
False

Explanation
It is Auto Scaling that contains scaling policies (which dictate the CloudWatch thresholds for adding/removing instances).
```

Q6. What best describes the purpose of an Elastic Load Balancer?

```
Correct answer
To evenly distribute traffic among multiple EC2 instances in separate Availability Zones.

Explanation
An ELB is used BEST when it is distributing traffic to EC2 instances located in separate Availability Zones. This provides for higher availability and is more fault tolerant than distributing traffic to EC2 instances in the same AZ
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



## Database
Q1. 11. You are building the database tier for an enterprise application that gets occasional activity throughout the day. Which storage type should you select as your default option?

```
A. Magnetic storage
>>>>B. General Purpose Solid State Drive (SSD)
C. Provisioned IOPS (SSD)
D. Storage Area Network (SAN)-attached
```

## SQS, SNS and SWF
Q1.  You are a solutions architect who is working for a mobile application company that wants to use Amazon Simple Workflow Service (Amazon SWF) for their new takeout ordering application. They will have multiple workflows that will need to interact. What should you advise them to do in structuring the design of their Amazon SWF environment?

```
A. Use multiple domains, each containing a single workflow, and design the workflows to interact across the different domains.
>>>>B. Use a single domain containing multiple workflows. In this manner, the workflows will be able to interact.
C. Use a single domain with a single workflow and collapse all activities to within this single workflow.
D. Workflows cannot interact with each other; they would be better off using Amazon
Simple Queue Service (Amazon SQS) and Amazon Simple Notification Service (Amazon SNS) for their application.


Use a single domain with multiple workflows. Workflows within separate domains cannot interact.
```

## Deployment service
Q1. Elastic BeanStalk is primarily used to deploy complex, multi-tier applications.

```
Correct answer
False

Explanation
Elastic BeanStalk is primarily used to deploy simple, single-tier applications.
```

## Security
Q1. Perfect Forward Secrecy is used to offer SSL/TLS cipher suites for which two AWS services?

```

Correct answer
Cloudfront and Elastic Load Balancing
```

Q2.  What feature should you utilize for redundancy if auto scaling and load balancing are not available?

```
Correct answer
Elastic IP address set up for failover to "stand-by" instances

Explanation
Setting up an Elastic IP address and having it ready for failover is a great solution when other services that provide high availability and fault tolerance are not available.
```

# Linux

Q1.  You recently purchased four reserved EC2 instances in the US-East-1 region’s Availability Zone 1. Your supervisor just informed you that she would like the instances distributed equally across US-East-1 region Availability Zones 1 and 2. Can you use the reserved instances you just purchased to deploy EC2 instances in Availability Zone 2?

```
Correct answer
Yes, you can migrate the reserved instances to Availability Zone 2
```

Explanation
After recent AWS updates you can now migrate reserved instances without having to sell and repurchase. Another resource link: https://aws.amazon.com/ec2/purchasing-options/reserved-instances/buyer

Further Reading
https://aws.amazon.com/ec2/pricing/reserved-instances/


Q2. Your company has moved a legacy application from an on-premises data center to the cloud. The legacy application requires a static IP address hard-coded into the backend, which prevents you from deploying the application with high availability and fault tolerance using the ELB. Which steps would you take to apply high availability and fault tolerance to this application?

```
Correct answer
Ensure that the instance it's using has an elastic IP address assigned to it, Write a custom script that pings the health of the instance, and, if the instance stops responding, switches the elastic IP address to a standby instance
```

Q3.  The KPL is an easy-to-use, highly-configurable library that helps you write to an Amazon Kinesis stream. It acts as an intermediary between your producer application code and the stream's API actions. One of its key concepts is aggregation. Which of the following best describes aggregation as it relates to the KPL?

```
Correct answer
It refers to the storage of multiple records in a stream's record and allows 
customers to increase the number of records sent per API call, which effectively increases producer throughput
```

Explanation
KPL aggregation directly refers to the storage of multiple records in a Kinesis Data Streams record. This, in turn, allows increase producer throughput. The Kinesis Data Streams records per second limit binds customers with records smaller than 1 KB. Record aggregation allows customers to combine multiple records into a single Kinesis Data Streams record.
```

Q4. You are setting up a VPC peering connection with another VPC. This is the first time that you have done this, and you are not that familiar with the limitations and rules. When reading up on this, you discover that there seems to be a lot of limitations and rules when it comes to VPC peering. Which of the following is NOT one of those limitations or rules?

```
Correct answer
You cannot create a VPC peering connection between VPCs in different regions, A placement group cannot span peered VPCs
```

Q5. You are building a system to distribute confidential training videos to employees. Using CloudFront, what method would be used to serve content that is stored in S3 but not publicly accessible from S3 directly?

```
Correct answer
Create an Origin Access Identify (OAI) for CloudFront and grant access to the objects in your S3 bucket to that OAI
```

Q6.  Auto Scaling is a tool used for creating elastic and self-healing applications.

```
Correct answer
True
```

Q7.  After deciding that, due to strict contractual requirements, the latest AWS VPC that you deploy will need to incorporate AWS CloudHSM as an encryption solution, where within your AWS infrastructure would be the best place to physically locate the HSM appliances and why?

```
Correct answer
Locate HSM appliances near your EC2 instances decreases network latency, which can improve application performance
```

Q8. What is the maximum size of a general SSD EBS volume?

```
Correct answer
16 TiB

1 TiB = 1.09951 TB
```

Q9. Your EC2 instances are configured to run behind an Amazon VPC. You have assigned two web servers instances to an Elastic Load Balancer. However, the instances and the ELB are not reachable via URL to the elastic load balancer serving the web app data from the EC2 instances. How might you resolve the issue so that your instances are serving the web app data to the public internet?

```
Correct answer
Attach an internet gateway to the VPC and route it to the subnet
```

Q10.After building an application that makes use of an Elastic Load Balancer over port 80, you notice that your instances, even though they are healthy as per the health check, are not serving traffic when you go to the ELB DNS cname. What might be the cause of this issue?

```
Correct answer
The ELB security group does not have port 80 open, The EC2 instances security group does not have port 80 open
```
Explanation
Remember that health checks do not have to be performed on port 80. This is the default, yes, but it can be changed. So in this case we could have a health check configured on a different port which is why it would be marked as healthy even though the ELB security group and/or the EC2 instance security group on port 80 could be closed. Even if this scenario does not sound very likely, it is possible. AWS likes to try and trick test takers by throwing in scenarios like these, which is why we included this tricky question.




