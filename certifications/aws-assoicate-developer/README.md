# Services
## IAM
https://docs.aws.amazon.com/kms/latest/developerguide/concepts.html

![IAM Policy](images/readme/IAM1.png)

* Identity-based policies: Managed policies(AWS managed policies, customer managed policies), inline policies
    * Effect – whether the policy allows or denies access
    * Action – the list of actions that are allowed or denied by the policy
    * Resource – the list of resources on which the actions can occur
    * Condition (Optional) – the circumstances under which the policy grants permission
    
```
{
  "Version": "2012-10-17",
  "Statement": {
    "Effect": "Allow",
    "Action": "s3:ListBucket",
    "Resource": "arn:aws:s3:::example_bucket"
  }
}
```

* Resource-bases policies
Two Additional fields: Sid(statement id) and Princial.

```
{
  "Version": "2012-10-17",
  "Id": "S3-Account-Permissions",
  "Statement": [{
    "Sid": "1",
    "Effect": "Allow",
    "Principal": {"AWS": ["arn:aws:iam::ACCOUNT-ID-WITHOUT-HYPHENS:root"]},
    "Action": "s3:*",
    "Resource": [
      "arn:aws:s3:::mybucket",
      "arn:aws:s3:::mybucket/*"
    ]
  }]
}
```

## EC2

## S3
* Performance:  Using a sequential prefix, such as time stamp or an alphabetical sequence, increases the likelihood that Amazon S3 will target a specific partition for a large number of your keys, overwhelming the I/O capacity of the partition.

```
examplebucket/2013-26-05-15-00-00/cust1234234/photo1.jpg
examplebucket/2013-26-05-15-00-00/cust3857422/photo2.jpg
```

Change to 

```
examplebucket/232a-2013-26-05-15-00-00/cust1234234/photo1.jpg
examplebucket/7b54-2013-26-05-15-00-00/cust3857422/photo2.jpg
```


* single put: < 5G
* multi-part upload < 5T (recommend for >100mb)
* Import/Export: Use your own device (TB level)
* snowball: Use Amazon device (PB level)
* Storage gateway: Where data mainly store(on-premise or s3)

## DynamoDB
* https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.CoreComponents.html
* https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/SQLtoNoSQL.ReadData.SingleItem.html

## SQS

## SNS
* Short codes, long codes 

```
Short code are are carrier approved to send A2P SMS and thus require carrier approval. 
Long codes are phone number

```
* Message body
    * Headers: started with x-amz-sns
    * MessageId, Message
    * Timestamp, Type, Token, TopicArn,(SubscribeURL?)
    * Signature, SignatureVersion, SigningCertURL


