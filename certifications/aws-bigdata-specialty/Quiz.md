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

## Storage

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



