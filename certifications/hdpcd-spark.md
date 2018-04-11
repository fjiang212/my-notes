# HDPCD: SPARK EXAM
* Exam Information
    * https://hortonworks.com/services/training/certification/hdp-certified-spark-developer/
    * https://hortonworks.com/services/training/certification/exam-objectives/#hdpcdspark
* Available link in the exam
    * http://spark.apache.org/docs/1.6.0/api/scala/index.html#org.apache.spark.package
    

## Core Spark
### Write a Spark Core application in Python or Scala
### Initialize a Spark application
### Run a Spark job on YARN
### Create an RDD
### Create an RDD from a file or directory in HDFS
Q1. How to load local file in sc.textFile, instead of HDFS
>Try explicitly specify sc.textFile("file:///path to the file/"). The error occurs when Hadoop environment is set.
>SparkContext.textFile internally calls org.apache.hadoop.mapred.FileInputFormat.getSplits, which in turn uses org.apache.hadoop.fs.getDefaultUri if schema is absent. This method reads "fs.defaultFS" parameter of Hadoop conf. If you set HADOOP_CONF_DIR environment variable, the parameter is usually set as "hdfs://..."; otherwise "file://".
>HDP `core-site.xml` set fs.defaultFS as `hdfs://sandbox.hortonworks.com:8020`

> def textFile(path: String, minPartitions: Int = defaultMinPartitions): RDD[String]
> Read a text file from HDFS, a local file system (available on all nodes), or any Hadoop-supported file system URI, and return it as an RDD of Strings(`array of line string`).

### Persist an RDD in memory or on disk
### Perform Spark transformations on an RDD
### Perform Spark actions on an RDD
### Create and use broadcast variables and accumulators
### Configure Spark properties

## Spark SQL

### Create Spark DataFrames from an existing RDD
### Perform operations on a DataFrame
### Write a Spark SQL application
### Use Hive with ORC from Spark SQL
### Write a Spark SQL application that reads and writes data from Hive tables


# Reference
* https://spark.apache.org/docs/latest/index.html 
* https://spark.apache.org/docs/latest/rdd-programming-guide.html

# Tasks
## Tutorial
- [ ] https://hortonworks.com/tutorial/hands-on-tour-of-apache-spark-in-5-minutes/

## Practice Exam
- [ ] https://2xbbhjxc6wk3v21p62t8n4d4-wpengine.netdna-ssl.com/wp-content/uploads/2015/02/HDPCD-PracticeExamGuide1.pdf

# Experience
* Experience 1
```
I have appeared today for my HDP-spark exam which lasted for 2 hours having 7 questions in total.
Points experienced today :
1.Please go through all the 7 questions first, Prioritize the questions based on your comfort level.
2.Expect the typical Cent-OS cluster behavior such as Ctrl+U , Ctrl+L won’t work in HDP-cluster.
3.No select pattern copy paste as we are able to do in our normal unix box.
4.Cluster is very slow, Please go with recommended bandwidth > 20 MBPS.
5.PSI support may take long time in solving environment issues like exam not getting delivered, DNS configuration at your browser.Please be ready for that.
6.As it’s a time constraint exam, Please don’t waste time on any ques more than 15 mins..
7.Concentrate more on string parsing , input parsing .Remember guys there is no time to think there.We won’t be able to complete 5 ques then.

Personal experience :
People said at many places we need to solve 4/7 ,its actually 5/7 we need to solve. Try to have the exam on desktop machine rather taking on laptop with descent monitor screen.Don’t compromise on bandwidth.
So Best Of luck guys....practice hard before an attempt.
```
* Experience 2

```
The current sandbox is HDP 2.5. Is this the version used in the exam?
HDP 2.5 comes with Spark 1.6 and 2.0. Can I choose which version I would like to use to solve the tasks? (2.0 supports writing and reading of csv files out of the box.)
Do I only have to use the Spark shell? If yes, why is there the exam objective "Initialize a Spark application"? Since using the Spark shell I do not have to do that manually. Further more there is "Run a Spark job on YARN". How should this be tested?
Do I have something like Ambari to look at Hive tables or the files in the HDFS?
Is there Zeppelin and can I use it?
Can I change the keyboard layout?

```
```
I had my exam three days ago. Let me answer my own question.

I do not know which HDP version it was.
The default version running spark-shell` in the terminal was Spark 1.6. I did not try to change it.
Yes, I was solving the tasks with Scala in the Spark Shell. However you have to save all you commands in the provided text files. It was not necessary to build a JAR manually to submit it. But there could be a task to submit a provided JAR to YARN.
I do not know. You can use hadoop fs commands in the terminal to browse the HDFS.
I do not think so.
You do not have to. Since the VM is running in your browser it automatically uses your local one.
Further information:

I think there were some links on the desktop to the documentation. But I did no use it.
You do not have to write CSV files with a header. Read carefully, the delimiter do not have to be the same in all tasks.
The general question pattern is: read this from here, do something with it, write the results to here.
Because only the output counts you have to read the tasks carefully (ordering of columns, sorting of the data, delimiter in CSV files, ...)
It is up to you how to solve the tasks. You can use RDD or SparkSQL API.
The exam is not really difficult if you work through the exam objectives
```
* Experience 3
```
couple notes on the exam
1. know RDD and dataframe api well. Go through all the docs in the test web page.
2. know how to import and export RDD/dataframe from/to csv files.
3. there is no limit on how you finish the task, so choose the technical you are most familiar with either the API or Spark SQL
4. test environment is quite slow in response, so be patient with it and leave enough time for tasks.
```

* spark environment
```
There is no IDE available on the Spark exam. You can use pyspark or spark-shell to execute your code.
You do NOT have access to google or the internet. You DO have access to the Spark doc pages, the Python and Scala doc pages, and the Hortonworks documentation as well.
There is currently no practice exam for the Spark exam. If you need experience writing Spark applications on HDP using Python or Scala, I recommend downloading the Sandbox and working through the Hortonworks Spark tutorials.
```