```
POST / HTTP/1.1
x-amz-sns-message-type: SubscriptionConfirmation
x-amz-sns-message-id: 165545c9-2a5c-472c-8df2-7ff2be2b3b1b
x-amz-sns-topic-arn: arn:aws:sns:us-west-2:123456789012:MyTopic
Content-Length: 1336
Content-Type: text/plain; charset=UTF-8
Host: myhost.example.com
Connection: Keep-Alive
User-Agent: Amazon Simple Notification Service Agent

{
  "Type" : "SubscriptionConfirmation",
  "MessageId" : "165545c9-2a5c-472c-8df2-7ff2be2b3b1b",
  "Token" : "2336412f37fb687f5d51e6e241d09c805a5a57b30d712f794cc5f6a988666d92768dd60a747ba6f3beb71854e285d6ad02428b09ceece29417f1f02d609c582afbacc99c583a916b9981dd2728f4ae6fdb82efd087cc3b7849e05798d2d2785c03b0879594eeac82c01f235d0e717736",
  "TopicArn" : "arn:aws:sns:us-west-2:123456789012:MyTopic",
  "Message" : "You have chosen to subscribe to the topic arn:aws:sns:us-west-2:123456789012:MyTopic.\nTo confirm the subscription, visit the SubscribeURL included in this message.",
  "SubscribeURL" : "https://sns.us-west-2.amazonaws.com/?Action=ConfirmSubscription&TopicArn=arn:aws:sns:us-west-2:123456789012:MyTopic&Token=2336412f37fb687f5d51e6e241d09c805a5a57b30d712f794cc5f6a988666d92768dd60a747ba6f3beb71854e285d6ad02428b09ceece29417f1f02d609c582afbacc99c583a916b9981dd2728f4ae6fdb82efd087cc3b7849e05798d2d2785c03b0879594eeac82c01f235d0e717736",
  "Timestamp" : "2012-04-26T20:45:04.751Z",
  "SignatureVersion" : "1",
  "Signature" : "EXAMPLEpH+DcEwjAPg8O9mY8dReBSwksfg2S7WKQcikcNKWLQjwu6A4VbeS0QHVCkhRS7fUQvi2egU3N858fiTDN6bkkOxYDVrY0Ad8L10Hs3zH81mtnPk5uvvolIC1CXGu43obcgFxeL3khZl8IKvO61GWB6jI9b5+gLPoBc1Q=",
  "SigningCertURL" : "https://sns.us-west-2.amazonaws.com/SimpleNotificationService-f3ecfb7224c7233fe7bb5f59f96de52f.pem"
  }
```

## SWF


## Lambda
* All calls made to AWS Lambda must complete execution within 300 seconds. The default timeout is 3 seconds, but you can set the timeout to any value between 1 and 300 seconds.
* In the AWS lambda resource mode, you choose the amount of memory you want for your function, and all allocated proportional CPU power and other resource. You can set your memory in 64MB increments from 128MB to 3G.
## Beanstalk

## CloudFormation
![Format](images/readme/CloudFormation1.PNG)

```
"Parameters" : {
  "ParameterLogicalID" : {
    "Type" : "DataType",
    "ParameterProperty" : "value"
  }
}
```
```
"Conditions" : {
  "Logical ID" : {Intrinsic function}
}
```
```
"Resources" : {
    "Logical ID" : {
        "Type" : "Resource type",
        "Properties" : {
            Set of properties
        }
    }
}
```
Examples

```

```

Function

```
{ "Fn::Base64" : valueToEncode }

{ "Fn::GetAtt" : [ "logicalNameOfResource", "attributeName" ] }
e.g.: "Fn::GetAtt" : [ "myELB" , "DNSName" ]
    
{ "Fn::FindInMap" : [ "MapName", "TopLevelKey", "SecondLevelKey"] }
e.g.: "Fn::FindInMap" : [ "RegionMap", { "Ref" : "AWS::Region" }, "32"]

{ "Fn::Join" : [ "delimiter", [ comma-delimited list of values ] ] }
e.g.: "Fn::Join" : [ ":", [ "a", "b", "c" ] ]

{ "Ref" : "logicalName" }
e.g.: "InstanceId" : { "Ref" : "MyEC2Instance" }

Condition Functions
Fn::And
Fn::Equals
Fn::If
Fn::Not
Fn::Or

"Fn::If": [condition_name, value_if_true, value_if_false]
"SecurityGroups" : [{
  "Fn::If" : [
    "CreateNewSecurityGroup",
    {"Ref" : "NewSecurityGroup"},
    {"Ref" : "ExistingSecurityGroup"}
  ]
}]
```

## Route53

## VPC

# AWS Document

* https://docs.aws.amazon.com/cli/latest/
* https://aws.amazon.com/whitepapers/

## APIs
* https://docs.aws.amazon.com/IAM/latest/APIReference/Welcome.html
* https://docs.aws.amazon.com/AWSEC2/latest/APIReference/Welcome.html
* https://docs.aws.amazon.com/AmazonS3/latest/API/Welcome.html
* https://docs.aws.amazon.com/amazondynamodb/latest/APIReference/Welcome.html
* https://docs.aws.amazon.com/amazon-mq/latest/api-reference/welcome.html
* https://docs.aws.amazon.com/sns/latest/api/Welcome.html
* https://docs.aws.amazon.com/amazonswf/latest/apireference/Welcome.html

