# Linux Academcy
## Collection
* Q1. Kinesis Streams can be transformed and processed using Lambda.

Correct answer
True

Explanation
When you enable Firehose data transformation, Firehose buffers incoming data up to 3 MB or the buffering size you specified for the delivery stream, whichever is smaller. Firehose then invokes the specified Lambda function with each buffered batch asynchronously. The transformed data is sent from Lambda to Firehose for buffering. Transformed data is delivered to the destination when the specified buffering size or buffering interval is reached, whichever happens first.

Further Reading
http://docs.aws.amazon.com/firehose/latest/dev/data-transformation.html

* Q2. AWS Snowball is a virtual appliance.

Correct answer
False

Explanation
Snowball is a physical appliance.



## Aanlysis
* Q1. Kinesis Analytics expected latency is in the minutes.

Correct answer
False

Explanation
Sub 1 second.

* Q2. The size of a row in an in-application stream is limited to ____ KB.

Correct answer
512

Explanation
The size of a row in an in-application stream is limited to 512 KB.

Further Reading
http://docs.aws.amazon.com/kinesisanalytics/latest/dev/limits.html

* Q3. Select the true statements from below.
Correct answer
The multi-node configuration requires a leader node that manages client connections and receives queries and two compute nodes that store data and perform queries and computations.

Explanation
The single node configuration enables you to get started with Amazon Redshift quickly and cost-effectively and scale up to a multi-node configuration as your needs grow. The multi-node configuration requires a leader node that manages client connections and receives queries, and two compute nodes that store data and perform queries and computations. The leader node is provisioned for you automatically and you are not charged for it.

Further Reading
https://aws.amazon.com/redshift/faqs/

* Q4. What is the maximum nodes a Amazon Redshift data warehouse cluster can contain?

Correct answer
128

Explanation
An Amazon Redshift data warehouse cluster can contain from 1-128 compute nodes, depending on the node type.

Further Reading
https://aws.amazon.com/redshift/faqs/

* Q5. What is the easiest way to put data into Elasticsearch?


Correct answer
S3 Import

Explanation
You can use Lambda to send data to your Amazon ES domain from Amazon S3. New data that arrives in an S3 bucket triggers an event notification to Lambda, which then runs your custom code to perform the indexing. This method of streaming data is extremely flexible. You can index object metadata, or if the object is plaintext, parse and index some elements of the object body. This section includes some unsophisticated Python sample code that uses regular expressions to parse a log file and index the matches.

Further Reading
https://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-aws-integrations.html#es-aws-integrations-fh

* Q6. Elasticsearch automated snapshots are kept for 14 days.

Correct answer
True

Explanation
Amazon Elasticsearch Service will retain the last 14 days worth of automated daily snapshots.

Further Reading
https://aws.amazon.com/elasticsearch-service/faqs/

* Q7. What is SerDe?

Correct answer
Serializer/Deserializer, which are libraries that tell Hive how to interpret data formats

Explanation
SerDe stands for Serializer/Deserializer, which are libraries that tell Hive how to interpret data formats. Hive DLL statements require you to specify a SerDe, so that the system knows how to interpret the data that you’re pointing to. Amazon Athena uses SerDes to interpret the data read from Amazon S3.

* Q8. You can only have one concurrent query at a time with Athena.

Correct answer
False

Explanation
Currently, you can have 20 concurrent queries at one time per account.

Further Reading
http://docs.aws.amazon.com/athena/latest/ug/service-limits.html
Further Reading
https://aws.amazon.com/athena/faqs/

# A clound Guru
## Collection 

* Q1. For an unknown reason, data delivery from Kinesis Firehose to your Redshift cluster has failed. Kinesis Firehose retries the data delivery every 5 minutes for a maximum period for of 60 minutes; however, none of the retries deliver the data to Redshift. Kinesis Firehose skips the files and move onto the next batch of files in S3. How can you ensure that the undelivered data is eventually loaded into Redshift?

