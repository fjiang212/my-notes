# Notes
## AWS Document

https://docs.aws.amazon.com/cli/latest/

### IAM
https://docs.aws.amazon.com/kms/latest/developerguide/concepts.html


### EC2

### S3


### DynamoDB
* https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.CoreComponents.html
* https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/SQLtoNoSQL.ReadData.SingleItem.html

### SQS, SNS, WCF


### Lambda

### Beanstalk

### CloudFormation

### Route53

### VPC

### APIs
* https://docs.aws.amazon.com/IAM/latest/APIReference/Welcome.html
* https://docs.aws.amazon.com/AWSEC2/latest/APIReference/Welcome.html
* https://docs.aws.amazon.com/AmazonS3/latest/API/Welcome.html


### FAQs
* https://aws.amazon.com/ec2/faqs/
* https://aws.amazon.com/s3/faqs/

# Number Related
https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html

## Resource Limit
| Service  |Resource   | Limit | 
| :--- | :-------------------------- | :------------------ |
| EC2  | Instance | 20 (contact amazon) |
| EC2  | Elastic IP Address | 5 |
|  |  |  |
| S3  | Single put| 5G |
| S3  | Object size | 5T |
| S3  | Buckets | 100 per account |
|  |  |  |
| DynamoDB  | Smallest Reserved Capacity | 100 |
| DynamoDB  | Tags per Table | 50 |
| DynamoDB  | table partition | max 3000 read CU or 1000 WU |
| DynamoDB | Item collection  |10GB |
| DynamoDB | BatchGetItem | max 100 items, < 16MB| 
|  |  |  |
| Beanstalk  | Applications | 75 |
| Beanstalk  | Applications Version | 1000 |
| Beanstalk  | Environments | 200 |
|  |  |  |
| CloudFormation  | template | unlimited |
| CloudFormation  | stacks  | 200 |
| CloudFormation  | parameters and oupts in template | 60 |
|  |  |  |
| SQS  | Message Size | 256KB |
| SQS  | Standard queue TPS per API Action| unlimited |
| SQS  | FIFO queue TPS per API Action| 300 |
| SQS  | Standard queue inflight message| 120,000  |
| SQS  | FIFO queue Tinflight message|| 20,000 |
|  |  |  |
| SNS | SMS message | 140 bytes |  
|  |  |  |
| SWF | Domain | 100 |  
| SWF | Activity tasks in one decision | 100 |  
| SWF | Maximum workflow and actiivty tasks | 10,000 |  
|  |  |  |
| VPC | Internet Gateway | one per VPC|  
| VPC | NACL | one per subnet |  
| VPC | Route Table | one per subnet |  
| VPC | Available Zone | one per subnet |  

## Limit and default value
| Service  | Item   | Range | Default |
| :-------- | :-------| :-----  |:----- |
| IAM | Default expiration for the temporary credential | 15 minutes ~ 36 hours |12 hours |
| IAM | AssumeRoleAPIs | 15 minutes ~ 12 hours | |
|  |  |  |  |
| DynamoDB | min length of partition key | 1byte ~ 2048byte | |
| DynamoDB | min length of sort key | 1byte ~ 1024byte | |
|  |  |  |  |
| SQS | Visibility Timeout | 0 ~ 12 hours| 30s |
| SQS | Long Poll Timeout | 0 ~ 20s |  |
| SQS | retention period | 1minute ~ 14 days | 4 days |
|  |  |  |  |
| SNS | subscription request valid |  | 3 days |
|  |  |  |  |
| SWF | maximum workflow |  | 1 year |


# Related knowledge
## IAM
* SAML: [Intro to SAML: What, How and Why](https://www.youtube.com/watch?v=0fmNoqz6Urw)

## DynamoDB


# References

* https://aws.amazon.com/cli/
* https://aws.amazon.com/whitepapers/
* [AWS Certification Training Videos](https://www.youtube.com/watch?v=IT1X42D1KeA&list=PL9ooVrP1hQOFWxRJcGdCot7AgJu29SVV3)

# Read later
* https://docs.aws.amazon.com/AmazonS3/latest/dev/request-rate-perf-considerations.html
* https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Programming.Errors.html


# Todo
* SNS message body
* Cloudformation example
* API summary
* cli summary
* sns long/short code, mobile subscription
