# Chapter 1: Introduction
## Tools 
- [ ] https://www.aginity.com/main/workbench-for-amazon-redshift/
- [ ] https://docs.aws.amazon.com/redshift/latest/mgmt/connecting-using-workbench.html
- [ ] Cost: https://help.acloud.guru/hc/en-us/articles/115004457893
- [ ] https://github.com/sko71/aws-bigdata-specialty
- [ ] https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AccessingInstancesLinux.html

## Generating a Dataset
- [ ] http://www.tpc.org/tpch/

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
- [ ] https://github.com/awslabs/amazon-kinesis-producer
- [ ] https://github.com/awslabs/amazon-kinesis-agent
- [ ] https://github.com/awslabs/amazon-kinesis-client
- [ ] https://aws.amazon.com/blogs/big-data/implementing-efficient-and-reliable-producers-with-the-amazon-kinesis-producer-library/
- [ ] https://github.com/awslabs/amazon-kinesis-connectors
- [ ] https://aws.amazon.com/blogs/compute/amazon-kinesis-firehose-data-transformation-with-aws-lambda/
- [ ] https://d0.awsstatic.com/whitepapers/core-tenets-of-iot1.pdf
- [ ] https://github.com/aws/aws-iot-device-sdk-python


# Chapter 3: Storage
- [ ] https://aws.amazon.com/blogs/big-data/scaling-writes-on-amazon-dynamodb-tables-with-global-secondary-indexes/
- [ ] http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/SecondaryIndexes.html
- [ ] http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Streams.CrossRegionRepl.html

# Chapter 4: Processing
## EMR Introduction
- [ ] https://github.com/sko71/aws-bigdata-specialty

## EMR Operations
- [ ] https://d0.awsstatic.com/whitepapers/aws-amazon-emr-best-practices.pdf
- [ ] http://docs.aws.amazon.com/emr/latest/ManagementGuide/emr-web-interfaces.html

## Using Hue with EMR
- [ ] http://docs.aws.amazon.com/emr/latest/ReleaseGuide/hue-ldap.html

## HBase on EMR
- [ ] https://d1.awsstatic.com/whitepapers/AWS_Comparing_the_Use_of_DynamoDB_and_HBase_for_NoSQL.pdf
- [ ] https://aws.amazon.com/blogs/big-data/combine-nosql-and-massively-parallel-analytics-using-apache-hbase-and-apache-hive-on-amazon-emr/
- [ ] http://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-hbase-access-hive.html

## Spark on EMR
- [ ] https://aws.amazon.com/blogs/big-data/analyze-your-data-on-amazon-dynamodb-with-apache-spark/
- [ ] https://aws.amazon.com/blogs/big-data/analyze-realtime-data-from-amazon-kinesis-streams-using-zeppelin-and-spark-streaming/
- [ ] https://aws.amazon.com/blogs/big-data/optimize-spark-streaming-to-efficiently-process-amazon-kinesis-streams/
- [ ] https://aws.amazon.com/blogs/big-data/powering-amazon-redshift-analytics-with-apache-spark-and-amazon-machine-learning/
- [ ] https://aws.amazon.com/blogs/big-data/using-spark-sql-for-etl/
- [ ] https://github.com/awslabs/emr-dynamodb-connector
- [ ] https://github.com/databricks/spark-redshift

## Lambda in the AWS Big Data Ecosystem
- [ ] https://aws.amazon.com/blogs/compute/implementing-a-serverless-aws-iot-backend-with-aws-lambda-and-amazon-dynamodb/
- [ ] https://aws.amazon.com/blogs/database/indexing-metadata-in-amazon-elasticsearch-service-using-aws-lambda-and-python/


# Chapter 5: Analysis
## Redshift Architecture
- [ ] https://d0.awsstatic.com/whitepapers/enterprise-data-warehousing-on-aws.pdf

## Redshift Table Design
- [ ] https://aws.amazon.com/blogs/big-data/amazon-redshift-engineerings-advanced-table-design-playbook-preamble-prerequisites-and-prioritization/
- [ ] https://aws.amazon.com/blogs/big-data/optimizing-for-star-schemas-and-interleaved-sorting-on-amazon-redshift/

