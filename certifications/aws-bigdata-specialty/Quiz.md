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


