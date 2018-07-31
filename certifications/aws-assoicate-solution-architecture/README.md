# Prepare

* AWS Certified Solutions Architect Official Study Guide: Associate Exam

* Linux Academy
* Whizlab practics test
* A CloundGuru
* White paper

# Scope Summary
Resources aren’t replicated across regions unless organizations choose to do so.

| Service  |Scope   | 
| :--- | :-------------------------- | 
| EBS | EBS volume is automatically replicated within its Availability Zone|
| EBS | EBS volume can only attach to the EC2 instance in the same AZ|
| ELB allow to distribute traffic across..  | Multiple AZ within a region |
| What Amazon Relational Database Service (Amazon RDS) feature provides the high availability for your database?  | Multi-AZ deployment |
|How is data stored in Amazon Simple Storage Service (Amazon S3) for high durability?|Data is automatically replicated to different Availability Zones within a region.|
|Subnet|A subnet is located in one specific availability zone, and does not span AZs|

# Reading
* [Done]Chapter 1: Introduction to AWS
* [Done]Chapter 2: Amazon Simple Storage Service (Amazon S3) and Amazon Glacier Storage
* [Done]Chapter 3: Amazon Elastic Compute Cloud (Amazon EC2) and Amazon Elastic Block Store (Amazon EBS)
* [Done]Chapter 4: Amazon Virtual Private Cloud (Amazon VPC)
* [Done]Chapter 5: Elastic Load Balancing, Amazon CloudWatch, and Auto Scaling
* [Done]Chapter 6: AWS Identity and Access Management (IAM)
* [Done]Chapter 7: Databases and AWS
* [Done]Chapter 8: SQS, SWF, and SNS
* Chapter 9: Domain Name System (DNS) and Amazon Route 53
* Chapter 10: Amazon ElastiCache
* Chapter 11: Additional Key Services
* Chapter 12: Security on AWS
* Chapter 13: AWS Risk and Compliance
* Chapter 14: Architecture Best Practices

# Topics
* How do I connect a public-facing load balancer to EC2 instances that have private IP addresses?

It is possible, but you must create public subnets in the same Availability Zones as the private subnets that are used by your private instances. Then associate these public subnets to the internet-facing load balancer.

https://aws.amazon.com/premiumsupport/knowledge-center/public-load-balancer-private-ec2/