Skipped files are delivered to your S3 bucket as a manifest file in an errors folder. Run the COPY command manually to load the skipped files after you have determined why they failed to load.

* Q2. Your team has successfully migrated the corporate data warehouse to Redshift. So far, all the data coming into the ETL pipeline for the data warehouse has been from other corporate systems also running on AWS. However, after signing some new business deals with a 3rd party, they will be securely sending files directly to S3. The data in these files needs to be ingested into S3. Members of your team are debating the most efficient and best automated way to introduce this change into the ETL pipeline. Which of the following options would you suggest? (Choose 2)

Use Lambda (AWS Redshift Database Loader).

Use Data Pipeline.

* Q3. Which service does Kinesis Firehose not load streaming data into?

DynamoDB


Kinesis Firehose can capture, transform, and load streaming data into Amazon Kinesis Analytics, Amazon S3, Amazon Redshift, and Amazon Elasticsearch Service.


## Storage
* Q1. Which of the following attribute data types can be table or item keys? (Choose 3)

String, Number, and Binary data types (scalars) can be table or item keys. 

## Analysis

* Q1. You have a table in your Redshift cluster, and the data in this table changes infrequently. The table has fewer than 15 million rows and does not JOIN any other tables. Which distribution style would you select for this table?

Answer: ALL

* Q2. 
True or False: When you use the UNLOAD command in Redshift to write data to S3, it automatically creates files using Amazon S3 server-side encryption with AWS-managed encryption keys (SSE-S3).

Answer: True

## Security
* Q1. Which of the following mechanisms work together to encrypt data at rest on instance store volumes and EBS volumes? (Choose 2)

Open-source HDFS Encryption

LUKS

# AWS Sample Quiz
* Q1. A company needs to deploy a data lake solution for their data scientists in which all company data is accessible and stored in a central S3 bucket. The company segregates the data by business unit, using specific prefixes. Scientists can only access the data from their own business unit. The company needs a single sign-on identity and management solution based on Microsoft Active Directory (AD) to manage access to the data in Amazon S3.
Which method meets these requirements?
    * A) Use AWS IAM Federation functions and specify the associated role based on the users' groups in AD.
    * B) Create bucket policies that only allow access to the authorized prefixes based on the users' group name in Active Directory.
    * C) Deploy the AD Synchronization service to create AWS IAM users and groups based on AD information.
    * D) Use Amazon S3 API integration with AD to impersonate the users on access in a transparent manner.

A - Identity Federation allows organizations to associate temporary credentials to users authenticated through an external identity provider such as Microsoft Active Directory (AD). These temporary credentials are linked to AWS IAM roles that grant access to the S3 bucket. Option B does not work because bucket policies are linked to IAM principles and cannot recognize AD attributes. Option C does not work because AD Synchronization will not sync directly with AWS IAM, and custom synchronization would not result in Amazon S3 being able to see group information. D isn't possible because there is no feature to integrate Amazon S3 directly with external identity providers.

* Q2. An organization needs a data store to handle the following data types and access patterns:
Key-value access pattern
Complex SQL queries and transactions
Consistent reads
Fixed schema
Which data store should the organization choose?

    * A) Amazon S3
    * B) Amazon Kinesis
    * C) Amazon DynamoDB
    * D) Amazon RDS

D - Amazon RDS handles all these requirements, and although Amazon RDS is not typically thought of as optimized for key-value based access, a schema with a good primary key selection can provide this functionality. Amazon S3 provides no fixed schema and does not have consistent read after PUT support. Amazon Kinesis supports streaming data that is consistent as of a given sequence number but doesn't provide key/value access. Finally, although Amazon DynamoDB provides key/value access and consistent reads, it does not support SQL-based queries.

* Q3. A web application emits multiple types of events to Amazon Kinesis Streams for operational reporting. Critical events must be captured immediately before processing can continue, but informational events do not need to delay processing.
What is the most appropriate solution to record these different types of events?

    * A) Log all events using the Kinesis Producer Library.
    * B) Log critical events using the Kinesis Producer Library, and log informational events using the PutRecords API method.
    * C) Log critical events using the PutRecords API method, and log informational events using the Kinesis Producer Library.
    * D) Log all events using the PutRecords API method.