## Redshift Maintenance and Operations 
- [ ] http://docs.aws.amazon.com/redshift/latest/mgmt/working-with-clusters.html
- [ ] https://github.com/awslabs/amazon-redshift-utils/tree/master/src/AnalyzeVacuumUtility
- [ ] http://docs.aws.amazon.com/redshift/latest/dg/performing-a-deep-copy.html
- [ ] https://github.com/awslabs/amazon-redshift-utils/tree/master/src/SnapshotManager
- [ ] https://github.com/awslabs/amazon-redshift-monitoring
- [ ] https://github.com/sko71/aws-bigdata-specialty/tree/master/Domain%204
- [ ] http://docs.aws.amazon.com/redshift/latest/dg/c-query-performance.html

## Machine Learning
- [ ] https://aws.amazon.com/blogs/big-data/building-a-multi-class-ml-model-with-amazon-machine-learning/
- [ ] https://aws.amazon.com/blogs/big-data/building-a-binary-classification-model-with-amazon-machine-learning-and-amazon-redshift/
- [ ] https://aws.amazon.com/blogs/big-data/building-a-numeric-regression-model-with-amazon-machine-learning/
- [ ] https://github.com/sko71/aws-bigdata-specialty/tree/master/Domain%204

## Elasticsearch
- [ ] https://aws.amazon.com/blogs/security/how-to-visualize-and-refine-your-networks-security-by-adding-security-group-ids-to-your-vpc-flow-logs/#more-3559
- [ ] http://docs.aws.amazon.com/elasticsearch-service/latest/developerguide/es-managedomains.html

## RStudio
- [ ] https://aws.amazon.com/blogs/big-data/connecting-r-with-amazon-redshift/
- [ ] https://aws.amazon.com/blogs/big-data/statistical-analysis-with-open-source-r-and-rstudio-on-amazon-emr/
- [ ] https://aws.amazon.com/blogs/big-data/crunching-statistics-at-scale-with-sparkr-on-amazon-emr/
- [ ] https://aws.amazon.com/blogs/big-data/running-r-on-aws/
- [ ] https://media.acloud.guru/aws-certified-big-data-specialty/resource/e576d80a-0495-4a08-fa97-b539da26fd79_0e6e3d38-d599-2d48-1736-9e658b8c5327/aws-certified-big-data-specialty-cdf30666-712b-4622-b610-da45a318a564.txt?Expires=1542049143&Signature=Zyhso9E0ENsnOWMjFEW/G9AdJ5kcCFH8z9T9+riZYlST0mEhsOXfs4m7STlg9UJhx+nVQ61X+2jq2A2bcJmIwb2OYIZeRoheEN5t9QTJUSI/2ea33QU/zwBAvxC908whzqWSp/F2i+PFKyIAaIXAD11+KsV3cpx28oOKh4vuJ2dmvHcckY2wUfEAgtdySpaHJwpbamcEfuzaJ9F7CShxvFgaJFLd3K6QEEuX8MscXdwUTy8uaHMggCM4qtEadqDISKILpdADze7sqi/JsnZYomtbOZjSHgzxB7IZJUPVLfo0FOAMbQWjGxEbfFmyMGlbAXuEF0OcU5FEFrJLU9qqiQ==&Key-Pair-Id=APKAISLU6JPYU7SF6EUA

# Chapter 6: Visualization
- [ ] https://aws.amazon.com/blogs/big-data/analyze-realtime-data-from-amazon-kinesis-streams-using-zeppelin-and-spark-streaming/
- [ ] https://aws.amazon.com/blogs/big-data/running-jupyter-notebook-and-jupyterhub-on-amazon-emr/

# Chapter 7: Security
- [ ] https://hadoop.apache.org/docs/r2.7.1/hadoop-mapreduce-client/hadoop-mapreduce-client-core/EncryptedShuffle.html
- [ ] http://docs.aws.amazon.com/redshift/latest/mgmt/working-with-db-encryption.html
