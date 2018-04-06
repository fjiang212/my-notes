# Command
## Different commands 
* `hadoop fs {args}`: FS relates to a generic file system which can point to any file systems like local, HDFS etc. So this can be used when you are dealing with different file systems such as Local FS, (S)FTP, S3, and others

https://hadoop.apache.org/docs/current/hadoop-project-dist/hadoop-common/FileSystemShell.html

* `hadoop dfs {args}`: dfs is very specific to HDFS. would work for operation relates to HDFS. This has been deprecated and we should use hdfs dfs instead.
* `hdfs dfs {args}`