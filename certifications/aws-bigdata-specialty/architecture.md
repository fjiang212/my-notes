# Overview
* Architecture
![architecture](images/architecture/architecture.png)

* Database
![Database](images/architecture/database.png)

# Collection
## Kinesis
* Kinesis Architecture
![kinesis architecture](images/architecture/kinesis_architecture.png)

* Kinesis Stream
![kinesis stream](images/architecture/kinesis_stream.png)

* Kinesis KPL
![kinesis kpl](images/architecture/kinesis_kpl.png)

* Kinesis Firehose

![kinesis_firehose](images/architecture/kinesis_firehose.png)


## IOT
* IOT Components
![iot_components](images/architecture/iot_components.png)

# Storage
## DyanmoDB


# Processing

## HBase
* HBase vs DynamoDB
![HBase vs DynamoDB ](images/architecture/hbase_dynamodb.png)

* HBase vs Redshift
![HBase vs Redshift ](images/architecture/hbase_redshift.png)

## Mics
* Compression
![Compression](images/architecture/compression.png)

* File Format
![ File Format](images/architecture/format.png)
# Analysis
## [AWS Glue](https://docs.aws.amazon.com/glue/latest/dg/what-is-glue.html)
AWS Glue is a fully managed ETL (extract, transform, and load) service that can categorize your data,
clean it, enrich it, and move it reliably between various data stores. AWS Glue crawlers automatically
infer database and table schema from your source data, storing the associated metadata in the AWS Glue
Data Catalog. When you create a table in Athena, you can choose to create it using an AWS Glue crawler

![alt text](images/architecture/glue_architecture.png)


## Athena
Amazon Athena is an interactive query service that makes it easy to analyze data directly in Amazon Simple Storage Service (Amazon S3) using standard SQL


* Under the hood, Athena uses Presto to execute DML statements and Hive to execute the DDL statements that create and modify schema.
* Athena can only query the latest version of data on a versioned Amazon S3 bucket, and cannot query previous versions of the data.
* By partitioning your data, you can restrict the amount of data scanned by each query, thus improving  performance and reducing cost. Athena leverages Hive for partitioning data. You can partition your data by any key.
* A results file stored automatically in a CSV format (*.csv), and An Athena metadata file (*.csv.metadata).



![Redshift Spectrum](images/architecture/athena_redshift_spectrum.png)



## Cloud Search
* he latest version of Amazon CloudSearch has been modified to use Apache Solr as the underlying text search engine.

## Redshift
* Redshift

![Redshift](images/architecture/redshift.png)

* Redshift Spectrum
![Redshift Spectrum](images/architecture/redshift_spectrum.png)


# Visualization
* Quicksight

![Quicksight](images/architecture/quicksight.png)

# Security
## KMS
* KMS (AWS service integration, FIPS 140-2)
![KMS](images/architecture/kms.png)

## CloudHSM
* CloudHS (Less AWS service integration, Use Java Cryptography Extension(JCE), CNG.  FIPS 140-3)
![CloudHSM](images/architecture/cloudhsm.png)

## Services
* EMR encryption (LUCK: Linux Unified Key Setup, use KMS CMK to generate encrpytion data key then use this key to protect LUCK master key)

![EMR encryption](images/architecture/emr_encryption.png)