C – The core of this question is how to send event messages to Kinesis synchronously vs. asynchronously. The critical events must be sent synchronously, and the informational events can be sent asynchronously. **The Kinesis Producer Library (KPL) implements an asynchronous send function, so it can be used for the informational messages. PutRecords is a synchronous send function, so it must be used for the critical events.**

* Q4. An administrator decides to use the Amazon Machine Learning service to classify social media posts that mention your company into two categories: posts that require a response and posts that do not. The training dataset of 10,000 posts contains the details of each post, including the timestamp, author, and full text of the post. You are missing the target labels that are required for training. Which two options will create valid target label data?

    * A) Ask the social media handling team to review each post and provide the label.
    * B) Use the sentiment analysis NLP library to determine whether a post requires a response.
    * C) Use the Amazon Mechanical Turk web service to publish Human Intelligence Tasks that ask Turk workers to label the posts.
    * D) Using the a priori probability distribution of the two classes, use Monte-Carlo simulation to generate the labels.

A, C - You need accurate data to train the service and get accurate results from future data. The options described in B and D would end up training an ML model using the output from a different machine learning model and therefore would significantly increase the possible error rate. It is extremely important to have a very low error rate (if any!) in your training set, and therefore human-validated or assured labels are essential.


* Q5. A data engineer needs to collect data from multiple Amazon Redshift clusters within a business and consolidate the data into a single central data warehouse. Data must be encrypted at all times while at rest or in flight.
What is the most scalable way to build this data collection process?

    * A) Run an ETL process that connects to the source clusters using SSL to issue a SELECT query for new data, and then write to the target data warehouse using an INSERT command over another SSL secured connection.
    * B) Use AWS KMS data key to run an UNLOAD ENCRYPTED command that stores the data in an unencrypted S3 bucket; run a COPY command to move the data into the target cluster.
    * C) Run an UNLOAD command that stores the data in an S3 bucket encrypted with an AWS KMS data key; run a COPY command to move the data into the target cluster.
    * D) Connect to the source cluster over an SSL client connection, and write data records to Amazon Kinesis Firehose to load into your target data warehouse.

B - The most scalable solutions are the UNLOAD/COPY solutions because they will work in parallel, which eliminates A and D as answers. Option C is incorrect because the data would not be encrypted in flight, and you cannot encrypt an entire bucket with a KMS key. Option B meets the encryption requirements, the UNLOAD ENCRYPTED command automatically stores the data encrypted using-client side encryption and uses HTTPS to encrypt the data during the transfer to S3.


* Q6. A company logs data from its application in large files and runs regular analytics of these logs to support internal reporting for three months after the logs are generated. After three months, the logs are infrequently accessed for up to a year. The company also has a regulatory control requirement to store application logs for seven years.
Which course of action should the company take to achieve these requirements in the most cost-efficient way?

    * A) Store the files in S3 Glacier with a Deny Delete vault lock policy for archives less than seven years old and a vault access policy that restricts read access to the analytics IAM group and write access to the log writer service role.
    * B) Store the files in S3 Standard with a lifecycle policy to transition the storage class to Standard - IA after three months. After a year, transition the files to Glacier and add a Deny Delete vault lock policy for archives less than seven years old.
    * C) Store the files in S3 Standard with lifecycle policies to transition the storage class to Standard – IA after three months and delete them after a year. Simultaneously store the files in Amazon Glacier with a Deny Delete vault lock policy for archives less than seven years old.
    * D) Store the files in S3 Standard with a lifecycle policy to remove them after a year. Simultaneously store the files in Amazon S3 Glacier with a Deny Delete vault lock policy for archives less than seven years old.

