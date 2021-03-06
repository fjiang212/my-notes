# Table of Contents
1. [HDPCD: SPARK EXAM](#hdpcd-spark-exam)
2. [Core Spark](#core-spark)
3. [Spark SQL](#spark-sql)
4. [Tasks](#tasks)
5. [Experience](#experience)

# HDPCD: SPARK EXAM
* Exam Information
    * https://hortonworks.com/services/training/certification/hdp-certified-spark-developer/
    * https://hortonworks.com/services/training/certification/exam-objectives/#hdpcdspark
    * https://www.whizlabs.com/blog/prepare-for-hdpcd-apache-spark-certification/
    
* Available link in the exam
    * http://spark.apache.org/docs/1.6.0/api/scala/index.html#org.apache.spark.package
* Other spark docuemnts
    * [ ] http://spark.apache.org/docs/1.6.0/
    * [X] http://spark.apache.org/docs/1.6.0/programming-guide.html
    * [ ] http://spark.apache.org/docs/1.6.0/sql-programming-guide.html
    * [X] http://spark.apache.org/docs/1.6.0/monitoring.html
* Scala Coding
    * [ ] http://spark.apache.org/docs/1.6.0/programming-guide.html#passing-functions-to-spark
    * [ ] https://docs.scala-lang.org/tutorials/FAQ/finding-symbols.html
* HPD Sanbox Links
    * Ambari: http://127.0.0.1:8080/#/login
    * Zeppelin: http://localhost:9995
    * SparkContext Spark-UI: http://localhost:4040/
    * Spark History Server: http://localhost:18080/ (/usr/hdp/current/spark-historyserver/sbin/start|stop-history-server.sh)

## Core Spark
### [X] Write a Spark Core application in Python or Scala
### [ ] Initialize a Spark application
* http://spark.apache.org/docs/1.6.0/configuration.html
### [ ] Run a Spark job on YARN
* http://spark.apache.org/docs/1.6.0/cluster-overview.html
* http://spark.apache.org/docs/1.6.0/submitting-applications.html
* http://spark.apache.org/docs/1.6.0/spark-standalone.html
* http://spark.apache.org/docs/1.6.0/running-on-yarn.html

### [X] Create an RDD
### [X] Create an RDD from a file or directory in HDFS
Q1. How to load local file in sc.textFile, instead of HDFS
* Try explicitly specify sc.textFile("file:///path to the file/"). The error occurs when Hadoop environment is set.
SparkContext.textFile internally calls org.apache.hadoop.mapred.FileInputFormat.getSplits, which in turn uses org.apache.hadoop.fs.getDefaultUri if schema is absent. This method reads "fs.defaultFS" parameter of Hadoop conf. If you set HADOOP_CONF_DIR environment variable, the parameter is usually set as "hdfs://..."; otherwise "file://".
* HDP `core-site.xml` set fs.defaultFS as `hdfs://sandbox.hortonworks.com:8020`
* `def textFile(path: String, minPartitions: Int = defaultMinPartitions): RDD[String]`
Read a text file from HDFS, a local file system (available on all nodes), or any Hadoop-supported file system URI, and return it as an RDD of Strings(`array of line string`).

### [X] Persist an RDD in memory or on disk
* RDD.persist()
* RDD.saveAsTextFile("path/to/file")
### [X] Perform Spark transformations on an RDD
Q1. What is the difference between `map` and `flatMap`?
* `map` transforms an RDD of length N into another RDD of length N.
* But `flatMap` (loosely speaking) transforms an RDD of length N into a collection of N collections(ex: through split), then flattens these into a single RDD of results.
* map(rec => xxx), flatMap(rec=>xxx): first element in the fuction is the record in the original RDD

Q2. What is the difference between `groupByKey`, `reduceByKey` , `aggregateByKey` and `reduce`?
* **groupByKey([numTasks])**: Transformation, When called on a dataset of (K, V) pairs, returns a dataset of `(K, Iterable<V>)` pairs.groupByKey can cause out of disk problems as data is sent over the network and collected on the reduce workers. 
```
val WordcountsWithReduce = wordPairsRDD.reduceByKey(_+_).collect()
val wordCountsWithGroup = wordPairsRDD.groupByKey().map(t = > t._1, t_2.sum)).collect()
```
![alt text](images/compare1.PNG)

**Notes: reduceByKey is doing map side combiner, groupByKey is not** 
* **reduceByKey(func, [numTasks])**: Transformation,When called on a dataset of (K, V) pairs, returns a dataset of (K, V) pairs where the values for each key are aggregated using the given reduce function func, which must be of type (V,V) => V. Data is combined at each partition , only one output for one key at each partition to send over network. reduceByKey required combining all your values into another value with the exact same type.
```
Examples
=========
k1, 1
k1, 2
K1, 3

# Do the caluation step by step, x and y are both data set
step 1: x=1, y=2 ==> x => 3(intermediate value)
step 2: x=3, y=3 ==> x => 6 (final value)

# if the value is tuple then
reduceByKey((x, y) => (x._1 + y._1, x._2 + y._2))
```
* **aggregateByKey(zeroValue)(seqOp, combOp, [numTasks])**: Transformation, When called on a dataset of (K, V) pairs, returns a dataset of (K, U) pairs where the values for each key are aggregated using the given combine functions and a neutral "zero" value. Allows an aggregated value type that is different than the input value type, while avoiding unnecessary allocations.
    * seqOp: Calculate the value on the local partition -> **Combiner Logic**
    * combOp: Combine the intrmediate value from seqOp -> **Reducer Logic**
```
(2013-11-11 00:00:00.0, 449.95)
key is date, value is float.

val revenuePerDay = orderJoinMap.aggregateByKey((0.0, 0))(
    (acc, value) => (acc._1 + value, acc._2 + 1),
    (total1, total2) => (total1._1 + total2._1, total1._2 + total2._2)
 )
```
**Note: Any xxxByKey fuction will take value as parameter**

* **reduce(func)**: Action,	Aggregate the elements of the dataset using a function func (which takes two arguments and returns one). The function should be commutative and associative so that it can be computed correctly in parallel.

### [X] Perform Spark actions on an RDD
Q1. How to print RDD element
* To print all elements on the driver, one can use the `collect()` method to first bring the RDD to the driver node thus: `rdd.collect().foreach(println)`. This can cause the driver to run out of memory, though, because collect() fetches the entire RDD to a single machine; 
* if you only need to print a few elements of the RDD, a safer approach is to use the `take()`: `rdd.take(100).foreach(println)`.
### [X] Create and use broadcast variables and accumulators
* Broadcast variables allow the programmer to keep a read-only variable cached on each machine rather than shipping a copy of it with tasks.
* Broadcast variables are created from a variable v by calling SparkContext.broadcast(v). The broadcast variable is a wrapper around v, and its value can be accessed by calling the value method
```
scala> val broadcastVar = sc.broadcast(Array(1, 2, 3))
broadcastVar: org.apache.spark.broadcast.Broadcast[Array[Int]] = Broadcast(0)

scala> broadcastVar.value
res0: Array[Int] = Array(1, 2, 3)
```
* Accumulators are variables that are only “added” to through an associative operation and can therefore be efficiently supported in parallel. 
* Only the driver program can read the accumulator’s value, using its value method.
```
scala> val accum = sc.accumulator(0, "My Accumulator")
accum: spark.Accumulator[Int] = 0

scala> sc.parallelize(Array(1, 2, 3, 4)).foreach(x => accum += x)
...
10/09/29 18:41:08 INFO SparkContext: Tasks finished in 0.317106 s

scala> accum.value
res2: Int = 10
```
### [ ] Configure Spark properties

## Spark SQL
### [ ] Create Spark DataFrames from an existing RDD
* default sqlContext in the spark-shell is HiveContext
* How to create DataFrame
   * Use sqlContext read json file, the return result is DF(sqlContext.read.json).
   * Use SparkContext to read text file, run map transformation to map to case class. Then call toDF() to convert RDD to DF.
### [ ] Perform operations on a DataFrame
* The results of SQL queries are DataFrames and support all the normal RDD operations.

### [ ] Write a Spark SQL application
### [ ] Use Hive with ORC from Spark SQL
### [ ] Write a Spark SQL application that reads and writes data from Hive tables

# Tasks
## Tutorial
- [X] https://hortonworks.com/tutorial/hands-on-tour-of-apache-spark-in-5-minutes/
- [X] https://hortonworks.com/tutorial/word-count-sparkr-repl-examples/
- [ ] https://hortonworks.com/tutorial/learning-the-ropes-of-the-hortonworks-sandbox/
- [X] https://databricks.com/blog/2016/07/14/a-tale-of-three-apache-spark-apis-rdds-dataframes-and-datasets.html
- [ ] https://github.com/CjTouzi/Learning-RSpark/blob/master/Zaharia%20M.%2C%20et%20al.%20Learning%20Spark%20(O'Reilly%2C%202015)(274s).pdf

## Practice Exam/Training
- [ ] https://2xbbhjxc6wk3v21p62t8n4d4-wpengine.netdna-ssl.com/wp-content/uploads/2015/02/HDPCD-PracticeExamGuide1.pdf
- [ ] https://www.whizlabs.com/spark-developer-certification/

## Exercises
- [ ] Read data from file and run differernt transformation and action

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

* Experience 4
```
Expert Tips for the Preparation of  HDPCD Spark Certification

Best practices to obtain the best performance.
Practice Spark core and Spark SQL problems as much as possible through spark-shell
If you are appearing for HDPCD Apache Spark certification exam as a Hadoop professional, you must have an understanding of Spark features and best practices. Furthermore, you should know how they are different from Hadoop MapReduce.
Practice chapter 1- 9 of “Learning Spark” book for all exercises on RDD
```
