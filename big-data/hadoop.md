# Tutoirals
## HDP
* https://hortonworks.com/tutorial/hadoop-tutorial-getting-started-with-hdp/
> Apache Hadoop is an open source framework for `distributed storage` and `processing` of large sets of data on  `commodity hardware`.
* 

# Command
## Different commands 
* `hadoop fs {args}`: FS relates to a generic file system which can point to any file systems like local, HDFS etc. So this can be used when you are dealing with different file systems such as Local FS, (S)FTP, S3, and others. https://hadoop.apache.org/docs/current/hadoop-project-dist/hadoop-common/FileSystemShell.html
* ~~`hadoop dfs {args}`: dfs is very specific to HDFS. would work for operation relates to HDFS. This has been deprecated and we should use hdfs dfs instead.~~
* `hdfs dfs {args}`
https://hadoop.apache.org/docs/r2.7.1/hadoop-project-dist/hadoop-hdfs/HDFSCommands.html


# Components
## HDFS
Q1. What are SUCCESS and part-00000 files in hadoop
* On the successful completion of a job, the MapReduce runtime creates a _SUCCESS file in the output directory. This may be useful for applications that need to see if a result set is complete just by inspecting HDFS. (MAPREDUCE-947)
* The output files are by default named part-yyyyy where: yyyyy is the mapper or reducer task number (zero based) So a job which has 32 reducers will have files named part-r-00000 to part-r-00031, one for each reducer task.
