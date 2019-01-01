# Quiz
Set the DeletionPolicy on the S3 resource declaration in the CloudFormation template to retain, set the RDS resource declaration DeletionPolicy to snapshot.

AD Connector is your best choice when you want to use your existing on-premises directory with AWS services. A large AD Connector can support up to 5,000 users.

Each NAT gateway is created in a specific Availability Zone and implemented with redundancy in that zone.

Internal Route 53 resource record sets only work if the originating request is made from within the VPC. Internal Route 53 record sets cannot be extended to on-premise usage.

Route53:  public resource record  and private resource recodrd

The PEM keys will not be copied to the new region but the authorization keys will still be in the operating system of the AMI. You need to ensure when the new AMI is launched that it is launched with the same PEM key name.

CloudFront download distribution/stream ditstribution

## Linux Academcy

* Q1.  You've been tasked with creating file level restore on your EC2 instances. You need to be able to restore an individual lost file on an EC2 instance within 15 minutes of a reported loss of information. The acceptable RPO is several hours. How would you perform this on an EC2 instance?

Take frequent snapshots of EBS volumes, create a volume from an EBS snapshot, attach the EBS volume to the EC2 instance at a different mount location, browse the file system to the file that needs to be restored on the new mount, copy from the new volume to the backup volume

Explanation
The question asks how you restore a "single" file. Restoring a whole volume would actually cause data loss if those other files were being updated

* Q2. BCJC has many employees who need to run internal applications that access the company's AWS resources. These employees already have user credentials in the company's current identity authentication system, which does not support SAML 2.0. The company does not want to create a separate IAM user for each company employee. How should the SSO setup be designed?

Create a custom identity broker application which authenticates employees using the existing system and uses the AssumeRole API call to gain temporary, role-based access to AWS., Create a custom identity broker application which authenticates the employees using the existing system, uses the GetFederationToken API call and passes a permission policy to gain temporary access credentials from STS.

* Q3. BCJC has developed a Ruby on Rails content management platform. Currently, BCJC is using OpsWorks with several stacks for dev, staging, and production to deploy and manage the application. BCJC is about to implement a new feature on the CMS application using Python instead of Ruby. How should BCJC deploy this new application feature?

BCJC should create a new stack that contains a new layer with the Python code. To cut over to the new stack BCJC should consider using Blue/Green deployment

* Q4. You're consulting for a new customer, who is attempting to create a hybrid network between AWS and their on-premise data centers. Currently, they have internal databases running on-premise that, due to licensing reasons, cannot be migrated to AWS. The front end of the application has been migrated to AWS and uses the DB hostname "db.internalapp.local" to communicate with the on-premise database servers. Hostnames provide an easy method for updating IP addresses in event of failover instead of having to update the IP address in the code. Given the current architecture what is the best way to configure internal DNS for this hybrid application? (Choose Two)

Use an existing on-premise DNS server to configure hostnames for internal DNS records. Create a new Amazon VPC DHCP Option Set with the internal DNS server's IP address., Create an EC2 instance DNS server to configure hostnames for internal DNS records, Create a new Amazon VPC DHCP option set with the internal DNS server's IP address.

Explanation
The application is an internal application. Using a public IP address would cause the application to route externally, which is not part of the desired architecture. Internal Route 53 record sets would not work since Route 53 internal resource record sets only work for requests originating from within the VPC and currently cannot extend to on-premise.

* Q5. Your company has just purchased some very expensive software which also involved the addition of a unique license for it. You have been told to set this up on an AWS EC2 instance; however, one of the problems is that the software license has to be tied to a specific MAC address and from your experience with AWS you know that every time an instance is restarted it will almost certainly lose it's MAC address. What would be a possible solution to this given the options below?

Use a VPC with an elastic network interface that has a fixed MAC Address.

* Q6. BCJC is running data application on-premise that requires large amounts (TBs) of data to be transferred to a VPC containing EC2 instances in an AWS region. BCJC is concerned about the total overall transfer costs required for this application and is potentially not going deploy a hybrid environment for the customer-facing part of the application to run in a VPC. Given that the data transferred to AWS is new data every time, what suggestions could you make to BCJC to help reduce the overall cost of data transfer to AWS?

Suggest provisioning a Direct Connect connection between the on-premise data center and the AWS region.

* Q7. You are setting up a video streaming service with the main components of the set up being S3, CloudFront and Transcoder. Your video content will be stored on AWS S3, and your first job is to upload 10 videos to S3 and make sure they are secure before you even begin to start thinking of streaming the videos. The 10 videos have just finished uploading to S3, so you now need to secure them with encryption at rest. Which of the following would be the best way to do this?

Use KMS to decrypt source data and encrypt resulting output. Also, use Origin Access Identity on your CloudFront distribution, so content is only able to be served via CloudFront, not S3 URLs.

* Q8. An online gaming server in which you have recently increased it's IOPS performance, by creating a RAID 0 configuration has now started to have bottleneck problems due to your instance bandwidth. Which of the following would be the best solution for this to increase throughput?

Use instance store backed instances and stripe the attached ephemeral storage devices and use DRBD Asynchronous Replication.

 * Q9. After having created a VPC with CIDR block 10.0.0.0/24 and launching it as a working network you decide a few weeks later that it is too small and you wish to make it larger. Which of the below options would accomplish this successfully?

Correct answer
Add a CIDR to the VPC with CIDR 10.1.0.0/16

