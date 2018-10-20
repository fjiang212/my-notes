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