C – There are two aspects to this question: setting up a lifecycle policy to ensure that objects are stored in the most cost-effective storage, and ensuring that the regulatory control is met. The lifecycle policy will store the objects on S3 Standard during the three months of active use, and then move the objects to S3 Standard – IA when access will be infrequent. That narrows the possible answer set to B and C. **The Deny Delete vault lock policy will ensure that the regulatory policy is met, but that policy must be applied over the entire lifecycle of the object, not just after it is moved to Glacier after the first year. Option C has the Deny Delete vault lock applied over the entire lifecycle of the object and is the right answer**.

# Whizlab
## Collection

## Storage

## Processing

## Analysis
| Machine Learning  | score    | Note|
| :--- | :-------------------------- | :------------------ |
| Binary  | AUC (Area-Under-the-Curve) |  | 
| Multi-Class  |  F1-measure  | 0-1  |
| Regression  |  |  | 

AWS machine learning read csv from s3. or copy data from Redshift/RDS to s3 first. 
## Visualization
Quick sign KPI is used to compare single metrir. Multiple breadown can use tree map to compare values.

## Security
### Encrpytion
* S3:
    * Verify s3 copy object use ETag: https://docs.aws.amazon.com/AmazonS3/latest/API/RESTCommonResponseHeaders.html
    * Amazon S3 Encryption Options 

| Options  | Athena   | Redshift Unload| EMR|
| :--- | :-------------------------- | :------------------ |:------------------ |
| SSE-S3  | X | X |X |
| SSE-KMS  | X  |  X  |X |
| SSE-C  |  |  | |
| CSE-KMS  | X | |X |
| CSE-CMK  |  |  X |	X |
* DynamoDB: When creating a new table, you can choose one of the following customer master keys (CMK) to encrypt your table:
    * AWS owned CMK - Default encryption type. The key is owned by DynamoDB (no additional charge).
    * AWS managed CMK - The key is stored in your account and is managed by AWS KMS (AWS KMS charges apply).

When you access an encrypted table, DynamoDB decrypts the table data transparently. 
* Redshift
    * When you launch an Amazon Redshift cluster, you can choose to encrypt it with a master key from the AWS Key Management Service (AWS KMS). AWS KMS keys are specific to a region. If you want to enable cross-region snapshot copy for an AWS KMS-encrypted cluster, you must configure a snapshot copy grant for a master key in the destination region so that Amazon Redshift can perform encryption operations in the destination region. 
    * You can enable encryption when you launch your cluster, or you can modify an unencrypted cluster to use AWS Key Management Service (AWS KMS) encryption. To do so, you can use either an AWS-managed key or a customer-managed key (CMK). When you modify your cluster to enable KMS encryption, Amazon Redshift automatically migrates your data to a new encrypted cluster. Snapshots created from the encrypted cluster are also encrypted. 
* Kinesis Data Firehose: If you have sensitive data, you can enable server-side data encryption when you use Amazon Kinesis Data Firehose. How you do this depends on the source of your data.
    * **Server-Side Encryption with Kinesis Data Streams as the Data Source**: When you configure a Kinesis data stream as the data source of a Kinesis Data Firehose delivery stream, Kinesis Data Firehose no longer stores the data at rest. Instead, the data is stored in the data stream. When you send data from your data producers to your data stream, Kinesis Data Streams encrypts your data using an AWS Key Management Service (AWS KMS) key before storing the data at rest. When your Kinesis Data Firehose delivery stream reads the data from your data stream, Kinesis Data Streams first decrypts the data and then sends it to Kinesis Data Firehose.
    * **Server-Side Encryption with Direct PUT or Other Data Sources**: If you send data to your delivery stream using PutRecord or PutRecordBatch, or if you send the data using AWS IoT, Amazon CloudWatch Logs, or CloudWatch Events, you can turn on server-side encryption by using the StartDeliveryStreamEncryption operation.To stop server-side-encryption, use the StopDeliveryStreamEncryption operation.
* VPN involved encryption and will be more secure for transferring the encryption keys


