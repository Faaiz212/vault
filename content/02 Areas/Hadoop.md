---
aliases: 
id: 20240222200524
title: "Hadoop"
created: 2024-02-23T01:05:24.233Z
tags:
  - areas
  - type/litnote
---

# **Hadoop**

### How Does Hadoop Work?

The primary function of Hadoop is to process the data in an organised manner among the cluster of commodity software. The client should submit the data or program that needs to be processed. Hadoop HDFS stores the data. YARN, MapReduce divides the resources and assigns the tasks to the data. Let’s know the working of Hadoop in detail.         

The client input data is divided into 128 MB blocks by HDFS. Blocks are replicated according to the replication factor: various DataNodes house the unions and their duplicates.

The user can process the data once all blocks have been put on HDFS DataNodes.

The client sends Hadoop the MapReduce programme to process the data.

The user-submitted software was then scheduled by ResourceManager on particular cluster nodes.

The output is written back to the HDFS once processing has been completed by all nodes.

### Hadoop Distributed File System:

HDFS is known as the Hadoop distributed file system. It is the allocated File System. It is the primary data storage system in Hadoop Applications. It is the storage system of Hadoop that is spread all over the system. In HDFS, the data is once written on the server, and it will continuously be used many times according to the need.  The targets of HDFS are as follows.

The ability to recover from hardware failures in a timely manner

Access to Streaming Data

Accommodation of Large data sets

Portability

Hadoop Distributed File System has two nodes included in it. They are the Name Node and Data Node.

Name Node:

Name Node is the primary component of HDFS. Name Node maintains the file systems along with namespaces. Actual data can not be stored in the Name Node. The modified data, such as Metadata, block data etc., can be stored here.

Data Node:

Data Node follows the instructions given by the Name Node. Data Nodes are also known as ‘slave Nodes’. These nodes store the actual data provided by the client and simply follow the commands of the Name Node.

Job Tracker:

The primary function of the Job Tracker is resource management. Job Tracker determines the location of the data by communicating with the Name Node. Job Tracker also helps in finding the Task Tracker. It also tracks the MapReduce from Local Node to Slave Node. In Hadoop, there is only one instance of Job Trackers. Job Tracker monitors the individual Task Tracker and tracks the status. Job Tracker also helps in the execution of MapReduce in Hadoop.

Task Tracker:

Task Tracker is the slave daemon in the cluster which accepts all the instructions from the Job Tracker. Task Tracker runs on its process. The task trackers monitor all the tasks by capturing the input and output codes. The Task Tracker helps in mapping, shuffling and reducing the data operations. Task Tracker arranges different slots to perform different tasks. Task Tracker continuously updates the status of the Job Tracker. It also informs about the number of slots available in the cluster. In case the Task Tracker is unresponsive, then Job Tracker assigns the work to some other nodes.

### How Hadoop Improves on Traditional Databases

Understanding what is Hadoop requires further understanding on how it differs from traditional databases.

Hadoop uses the HDFS (Hadoop Data File System) to divide the massive data amounts into manageable smaller pieces, then saved on clusters of community servers. This offers scalability and economy.

Furthermore, Hadoop employs MapReduce to run parallel processings, which both stores and retrieves data faster than information residing on a traditional database. Traditional databases are great for handling predictable and constant workflows; otherwise, you need Hadoop’s power of scalable infrastructure.

### 5 Advantages of Hadoop for Big Data

Hadoop was created to deal with big data, so it’s hardly surprising that it offers so many benefits. The five main benefits are:

Speed. Hadoop’s concurrent processing, MapReduce model, and HDFS lets users run complex queries in just a few seconds.

Diversity. Hadoop’s HDFS can store different data formats, like structured, semi-structured, and unstructured.

Cost-Effective. Hadoop is an open-source data framework.

Resilient. Data stored in a node is replicated in other cluster nodes, ensuring fault tolerance.

Scalable. Since Hadoop functions in a distributed environment, you can easily add more servers.

### Conclusion