Explanation
Amazon Virtual Private Cloud (VPC) now allows customers to expand their VPCs by adding secondary IPv4 address ranges (CIDRs) to their VPCs. Customers can add the secondary CIDR blocks to the VPC directly from the console or by using the CLI after they have created the VPC with the primary CIDR block.

* Q10.  The Dynamic Host Configuration Protocol (DHCP) provides a standard for passing configuration information to hosts on a TCP/IP network. You can have multiple sets of DHCP options, but you can associate only one set of DHCP options with a VPC at a time. You have just created your first set of DHCP options, associated it with your VPC but now realize that you have made an error in setting them up and you need to change the options. Which of the following options do you need to take to achieve this?

Correct answer
You must create a new set of DHCP options and associate them with your VPC.

* Q11. You are excited that your company has just purchased a Direct Connect link from AWS as everything you now do on AWS should be much faster and more reliable. Your company is based in Sydney, Australia so obviously the Direct Connect Link to AWS will go into the Asia Pacific (Sydney) region. Your first job after the new link purchase is to create a multi-region design across the Asia Pacific(Sydney) region and the US West (N. California) region. You soon discover that all the infrastructure you deploy in the Asia Pacific(Sydney) region is extremely fast and reliable, however the infrastructure you deploy in the US West(N. California) region is much slower and unreliable. Which of the following would be the best option to make the US West(N. California) region a more reliable connection?

Correct answer
Create a public virtual interface to the US West region's public end points and use VPN over the public virtual interface to protect the data.

* Q12.  You have just set up your first AWS Data Pipeline. AWS Data Pipeline is a web service that you can use to automate the movement and transformation of data. With AWS Data Pipeline, you can define data-driven workflows, so that tasks can be dependent on the successful completion of previous tasks. You are pretty excited that it is about to run; however, when it finally kicks off, you receive a "400 Error Code: PipelineNotFoundException." Which of the following explanations is the most accurate in describing what this error probably means?

This error means that your IAM default roles might not have the required permissions necessary for AWS Data Pipeline to function correctly.

* Q13. You are designing multi-region architecture and you want to send users to a geographic location based on latency- based routing, which seems simple enough; however, you also want to use weighted-based routing among resources within that region. Which of the below setups would best accomplish this?

You will need to use complex routing (nested record sets) and ensure that you define the weighted resource record sets first.

* Q14. BCJC is building out an AWS Cloud Environment for a financial regulatory firm. Part of the requirements are being able to monitor all changes in an environment and all traffic sent to and from the environment. What suggestions would you make to ensure all the requirements for monitoring the financial architecture are satisfied? (Choose Two)

Configure an IPS/IDS system, such as Palo Alto Networks, that monitors, filters, and alerts of all potential hazard traffic leaving the VPC., Configure an IPS/IDS to listen and block all suspected bad traffic coming into and out of the VPC. Configure CloudTrail with CloudWatch Logs to monitor all changes within an environment.

* Q15. You have created a VPC with CIDR block 10.0.0.0/24, which supports 256 IP addresses. You want to now split this into two subnets, each supporting 128 IP addresses and allowing for 123 hosts addresses. Can this be done and if so how will the allocation of IP addresses be configured?

One subnet will use CIDR block 10.0.0.0/25 (for addresses 10.0.0.0 - 10.0.0.127) and the other will use CIDR block 10.0.0.128/25 (for addresses 10.0.0.128 - 10.0.0.255).

* Q16. In an attempt to cut costs your accounts manager has come to you and tells you that he thinks that if the company starts to use consolidated billing that it will save some money. He also wants the billing set up in such a way that it is relatively simple, and it gives insights into the environment regarding utilization of resources. Which of the following consolidated billing setups would satisfy your account manager's needs?

Use one master account and many sub accounts., Use one account but multiple VPCs to break out environments.

* Q17. When you create a subnet, you specify the CIDR block for the subnet. The CIDR block of a subnet can be the same as the CIDR block for the VPC (for a single subnet in the VPC), or a subset (to enable multiple subnets). The allowed block size is between a /28 netmask and /16 netmask. You decide to you create a VPC with CIDR block 10.0.0.0/24. Therefore what is the maximum allowed number of IP addresses and the minimum allowed number of IP addresses according to AWS and what is the number of IP addresses supported by the VPC you created?

Maximum is 65,536 and the minimum is 16 and the one created supports 256 IP addresses

* **Q18??**. You are setting up a website for a small startup company. You have built them what you believe to be a great solution on AWS for the money they wanted to spend. It is a very image intensive site, so you have utilized CloudFront to help with the serving of images. The client complains to you, however, that he requires a custom domain name when serving up this content that should work with https from CloudFront, so rather than being provided with a xxxx.cloudfront.net domain he wants a custom domain such as ssuc.com. What would you need to do to accomplish what the customer is asking?

You must provision and configure your own SSL certificate in IAM and associate it to your CloudFront distribution.

* Q19. BCJC has developed a viral marketing website that specializes in posting blog posts that go viral. The posts usually receive 90% of the viral traffic within 24 hours of being posted and often need to be updated with corrections during the first 24 hours. What would be the best method for implementing a solution to help handle the scale of requests given the behavior of the blog posts?

Use a CloudFront CDN and configure 0 TTL and enable URL parameter forwarding to the origin.

Explanation
While ElastiCache with write through would technically work, since 90% of the requests occur in the first 24 hours, using write through will hog a lot of resources and be an expensive caching strategy. Given the requirements of short-lived caching, a TTL of 0 allows the edge location to keep a TCP connection open and use headers to determine if the dynamic object has been updated.

## Whizlab

