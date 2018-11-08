# Chapter 1: Introduction
## Tools 
* https://www.aginity.com/main/workbench-for-amazon-redshift/
* https://docs.aws.amazon.com/redshift/latest/mgmt/connecting-using-workbench.html
* Cost: https://help.acloud.guru/hc/en-us/articles/115004457893
* https://github.com/sko71/aws-bigdata-specialty
* https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AccessingInstancesLinux.html

## Generating a Dataset
* http://www.tpc.org/tpch/

```
//install software
sudo yum install git
sudo yum install gcc
sudo yum install make

git clone https://github.com/gregrahn/tpch-kit
cd tcpch-kit/dbgen
make OS=LINUX

//generate EMR Data 
cd $HOME
mkdir emrdata
export DSS_PATH=$HOME/emrdata
cd tcpch-kit/dbgen
./dbgen -v -T o -s 10

aws s3api create-bucket --bucket bigdatalabsk --region us-east-1
aws s3 cp $HOME/emrdata s3://bigdatalabsk/emrdata --recursive

//generate Redshift Data 
cd $HOME
mkdir redshiftdata
export DSS_PATH=$HOME/redshiftdata
cd tcpch-kit/dbgen
./dbgen -v -T o -s 40

cd $HOME/redshiftdata
wc -l orders.tbl
split -d -l 15000000 -a 4 orders.tbl orders.tbl.
wc -l lineitem.tbl
split -d -l 60000000 -a 4 lineitem.tbl lineitem.tbl.
rm orders.tbl
rm lineitem.tbl
aws s3 cp $HOME/redshiftdata s3://bigdatalabsk/redshiftdata --recursive
```


# Chapter 2: Collection
## Kinesis Streams Core Concepts
* https://github.com/awslabs/amazon-kinesis-producer
* https://github.com/awslabs/amazon-kinesis-agent
* https://github.com/awslabs/amazon-kinesis-client
* https://aws.amazon.com/blogs/big-data/implementing-efficient-and-reliable-producers-with-the-amazon-kinesis-producer-library/

# Chapter 3: Storage

# Chapter 4: Processing
## EMR Introduction
* https://github.com/sko71/aws-bigdata-specialty

## EMR Operations
* https://d0.awsstatic.com/whitepapers/aws-amazon-emr-best-practices.pdf
* http://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-web-interfaces.html

## Using Hue with EMR
* http://docs.aws.amazon.com/emr/latest/ReleaseGuide/hue-ldap.html

## HBase on EMR
* https://d1.awsstatic.com/whitepapers/AWS_Comparing_the_Use_of_DynamoDB_and_HBase_for_NoSQL.pdf
* https://aws.amazon.com/blogs/big-data/combine-nosql-and-massively-parallel-analytics-using-apache-hbase-and-apache-hive-on-amazon-emr/
* http://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-hbase-access-hive.html

## Spark on EMR
* https://aws.amazon.com/blogs/big-data/analyze-your-data-on-amazon-dynamodb-with-apache-spark/
* https://aws.amazon.com/blogs/big-data/analyze-realtime-data-from-amazon-kinesis-streams-using-zeppelin-and-spark-streaming/
* https://aws.amazon.com/blogs/big-data/optimize-spark-streaming-to-efficiently-process-amazon-kinesis-streams/
* https://aws.amazon.com/blogs/big-data/powering-amazon-redshift-analytics-with-apache-spark-and-amazon-machine-learning/
* https://aws.amazon.com/blogs/big-data/using-spark-sql-for-etl/
* https://github.com/awslabs/emr-dynamodb-connector
* https://github.com/databricks/spark-redshift

## Lambda in the AWS Big Data Ecosystem
* https://aws.amazon.com/blogs/compute/implementing-a-serverless-aws-iot-backend-with-aws-lambda-and-amazon-dynamodb/
* https://aws.amazon.com/blogs/database/indexing-metadata-in-amazon-elasticsearch-service-using-aws-lambda-and-python/


# Chapter 4: Analysis
## Redshift Architecture
* https://d0.awsstatic.com/whitepapers/enterprise-data-warehousing-on-aws.pdf