Hadoop is a widely used Big Data technology for storing, processing, and analyzing large datasets. After reading this article on what is Hadoop, you would have understood how Big Data evolved and the challenges it brought with it. You understood the [basics of Hadoop](https://www.simplilearn.com/learn-hadoop-spark-basics-skillup?source=GhPreviewCoursepages "basics of Hadoop"), its components, and how they work. Do you have any questions related to what is Hadoop article? If you have, then please put it in the comments section of this article. Our team will help you solve your queries.

If you want to grow your career in Big Data and Hadoop, then you can check [Big Data Engineer Course](https://www.simplilearn.com/pgp-data-engineering-certification-training-course?source=GhPreviewCoursepages "Big Data Engineer Course").

- [[Components]]
- [[Rise of Big Data]]
- [[Big data and its challenges]]
- [[Importance of Hadoop]]





## File Formats Supported by Hadoop

[Hive](https://www.simplilearn.com/tutorials/hadoop-tutorial/hive "Hive") and Impala table in [HDFS](https://www.simplilearn.com/tutorials/hadoop-tutorial/hdfs "HDFS") can be created using four different Hadoop file formats:

- Text files
- Sequence File
- Avro data files
- Parquet file format

Let’s learn about each Hadoop file formats in detail.

1. Text files

A text file is the most basic and a human-readable file. It can be read or written in any programming language and is mostly delimited by comma or tab.

The text file format consumes more space when a numeric value needs to be stored as a string. It is also difficult to represent binary data such as an image.

2. Sequence File

The sequencefile format can be used to store an image in the binary format. They store key-value pairs in a binary container format and are more efficient than a text file. However, sequence files are not human- readable.

3. Avro Data Files

The Avro file format has efficient storage due to optimized binary encoding. It is widely supported both inside and outside the [Hadoop ecosystem](https://www.simplilearn.com/tutorials/hadoop-tutorial/hadoop-ecosystem "Hadoop ecosystem").

The Avro file format is ideal for long-term storage of important data. It can read from and write in many languages like [Java](https://www.simplilearn.com/tutorials/java-tutorial/learn-java "Java"), Scala and so on.Schema metadata can be embedded in the file to ensure that it will always be readable. Schema evolution can accommodate changes. The Avro file format is considered the best choice for general-purpose storage in Hadoop.

4. Parquet File Format

Parquet is a columnar format developed by Cloudera and Twitter. It is supported in Spark, MapReduce, Hive, Pig, Impala, Crunch, and so on. Like Avro, schema metadata is embedded in the file.

Parquet file format uses advanced optimizations described in Google’s Dremel paper. These optimizations reduce the storage space and increase performance. This Parquet file format is considered the most efficient for adding multiple records at a time. Some optimizations rely on identifying repeated patterns. We will look into what data serialization is in the next section.

### What is Data Serialization?

Data serialization is a way to represent data in the storage memory as a series of bytes. It allows you to save data to disk or send it across the network.

For example, how do you serialize the number 123456789? It can be serialized as 4 bytes when stored as a Java int and 9 bytes when stored as a Java String.

Avro is an efficient data serialization framework, widely supported throughout Hadoop and its ecosystem. It also supports Remote Procedure Calls or RPC and offers compatibility with programming environment without compromising performance. Let’s take a look at the data types supported by Apache Avro and Avro Schemas.

### Avro With Scoop

Avro and Parquet file format use Sqoop which is a tool designed to transfer data between Hadoop and "[Relational Database Management System](https://www.simplilearn.com/what-is-database-management-article "Relational Database Management System")" or "RDBMS"

In Sqoop, you can import data to HDFS in the Avro format and export the Avro format to RDBMS. To perform the operation, add the parameter--as-avrodatafile in the Sqoop command.

Hive supports all Avro types. However, Impala does not support complex or nested types with Avro, such as enum, array, fixed, map, union, and record (nested).

In the next section, we will discuss how to import data in Parquet file format using Sqoop.

### Parquet With Sqoop

You can import data to HDFS in the Parquet file format and export the Parquet file format to RDBMS using [Sqoop](https://www.simplilearn.com/tutorials/hadoop-tutorial/sqoop "Sqoop"). To perform the operation, add the parameter: -as-parquetfile in the Sqoop command. In the next section, we will discuss how to import [Mysql](https://www.simplilearn.com/tutorials/sql-tutorial/create-mysql-database "Mysql") to hdfs in Parquet File Format.

### Summary

Here’s a quick summary of the Hadoop file formats tutorial!

- Hive and Impala tables in HDFS can be created using text files.
- Sequence files, Avro data files, and Parquet file formats.
- Data serialization is a way of representing data in memory as a series of bytes.
- Avro is an efficient data serialization framework and is widely supported throughout Hadoop and its ecosystem.
- Using Sqoop, data can be imported to HDFS in Avro and Parquet file formats.
- Using Sqoop, Avro, and Parquet file format can be exported to RDBMS.
