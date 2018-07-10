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
Todo: SNS message body

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
| -------- | --------- | ----- |
| EC2  | Instance | 20 (contact amazon) |
| EC2  | Applications | 75 |
| -------- | --------- | ----- |
| Beanstalk  | Applications | 75 |
| Beanstalk  | Applications Version | 1000 |
| Beanstalk  | Environments | 200 |
| -------- | --------- | ----- |
| CloudFormation  | template | unlimited |
| CloudFormation  | stacks  | 200 |
| CloudFormation  | parameters and oupts in template | 60 |

 
## Limit and default value
| Service  | Item   | Range | Default |
| -------- | -------| ----- |----- |
| IAM | Default expiration for the temporary credential | 15 minutes ~ 36 hours |12 hours |
| IAM | AssumeRoleAPIs | 15 minutes ~ 12 hours | |



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