```
Add... 
Attache...
Create...
Update...
Remove...
Delete...
Get...
Set...
List...s
Describe...
```

* API can be used as action in the HTTP GET

```
https://iam.amazonaws.com/?Action=AddClientIDToOpenIDConnectProvider
&ClientID=my-application-ID
&OpenIDConnectProviderArn=arn:aws:iam::123456789012:oidc-provider/server.example.com
&Version=2010-05-08
&AUTHPARAMS
```

* AWS SDK support java, .Net, C++, Python, Ruby, Go, Javascript, PHP and Node.js

## FAQs
* https://aws.amazon.com/ec2/faqs/
* https://aws.amazon.com/lambda/faqs/
* https://aws.amazon.com/s3/faqs/
* https://aws.amazon.com/dynamodb/faqs/

# Number Related
https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html

## Resource Limit
| Service  |Resource   | Limit | 
| :--- | :-------------------------- | :------------------ |
| EC2  | Instance | 20 (contact amazon) |
| EC2  | Elastic IP Address | 5 |
| S3  | Single put| 5G |
| S3  | Object size | 5T |
| S3  | Buckets | 100 per account |
| DynamoDB  | Smallest Reserved Capacity | 100 |
| DynamoDB  | Tags per Table | 50 |
| DynamoDB  | table partition | max 3000 read CU or 1000 WU |
| DynamoDB | Item collection  |10GB |
| DynamoDB | BatchGetItem | max 100 items, < 16MB| 
| Beanstalk  | Applications | 75 |
| Beanstalk  | Applications Version | 1000 |
| Beanstalk  | Environments | 200 |
| CloudFormation  | template | unlimited |
| CloudFormation  | stacks  | 200 |
| CloudFormation  | parameters and oupts in template | 60 |
| SQS  | Message Size | 256KB |
| SQS  | Standard queue TPS per API Action| unlimited |
| SQS  | FIFO queue TPS per API Action| 300 |
| SQS  | Standard queue inflight message| 120,000  |
| SQS  | FIFO queue Tinflight message| 20,000 |
| SNS | SMS message | 140 bytes | 
| SNS | Subscription per topic | 10million |  
| SNS | topic per account | 100,000 |   
| SWF | Domain | 100 |  
| SWF | Activity tasks in one decision | 100 |  
| SWF | Maximum workflow and actiivty tasks | 10,000 |  
| VPC | Internet Gateway | one per VPC|  
| VPC | NACL | one per subnet |  
| VPC | Route Table | one per subnet |  
| VPC | Available Zone | one per subnet |  

## Limit and default value
| Service  | Item   | Range | Default |
| :-------- | :-------| :-----  |:----- |
| IAM | Default expiration for the temporary credential | 15 minutes ~ 36 hours |12 hours |
| IAM | AssumeRoleAPIs | 15 minutes ~ 12 hours | |
| DynamoDB | min length of partition key | 1byte ~ 2048byte |  |
| DynamoDB | min length of sort key | 1byte ~ 1024byte |  |
| SQS | Visibility Timeout | 0 ~ 12 hours| 30s |
| SQS | Long Poll Timeout | 0 ~ 20s |  |
| SQS | retention period | 1minute ~ 14 days | 4 days |
| SNS | subscription request valid |  | 3 days |
| SWF | maximum workflow |  | 1 year |


# Related knowledge
## IAM
* SAML: [Intro to SAML: What, How and Why](https://www.youtube.com/watch?v=0fmNoqz6Urw)

## DynamoDB




# Read later
* https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Programming.Errors.html


# Todo
* cli summary
* read faq
* ssh key for IAM
* SNS mobile subscrition steps
