# Overview
* Architecture
![architecture](images/architecture/architecture.png)


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
## Redshift
* Redshift

![Redshift](images/architecture/redshift.png)

* Redshift Spectrum
![Redshift Spectrum](images/architecture/redshift-spectrum.png)


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
