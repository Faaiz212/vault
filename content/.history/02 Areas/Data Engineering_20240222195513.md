---
aliases: 
id: 20240222193835
title: "Data Engineering"
created: 2024-02-23T00:38:35.592Z
tags:
  - areas
  - type/litnote
---

Table of Contents


# **Hadoop**

## What is Hadoop?

Hadoop is a framework that uses distributed storage and parallel processing to store and manage big data. It is the software most used by data analysts to handle big data, and its [market size continues to grow.](https://www.businesswire.com/news/home/20201112005841/en/Global-Hadoop-Market-2020-to-2027---by-Component-Deployment-Model-Organization-Size-and-End-user---ResearchAndMarkets.com "market size continues to grow.") There are three components of Hadoop:

Hadoop HDFS - [Hadoop Distributed File System (HDFS)](https://www.simplilearn.com/tutorials/hadoop-tutorial/hdfs "Hadoop Distributed File System (HDFS)") is the storage unit.

Hadoop MapReduce - [Hadoop MapReduce](https://www.simplilearn.com/tutorials/hadoop-tutorial/mapreduce "Hadoop MapReduce") is the processing unit.

Hadoop YARN - [Yet Another Resource Negotiator (YARN)](https://www.simplilearn.com/tutorials/hadoop-tutorial/yarn "Yet Another Resource Negotiator (YARN)") is a resource management unit.

## The Rise of Big Data

Back in the day, there was limited data generation. Hence, storing and processing data was done with a single storage unit and a processor, respectively. In the blink of an eye, data generation increases by leaps and bounds. Not only did it increase in volume but also its variety. Therefore, a single processor was incapable of processing high volumes of different varieties of data. Speaking of varieties of data, you can have structured, semi-structured and unstructured data. 

[[_bin\/images\/Data Engineering\/clip_image001.jpg]]

This chart is analogous to how Jack found it hard to harvest different types of fruits single-handedly. Thus, just like Jack’s approach, analysts needed multiple processors to process various data types.

Multiple machines help process data parallelly. However, the storage unit became a bottleneck resulting in a network overhead generation

[[_bin\/images\/Data Engineering\/clip_image002.jpg]]

To address this issue, the storage unit is distributed amongst each of the processors. The distribution resulted in storing and accessing data efficiently and with no network overheads. As seen below, this method is called parallel processing with distributed storage.

[[_bin\/images\/Data Engineering\/clip_image003.jpg]]

This setup is how data engineers and analysts manage big data effectively. Now, do you see the connection between Jack’s story and big data management?

## Big Data and Its Challenges

Big Data refers to the massive amount of data that cannot be stored, processed, and analyzed using traditional ways.

The main elements of Big Data are:

Volume - There is a massive amount of data generated every second.

Velocity - The speed at which data is generated, collected, and analyzed

Variety - The different types of data: structured, semi-structured, unstructured

Value - The ability to turn data into useful insights for your business

Veracity - Trustworthiness in terms of quality and accuracy

The main challenges that Big Data faced and the solutions for each are listed below:

|   |   |
|---|---|
|Challenges|Solution|
|Single central storage|Distributed storage|
|Serial processing<br><br>One input<br><br>One processor<br><br>One output|Parallel processing<br><br>Multiple inputs<br><br>Multiple processors<br><br>One output|
|Lack of ability to process unstructured data|Ability to process every type of data|

Let’s understand what is Hadoop in details

## Why Is Hadoop Important?

Hadoop is a beneficial technology for data analysts. There are many essential features in Hadoop which make it so important and user-friendly.

The system is able to store and process enormous amounts of data at an extremely fast rate. A semi-structured, structured and unstructured data set can differ depending on how the data is structured.

Enhances operational decision-making and batch workloads for historical analysis by supporting real-time analytics.

Data can be stored by organizations, and it can be filtered for specific analytical uses by processors as needed. 

A large number of nodes can be added to Hadoop as it is scalable, so organization’s will be able to pick up more data.

A protection mechanism prevents applications and data processing from being harmed by hardware failures. Nodes that are down are automatically redirected to other nodes, allowing applications to run without interruption. 

Based on the above reasons, we can say that Hadoop is important.

## Components of Hadoop

Hadoop is a framework that uses distributed storage and parallel processing to store and manage Big Data. It is the most commonly used software to handle Big Data. There are three components of Hadoop.

Hadoop HDFS - Hadoop Distributed File System (HDFS) is the storage unit of Hadoop.

Hadoop MapReduce - Hadoop MapReduce is the processing unit of Hadoop.

Hadoop YARN - Hadoop YARN is a resource management unit of Hadoop.

Let us take a detailed look at Hadoop HDFS in this part of the What is Hadoop article.

### Hadoop HDFS

Data is stored in a distributed manner in HDFS. There are two components of HDFS - name node and [data](https://www.simplilearn.com/what-is-data-article "data") node. While there is only one name node, there can be multiple data nodes.

HDFS is specially designed for storing huge datasets in commodity hardware. An enterprise version of a server costs roughly $10,000 per terabyte for the full processor. In case you need to buy 100 of these enterprise version servers, it will go up to a million dollars.

Hadoop enables you to use commodity machines as your data nodes. This way, you don’t have to spend millions of dollars just on your data nodes. However, the name node is always an enterprise server.

### Features of HDFS

Provides distributed storage

Can be implemented on commodity hardware

Provides data security

Highly fault-tolerant - If one machine goes down, the data from that machine goes to the next machine

Master and Slave Nodes

Master and slave nodes form the [HDFS cluster](https://www.simplilearn.com/what-is-a-hadoop-cluster-article "HDFS cluster"). The name node is called the master, and the data nodes are called the slaves.

[[_bin\/images\/Data Engineering\/clip_image005.jpg]]

The name node is responsible for the workings of the data nodes. It also stores the metadata.

The data nodes read, write, process, and replicate the data. They also send signals, known as heartbeats, to the name node. These heartbeats show the status of the data node.

[[_bin\/images\/Data Engineering\/clip_image007.jpg]]

Consider that 30TB of data is loaded into the name node. The name node distributes it across the data nodes, and this data is replicated among the data notes. You can see in the image above that the blue, grey, and red data are replicated among the three data nodes.

Replication of the data is performed three times by default. It is done this way, so if a commodity machine fails, you can replace it with a new machine that has the same data.

## Detailed Explanation:

Introduction:

- Hadoop Distributed File System (HDFS): Designed for commodity hardware, fault-tolerant, high throughput access to large data sets.

- Originally for Apache Nutch, now an Apache Hadoop subproject.

- Key features include fault tolerance, scalability, and high throughput.

Assumptions and Goals:

1. Hardware Failure: Detection and automatic recovery crucial due to frequent hardware failures.

2. Streaming Data Access: Suited for batch processing, emphasizes high throughput over low latency.

3. Large Data Sets: Supports gigabytes to terabytes, scalable to hundreds of nodes for massive data storage.

4. Simple Coherency Model: Write-once-read-many access simplifies data coherency and enables high throughput.

5. "Moving Computation is Cheaper than Moving Data": Emphasizes moving computation close to data to minimize network congestion and increase overall system throughput.

6. Portability Across Platforms: Designed for easy deployment across heterogeneous hardware and software platforms.

NameNode and DataNodes:

- Master/slave architecture with a single NameNode managing metadata and multiple DataNodes storing actual data.

- NameNode handles file system namespace operations, while DataNodes serve read/write requests and manage block storage.

[[_bin\/images\/Data Engineering\/clip_image009.jpg]]- Uses Java for portability, with NameNode typically running on a dedicated machine and DataNodes distributed across the cluster.

File System Namespace:

- Supports hierarchical organization with directories and files.

- NameNode maintains namespace and replication factor of files, records changes in the EditLog.

Data Replication:

- Files stored as blocks replicated for fault tolerance.

- Replication factor configurable per file, maintained by NameNode, ensures reliability and availability.

[[_bin\/images\/Data Engineering\/clip_image011.jpg]]

Replica Placement:

- Critical for reliability and performance optimization.

- Rack-aware placement policy balances reliability, availability, and network bandwidth utilization.

- Default policy places replicas on local and remote racks to optimize performance without compromising reliability.

Robustness:

- Objective is reliable data storage despite failures.

- Handles NameNode, DataNode failures, and network partitions through heartbeat mechanism and re-replication strategies.

Metadata and Snapshots:

- NameNode stores metadata persistently in EditLog and FsImage.

- Snapshots feature (future release) supports storing data at specific points in time for recovery purposes.

Data Organization:

- Supports very large files with write-once-read-many semantics.

- Client-side caching and replication pipelining optimize performance for streaming writes and reads.

Space Reclamation:

- Files deleted moved to trash for restoration, gradually deleted to free up space.

- Decreasing replication factor triggers removal of excess replicas to reclaim space.

Communication Protocols:

- Layered on TCP/IP, with Client Protocol for clients and DataNode Protocol for DataNodes.

- RPC abstraction facilitates communication between nodes.

Browser Interface:

- Web server exposes HDFS namespace for navigation via web browser.

- Allows users to view and interact with files and directories in HDFS.

Conclusion:

Understanding Hadoop's architecture, data organization, and robustness features is crucial for efficient utilization. HDFS offers fault tolerance, scalability, and high throughput, making it suitable for handling large data sets in batch processing applications.

Let us focus on Hadoop MapReduce in the following section of the What is Hadoop article.

## Hadoop MapReduce

Hadoop MapReduce is the processing unit of Hadoop. In the MapReduce approach, the processing is done at the slave nodes, and the final result is sent to the master node.

A data containing code is used to process the entire data. This coded data is usually very small in comparison to the data itself. You only need to send a few kilobytes worth of code to perform a heavy-duty process on computers.

[[_bin\/images\/Data Engineering\/clip_image013.jpg]]

The input dataset is first split into chunks of data. In this example, the input has three lines of text with three separate entities - “bus car train,” “ship ship train,” “bus ship car.” The dataset is then split into three chunks, based on these entities, and processed parallelly.

In the map phase, the data is assigned a key and a value of 1. In this case, we have one bus, one car, one ship, and one train.

These key-value pairs are then shuffled and sorted together based on their keys. At the reduce phase, the aggregation takes place, and the final output is obtained.

Hadoop YARN is the next concept we shall focus on in the What is Hadoop article.

### Hadoop YARN

Hadoop YARN stands for Yet Another Resource Negotiator. It is the resource management unit of Hadoop and is available as a component of Hadoop version 2.

Hadoop YARN acts like an OS to Hadoop. It is a file system that is built on top of HDFS.

It is responsible for managing cluster resources to make sure you don't overload one machine.

It performs job scheduling to make sure that the jobs are scheduled in the right place

[[_bin\/images\/Data Engineering\/clip_image015.jpg]]

Suppose a client machine wants to do a query or fetch some code for [data analysis](https://www.simplilearn.com/data-analysis-methods-process-types-article "data analysis"). This job request goes to the resource manager (Hadoop Yarn), which is responsible for resource allocation and management.

In the node section, each of the nodes has its node managers. These node managers manage the nodes and monitor the resource usage in the node. The containers contain a collection of physical resources, which could be RAM, CPU, or hard drives. Whenever a job request comes in, the app master requests the container from the node manager. Once the node manager gets the resource, it goes back to the Resource Manager.

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

## Hadoop Ecosystem

### HDFS

[[_bin\/images\/Data Engineering\/clip_image016.jpg]]

In the traditional approach, all data was stored in a single central database. With the rise of big data, a single database was not enough to handle the task. The solution was to use a distributed approach to store the massive volume of information. Data was divided up and allocated to many individual databases. [HDFS](https://www.simplilearn.com/tutorials/hadoop-tutorial/hdfs "HDFS") is a specially designed file system for storing huge datasets in commodity hardware, storing information in different formats on various machines. 

[[_bin\/images\/Data Engineering\/clip_image017.jpg]]

There are two components in HDFS:

NameNode - NameNode is the master daemon. There is only one active NameNode. It manages the DataNodes and stores all the metadata.

DataNode   - DataNode is the slave daemon. There can be multiple DataNodes. It stores the actual data.

So, we spoke of HDFS storing data in a distributed fashion, but did you know that the storage system has certain specifications? HDFS splits the data into multiple blocks, defaulting to a maximum of 128 MB. The default block size can be changed depending on the processing speed and the data distribution. Let’s have a look at the example below:

[[_bin\/images\/Data Engineering\/clip_image018.jpg]]

As seen from the above image, we have 300 MB of data. This is broken down into 128 MB, 128 MB, and 44 MB. The final block handles the remaining needed storage space, so it doesn’t have to be sized at 128 MB. This is how data gets stored in a distributed manner in HDFS.

Now that you have an overview of HDFS, it is also vital for you to understand what it sits on and how the HDFS cluster is managed. That is done by YARN, and that’s what we’re looking at next.

### YARN (Yet Another Resource Negotiator)

[[_bin\/images\/Data Engineering\/clip_image019.jpg]]

[YARN](https://www.simplilearn.com/tutorials/hadoop-tutorial/yarn "YARN") is an acronym for Yet Another Resource Negotiator. It handles the cluster of nodes and acts as Hadoop’s resource management unit. YARN allocates RAM, memory, and other resources to different applications.

[[_bin\/images\/Data Engineering\/clip_image020.jpg]]

### YARN Has Two Components:

ResourceManager (Master) - This is the master daemon. It manages the assignment of resources such as CPU, memory, and network bandwidth.

NodeManager (Slave) - This is the slave daemon, and it reports the resource usage to the Resource Manager.

Let us move on to MapReduce, Hadoop’s processing unit.

MapReduce

[[_bin\/images\/Data Engineering\/clip_image022.jpg]]

Hadoop data processing is built on [MapReduce](https://www.simplilearn.com/tutorials/hadoop-tutorial/mapreduce "MapReduce"), which processes large volumes of data in a parallelly distributed manner. With the help of the figure below, we can understand how MapReduce works:

[[_bin\/images\/Data Engineering\/clip_image023.jpg]]

As we see, we have our big data that needs to be processed, with the intent of eventually arriving at an output. So in the beginning, input data is divided up to form the input splits. The first phase is the Map phase, where data in each split is passed to produce output values. In the shuffle and sort phase, the mapping phase’s output is taken and grouped into blocks of similar data. Finally, the output values from the shuffling phase are aggregated. It then returns a single output value. 

In summary, HDFS, MapReduce, and YARN are the three components of Hadoop. Let us now dive deep into the data collection and ingestion tools, starting with Sqoop.

### Sqoop

[[_bin\/images\/Data Engineering\/clip_image025.jpg]]

[Sqoop](https://www.simplilearn.com/tutorials/hadoop-tutorial/sqoop "Sqoop") is used to transfer data between Hadoop and external datastores such as relational databases and enterprise data warehouses. It imports data from external datastores into HDFS, Hive, and HBase.

As seen below, the client machine gathers code, which will then be sent to Sqoop. The Sqoop then goes to the Task Manager, which in turn connects to the enterprise data warehouse, documents based systems, and RDBMS. It can map those tasks into Hadoop.

[[_bin\/images\/Data Engineering\/clip_image026.jpg]]

### Flume

[[_bin\/images\/Data Engineering\/clip_image027.jpg]]

Flume is another data collection and ingestion tool, a distributed service for collecting, aggregating, and moving large amounts of log data. It ingests online streaming data from social media, logs files, web server into HDFS.

[[_bin\/images\/Data Engineering\/clip_image028.jpg]]

As you can see below, data is taken from various sources, depending on your organization’s needs. It then goes through the source, channel, and sink. The sink feature ensures that everything is in sync with the requirements. Finally, the data is dumped into HDFS.

[[_bin\/images\/Data Engineering\/clip_image030.jpg]]

Let us now have a look at Hadoop’s scripting languages and query languages.

### Pig

[[_bin\/images\/Data Engineering\/clip_image032.jpg]]

[Apache Pig](https://www.simplilearn.com/tutorials/hadoop-tutorial/pig "Apache Pig") was developed by Yahoo researchers, targeted mainly towards non-programmers. It was designed with the ability to analyze and process large datasets without using complex Java codes. It provides a high-level data processing language that can perform numerous operations without getting bogged down with too many technical concepts.

It consists of:

Pig Latin - This is the language for scripting 

Pig Latin Compiler - This converts Pig Latin code into executable code

Pig also provides Extract, Transfer, and Load (ETL), and a platform for building data flow. Did you know that ten lines of Pig Latin script equals approximately 200 lines of MapReduce job? Pig uses simple, time-efficient steps to analyze datasets. Let’s take a closer look at Pig’s architecture. 

[[_bin\/images\/Data Engineering\/clip_image033.jpg]]

Programmers write scripts in Pig Latin to analyze data using Pig. Grunt Shell is Pig’s interactive shell, used to execute all Pig scripts. If the Pig script is written in a script file, the Pig Server executes it. The parser checks the syntax of the Pig script, after which the output will be a DAG (Directed Acyclic Graph). The DAG (logical plan) is passed to the logical optimizer. The compiler converts the DAG into MapReduce jobs. The MapReduce jobs are then run by the Execution Engine. The results are displayed using the “DUMP” statement and stored in HDFS using the “STORE” statement.

Next up on the language list is Hive.

### Hive

[[_bin\/images\/Data Engineering\/clip_image034.jpg]]

[Hive](https://www.simplilearn.com/tutorials/hadoop-tutorial/hive "Hive") uses SQL (Structured Query Language) to facilitate the reading, writing, and management of large datasets residing in distributed storage. The hive was developed with a vision of incorporating the concepts of tables and columns with SQL since users were comfortable with writing queries in SQL. 

Apache Hive has two major components:

Hive Command Line  

JDBC/ ODBC driver

The Java Database Connectivity (JDBC) application is connected through JDBC Driver, and the Open Database Connectivity (ODBC) application is connected through ODBC Driver. Commands are executed directly in CLI. Hive driver is responsible for all the queries submitted, performing the three steps of compilation, optimization, and execution internally. It then uses the MapReduce framework to process queries.

Hive’s architecture is shown below:

[[_bin\/images\/Data Engineering\/clip_image035.jpg]]

### Spark

[[_bin\/images\/Data Engineering\/clip_image036.jpg]]

Spark is a huge framework in and of itself, an open-source distributed computing engine for processing and analyzing vast volumes of real-time data. It runs 100 times faster than MapReduce. Spark provides an in-memory computation of data, used to process and analyze real-time streaming data such as stock market and banking data, among other things.

[[_bin\/images\/Data Engineering\/clip_image037.jpg]]

As seen from the above image, the MasterNode has a driver program. The Spark code behaves as a driver program and creates a SparkContext, which is a gateway to all of the Spark functionalities. Spark applications run as independent sets of processes on a cluster. The driver program and Spark context take care of the job execution within the cluster. A job is split into multiple tasks that are distributed over the worker node. When an RDD is created in the Spark context, it can be distributed across various nodes. Worker nodes are slaves that run different tasks. The Executor is responsible for the execution of these tasks. Worker nodes execute the tasks assigned by the Cluster Manager and return the results to the SparkContext.

Let us now move to the field of Hadoop Machine Learning and its different permutations. 

### Mahout

[[_bin\/images\/Data Engineering\/clip_image038.jpg]]

Mahout is used to create scalable and distributed machine learning algorithms such as clustering, linear regression, classification, and so on. It has a library that contains built-in algorithms for collaborative filtering, classification, and clustering.  
  
[[_bin\/images\/Data Engineering\/clip_image039.jpg]]

### Ambari

[[_bin\/images\/Data Engineering\/clip_image040.jpg]]

Next up, we have Apache Ambari. It is an open-source tool responsible for keeping track of running applications and their statuses. Ambari manages, monitors, and provisions Hadoop clusters. Also, it also provides a central management service to start, stop, and configure Hadoop services.

As seen in the following image, the Ambari web, which is your interface, is connected to the Ambari server. Apache Ambari follows a master/slave architecture. The master node is accountable for keeping track of the state of the infrastructure. For doing this, the master node uses a database server that can be configured during the setup time. Most of the time, the Ambari server is located on the MasterNode, and is connected to the database. This is where agents look into the host server. Agents run on all the nodes that you want to manage under Ambari. This program occasionally sends heartbeats to the master node to show its aliveness. By using Ambari Agent, the Ambari Server is able to execute many tasks.

[[_bin\/images\/Data Engineering\/clip_image041.jpg]]

We have two more data streaming services, Kafka and Apache Storm.

### Kafka

[[_bin\/images\/Data Engineering\/clip_image043.jpg]]

Kafka is a distributed streaming platform designed to store and process streams of records. It is written in Scala. It builds real-time streaming data pipelines that reliably get data between applications, and also builds real-time applications that transform data into streams. 

Kafka uses a messaging system for transferring data from one application to another. As seen below, we have the sender, the message queue, and the receiver involved in data transfer. 

[[_bin\/images\/Data Engineering\/clip_image044.jpg]]

### Storm

[[_bin\/images\/Data Engineering\/clip_image045.jpg]]

The storm is an engine that processes real-time streaming data at a very high speed. It is written in Clojure. A storm can handle over 1 million jobs on a node in a fraction of a second. It is integrated with Hadoop to harness higher throughputs. 

Now that we have looked at the various data ingestion tools and streaming services let us take a look at the security frameworks in the Hadoop ecosystem. 

### Ranger

[[_bin\/images\/Data Engineering\/clip_image046.jpg]]

Ranger is a framework designed to enable, monitor, and manage data security across the Hadoop platform. It provides centralized administration for managing all security-related tasks. Ranger standardizes authorization across all [Hadoop components](https://www.simplilearn.com/tutorials/hadoop-tutorial/what-is-hadoop "Hadoop components"), and provides enhanced support for different authorization methods like role-based access control, and attributes based access control, to name a few.

### Knox

![  clip_image047.jpg)

Apache Knox is an application gateway used in conjunction with Hadoop deployments, interacting with REST APIs and UIs. The gateway delivers three types of user-facing services:

Proxying Services - This provides access to Hadoop via proxying the HTTP request

Authentication Services - This gives authentication for REST API access and WebSSO flow for user interfaces

Client Services - This provides client development either via scripting through DSL or using the Knox shell classes

Let us now take a look at the workflow system, Oozie. 

### Oozie

[[_bin\/images\/Data Engineering\/clip_image048.jpg]]

Oozie is a workflow scheduler system used to manage Hadoop jobs. It consists of two parts:

Workflow engine - This consists of Directed Acyclic Graphs (DAGs), which specify a sequence of actions to be executed

Coordinator engine - The engine is made up of workflow jobs triggered by time and data availability

As seen from the flowchart below, the process begins with the MapReduce jobs. This action can either be successful, or it can end in an error. If it is successful, the client is notified by an email. If the action is unsuccessful, the client is similarly notified, and the action is terminated. 

[[_bin\/images\/Data Engineering\/clip_image049.jpg]]

### Conclusion

We hope this has helped you gain a better understanding of the Hadoop ecosystem. If you’ve read through this lesson, you have learned about HDFS, YARN, MapReduce, Sqoop, Flume, Pig, Hive, Spark, Mahout, Ambari, Kafka, Storm, Ranger, Knox, and Oozie. Furthermore, you have an idea of what each of these tools does. 

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

# **Hive**

No one can better explain what Hive in Hadoop is than [the creators of Hive](https://hive.apache.org/index.html "the creators of Hive") themselves: "The Apache Hive™ data warehouse software facilitates reading, writing, and managing large datasets residing in distributed storage using SQL. The structure can be projected onto data already in storage."

In other words, Hive is an open-source system that processes structured data in Hadoop, residing on top of the latter for summarizing Big Data, as well as facilitating analysis and queries.

Now that we have investigated what is Hive in Hadoop, let’s look at the features and characteristics.

## Architecture of Hive

[[_bin\/images\/Data Engineering\/clip_image051.jpg]]

The above figure shows the architecture of Apache Hive and its major components. The major components of Apache Hive are:

1. **Hive Client**
2. **Hive Services**
3. **Processing and Resource Management**
4. **Distributed Storage**

### Hive Client

Hive supports applications written in any language like Python, Java, C++, Ruby, etc. using JDBC, ODBC, and Thrift drivers, for performing queries on the Hive. Hence, one can easily write a hive client application in any language of its own choice.

Hive clients are categorized into three types:

#### 1. Thrift Clients

The Hive server is based on Apache Thrift so that it can serve the request from a thrift client.

#### 2. JDBC Client

Hive allows for the Java applications to connect to it using the JDBC driver. JDBC driver uses Thrift to communicate with the Hive Server.

#### 3. ODBC Client

Hive ODBC driver allows applications based on the ODBC protocol to connect to Hive. Similar to the JDBC driver, the ODBC driver uses Thrift to communicate with the Hive Server.

### Hive Service

To perform all queries, Hive provides various services like the Hive server2, Beeline, etc. The various services offered by Hive are:

#### 1. Beeline

The Beeline is a command shell supported by HiveServer2, where the user can submit its queries and command to the system. It is a **JDBC** client that is based on **SQLLINE CLI** (pure Java-console-based utility for connecting with relational databases and executing SQL queries).

#### 2. Hive Server 2

HiveServer2 is the successor of HiveServer1. HiveServer2 enables clients to execute queries against the Hive. It allows multiple clients to submit requests to Hive and retrieve the final results. It is basically designed to provide the best support for open API clients like JDBC and ODBC.

**Note:** Hive server1, also called a Thrift server, is built on Apache Thrift protocol to handle the cross-platform communication with Hive. It allows different client applications to submit requests to Hive and retrieve the final results.

It does not handle concurrent requests from more than one client due to which it was replaced by HiveServer2.

#### 3. Hive Driver

The Hive driver receives the **HiveQL** statements submitted by the user through the command shell. It creates the session handles for the query and sends the query to the compiler.

#### 4. Hive Compiler

Hive compiler parses the query. It performs semantic analysis and type-checking on the different query blocks and query expressions by using the metadata stored in metastore and generates an execution plan.

The execution plan created by the compiler is the **DAG(Directed Acyclic Graph)**, where each stage is a map/reduce job, operation on HDFS, a metadata operation.

#### 5. Optimizer

Optimizer performs the transformation operations on the execution plan and splits the task to improve efficiency and scalability.

#### 6. Execution Engine

Execution engine, after the compilation and optimization steps, executes the execution plan created by the compiler in order of their dependencies using Hadoop.

#### 7. Metastore

Metastore is a central repository that stores the metadata information about the structure of tables and partitions, including column and column type information.

It also stores information of serializer and deserializer, required for the read/write operation, and HDFS files where data is stored. This metastore is generally a relational database.

Metastore provides a Thrift interface for querying and manipulating Hive metadata.

We can configure metastore in any of the two modes:

- **Remote:** In remote mode, metastore is a Thrift service and is useful for non-Java applications.
- **Embedded:** In embedded mode, the client can directly interact with the metastore using JDBC.

#### 8. HCatalog

HCatalog is the table and storage management layer for Hadoop. It enables users with different data processing tools such as Pig, MapReduce, etc. to easily read and write data on the grid.

It is built on the top of Hive metastore and exposes the tabular data of Hive metastore to other data processing tools.

#### 9. WebHCat

WebHCat is the REST API for HCatalog. It is an HTTP interface to perform Hive metadata operations. It provides a service to the user for running Hadoop MapReduce (or YARN), Pig, Hive jobs.

### Processing Framework and Resource Management

Hive internally uses a **MapReduce** framework as a defacto engine for executing the queries.

MapReduce is a software framework for writing those applications that process a massive amount of data in parallel on the large clusters of commodity hardware. MapReduce job works by splitting data into chunks, which are processed by map-reduce tasks.

### Distributed Storage

Hive is built on top of Hadoop, so it uses the underlying Hadoop Distributed File System for the distributed storage.

### Summary

In short, we can summarize the Hive Architecture tutorial by saying that Apache Hive is an open-source data warehousing tool. The major components of Apache Hive are the Hive clients, Hive services, Processing framework and Resource Management, and the Distributed Storage.

The user interacts with the Hive through the user interface by submitting Hive queries.

The driver passes the Hive query to the compiler. The compiler generates the execution plan. The Execution engine executes the plan.

Let us now see how to process data with Apache Hive.

## Working of Hive

**Step 1: executeQuery:** The user interface calls the execute interface to the driver.

**Step 2: getPlan:** The driver accepts the query, creates a session handle for the query, and passes the query to the compiler for generating the execution plan.

**Step 3: getMetaData:** The compiler sends the metadata request to the metastore.

**Step 4: sendMetaData:** The metastore sends the metadata to the compiler.

The compiler uses this metadata for performing type-checking and semantic analysis on the expressions in the query tree. The compiler then generates the execution plan (**Directed acyclic Graph**). For Map Reduce jobs, the plan contains **map operator trees** (operator trees which are executed on mapper) and **reduce operator tree** (operator trees which are executed on reducer).

**Step 5: sendPlan:** The compiler then sends the generated execution plan to the driver.

**Step 6: executePlan:** After receiving the execution plan from compiler, driver sends the execution plan to the execution engine for executing the plan.

**Step 7: submit job to MapReduce:** The execution engine then sends these stages of DAG to appropriate components.

For each task, either mapper or reducer, the deserializer associated with a table or intermediate output is used in order to read the rows from HDFS files. These are then passed through the associated operator tree.

Once the output gets generated, it is then written to the HDFS temporary file through the serializer. These temporary HDFS files are then used to provide data to the subsequent map/reduce stages of the plan.

For DML operations, the final temporary file is then moved to the table’s location.

**Step 8,9,10: sendResult:** Now for queries, the execution engine reads the contents of the temporary files directly from HDFS as part of a fetch call from the driver. The driver then sends results to the Hive interface.

## Hive's Features

These are Hive's chief characteristics:

- Hive is designed for querying and managing only structured data stored in tables
- Hive is scalable, fast, and uses familiar concepts
- Schema gets stored in a database, while processed data goes into a Hadoop Distributed File System (HDFS)
- Tables and databases get created first; then data gets loaded into the proper tables
- Hive supports four file formats: ORC, SEQUENCEFILE, RCFILE (Record Columnar File), and TEXTFILE
- Hive uses an SQL-inspired language, sparing the user from dealing with the complexity of MapReduce programming. It makes learning more accessible by utilizing familiar concepts found in relational databases, such as columns, tables, rows, and schema, etc.
- The most significant difference between the Hive Query Language (HQL) and SQL is that Hive executes queries on Hadoop's infrastructure instead of on a traditional database
- Since Hadoop's programming works on flat files, Hive uses directory structures to "partition" data, improving performance on specific queries
- Hive supports partition and buckets for fast and simple data retrieval
- Hive supports custom user-defined functions (UDF) for tasks like data cleansing and filtering. Hive UDFs can be defined according to programmers' requirements

## Limitations of Hive

Of course, no resource is perfect, and Hive has some limitations. They are:

- Hive doesn’t support OLTP. Hive supports Online Analytical Processing (OLAP), but not Online Transaction Processing (OLTP).
- It doesn’t support subqueries.
- It has a high latency.
- Hive tables don’t support delete or update operations.

## How Data Flows in the Hive in Simple Terms:

1. The [data analyst](https://www.simplilearn.com/tutorials/data-analytics-tutorial/how-to-become-a-data-analyst "data analyst") executes a query with the User Interface (UI).
2. The driver interacts with the query compiler to retrieve the plan, which consists of the query execution process and metadata information. The driver also parses the query to check syntax and requirements.
3. The compiler creates the job plan (metadata) to be executed and communicates with the metastore to retrieve a metadata request.
4. The metastore sends the metadata information back to the compiler
5. The compiler relays the proposed query execution plan to the driver.
6. The driver sends the execution plans to the execution engine.
7. The execution engine (EE) processes the query by acting as a bridge between the Hive and Hadoop. The job process executes in MapReduce. The execution engine sends the job to the JobTracker, found in the Name node, and assigns it to the TaskTracker, in the Data node. While this is happening, the execution engine executes metadata operations with the metastore.
8. The results are retrieved from the data nodes.
9. The results are sent to the execution engine, which, in turn, sends the results back to the driver and the front end (UI).

Since we have gone on at length about what Hive is, we should also touch on what Hive is not:

- Hive isn't a language for row-level updates and real-time queries
- Hive isn't a relational database
- Hive isn't a design for Online Transaction Processing

As we have looked into what is Hive, let us learn about the Hive modes.

## Hive Modes

Depending on the size of Hadoop data nodes, Hive can operate in two different modes:

- Local mode
- Map-reduce mode

User Local mode when:

- Hadoop is installed under the pseudo mode, possessing only one data node
- The data size is smaller and limited to a single local machine
- Users expect faster processing because the local machine contains smaller datasets.

Use Map Reduce mode when:

- Hadoop has multiple data nodes, and the data is distributed across these different nodes
- Users must deal with more massive data sets

MapReduce is Hive's default mode.

## Hive and Hadoop on AWS

Amazon Elastic Map Reduce (EMR) is a managed service that lets you use big data processing frameworks such as Spark, Presto, Hbase, and, yes, Hadoop to analyze and process large data sets. Hive, in turn, runs on top of Hadoop clusters, and can be used to query data residing in Amazon EMR clusters, employing an SQL language.

## Hive and IBM Db2 Big SQL

Data analysts can query Hive transactional (ACID) tables straight from Db2 Big SQL, although Db2 Big SQL can only see compacted data in the transactional table. Data modification statement results won’t be seen by any queries generated in Db2 Big SQL until you perform a compaction operation, which places data in a base directory.

## Hive vs. Relational Databases

Relational databases, or RDBMS, is a database that stores data in a structured format with rows and columns, a structured form called “tables.” Hive, on the other hand, is a data warehousing system that offers data analysis and queries.

Here’s a handy chart that illustrates the differences at a glance:

|   |   |
|---|---|
|Relational Database|Hive|
|Maintains a database|Maintains a data warehouse|
|Fixed schema|Varied schema|
|Sparse tables|Dense tables|
|Doesn’t support partitioning|Supports automation partition|
|Stores normalized data|Stores both normalized and denormalized data|
|Uses SQL (Structured Query Language)|Uses HQL (Hive Query Language)|

In order to continue our understanding of what Hive is, let us next look at the difference between Pig and Hive.

## Pig vs. Hive

Both [Hive](https://www.simplilearn.com/tutorials/hadoop-tutorial/hive "Hive") and [Pig](https://www.simplilearn.com/tutorials/hadoop-tutorial/pig "Pig") are sub-projects, or tools used to manage data in Hadoop. While Hive is a platform that used to create SQL-type scripts for MapReduce functions, Pig is a procedural language platform that accomplishes the same thing. Here's how their differences break down:

Users

- Data analysts favor Apache Hive
- Programmers and researchers prefer Apache Pig

Language Used

- Hive uses a declarative language variant of SQL called HQL
- Pig uses a unique procedural language called Pig Latin

Data Handling

- Hive works with structured data
- Pig works with both structured and semi-structured data

Cluster Operation

- Hive operates on the cluster's server-side
- Pig operates on the cluster's client-side

Partitioning

- Hive supports partitioning
- Pig doesn't support partitioning

Load Speed

- Hive doesn't load quickly, but it executes faster
- Pig loads quickly

So, if you're a data analyst accustomed to working with SQL and want to perform analytical queries of historical data, then Hive is your best bet. But if you're a programmer and are very familiar with scripting languages and you don't want to be bothered by creating the schema, then use Pig.

In order to strengthen our understanding of what is Hive, let us next look at the difference between Hive and Hbase.

## Apache Hive vs. Apache Hbase

We've spotlighted the differences between Hive and Pig. Now, it's time for a brief comparison between Hive and Hbase.

- HBase is an open-source, column-oriented database management system that runs on top of the Hadoop Distributed File System ([HDFS](https://www.simplilearn.com/tutorials/hadoop-tutorial/hdfs "HDFS"))
- Hive is a query engine, while Hbase is a data storage system geared towards unstructured data. Hive is used mostly for batch processing; Hbase is used extensively for transactional processing
- Hbase processes in real-time and features real-time querying; Hive doesn't and is used only for analytical queries
- Hive runs on the top of Hadoop, while Hbase runs on the top of the HDFS
- Hive isn't a database, but Hbase supports NoSQL databases
- Hive has a schema model, Hbase doesn't
- And finally, Hive is ideal for high latency operations, while Hbase is made primarily for low-level latency ones

## Hive Vs Athena

Amazon Athena and Apache Hive are both tools used for querying and analyzing data. Here are the key differences between them:

1. **Query Language Syntax:** Amazon Athena uses Presto SQL, which is based on ANSI SQL syntax. It supports a wide range of SQL functions and has strong compatibility with various SQL clients. On the other hand, Apache Hive uses its own query language called HiveQL, which is SQL-like but not fully compatible with ANSI SQL. It has additional features like user-defined functions and custom serialization.
2. **Data Processing framework:** Amazon Athena uses a serverless processing framework, where the queries are executed on distributed resources managed by AWS. It offers high scalability and parallelism without the need for infrastructure provisioning. Apache Hive, on the other hand, runs on top of Hadoop MapReduce or Apache Tez for data processing. It requires setting up and configuring Hadoop clusters, which may be complex and time-consuming.
3. **Data Storage Integration:** Amazon Athena directly integrates with AWS S3 as its primary data source and does not require any data loading process. It can query data stored in various formats, such as CSV, JSON, Parquet, and ORC. Apache Hive can also work with various storage systems, including Hadoop Distributed File System (HDFS), but data needs to be loaded into the Hive tables before querying.
4. **Performance and Scalability:** Amazon Athena leverages the highly optimized Presto engine for distributed query execution, enabling fast query processing. It automatically scales up or down based on the query workload, ensuring high performance and resource efficiency. Apache Hive's performance heavily relies on the underlying data processing framework (MapReduce or Tez) and requires manual optimization for better performance.
5. **Data Catalog and Metadata Management:** Amazon Athena utilizes AWS Glue Data Catalog, which provides a central repository for storing table metadata and schema information. It simplifies the process of creating and managing tables, including automatic schema detection. Apache Hive has its own metastore for managing table metadata, but it requires manual configuration and maintenance.
6. **Cost Model and Pricing:** Amazon Athena follows a pay-per-query pricing model, where users are charged based on the amount of data scanned by each query. This allows cost optimization by using data partitioning, compression, and columnar storage techniques. Apache Hive, being part of the Hadoop ecosystem, typically requires infrastructure setup and maintenance costs, including hardware and software licenses.

In summary, Amazon Athena offers a serverless and scalable query service with ANSI SQL compatibility and tight integration with AWS S3, while Apache Hive requires manual setup, has its own query language, and relies on underlying Hadoop infrastructure for distributed processing.

## Hive Optimization Techniques

Data analysts who want to optimize their Hive queries and make them run faster in their clusters should consider the following hacks:

- Partition your data to reduce read time within your directory, or else all the data will get read
- Use appropriate file formats such as the Optimized Row Columnar (ORC) to increase query performance. ORC reduces the original data size by up to 75 percent
- Divide table sets into more manageable parts by employing bucketing
- Improve aggregations, filters, scans, and joins by vectorizing your queries. Perform these functions in batches of 1024 rows at once, rather than one at a time
- Create a separate index table that functions as a quick reference for the original table.

## Hive Table Types

Fundamentally, Hive knows two different types of tables: **Internal table** and the **External table**. The Internal table is also known as the managed table.

We can identify the internal or External tables using the **DESCRIBE FORMATTED table_name** statement in the Hive, which will display either **MANAGED_TABLE** or **EXTERNAL_TABLE** depending on the table type.

### 1. Hive Internal Table

Hive owns the data for the internal tables.

It is the default table in Hive. When the user creates a table in Hive without specifying it as external, then by default, an internal table gets created in a specific location in HDFS.

By default, an internal table will be created in a folder path similar to **/user/hive/warehouse** directory of HDFS. We can override the default location by the location property during table creation.

If we drop the managed table or partition, the table data and the metadata associated with that table will be deleted from the HDFS.

### 2. Hive External Table

Hive does not manage the data of the External table.

We create an external table for external use as when we want to use the data outside the Hive.

External tables are stored outside the warehouse directory. They can access data stored in sources such as remote HDFS locations or Azure Storage Volumes.

Whenever we drop the external table, then only the metadata associated with the table will get deleted, the table data remains untouched by Hive.

We can create the external table by specifying the **EXTERNAL** keyword in the Hive create table statement.

### Difference between Hive Internal and External Table

[[[_bin\/images\/Data Engineering\/clip_image053.jpg]]](https://data-flair.training/blogs/wp-content/uploads/sites/2/2017/09/Hive-internal-table-vs-external-table.jpg)

Let us now see the difference between both Hive tables. The major differences in the internal and external tables in Hive are:

#### 1. LOAD Semantics

The Load semantics varies in both the tables. Let us see the difference in load semantics between the internal table and the external table.

a. Internal Table

When we load data into an internal table, then Hive moves data into the warehouse directory.

b. External Table

With the EXTERNAL keyword, Hive knows that it is not managing the table data, so it does not move data to its warehouse directory. Hive does not even check whether the external location at the time it is defined exists or not.

#### 2. DROP Semantics

Like load semantics, drop semantics also varies in both tables. Let us see the difference in drop semantics between the internal table and the external table.

a. Internal table

Dropping the internal table will delete the table data, as well as the metadata associated with the table.

Table data also gets deleted from the HDFS.

b. External table

Dropping the external table will delete only table metadata. The table content remains untouched.

#### 3. TRUNCATE Support

The **TRUNCATE command** only works for the internal table.

#### 4. ACID Support

ACID/transactional works only for the internal table. They do not work for External Table.

#### 5. Query Result Caching

Query Result Caching that saves the results of an executed Hive query for reuse on subsequent queries only works for the internal table.

### When to Use the Internal and External Table?

#### 1. Hive Internal Table

We can use the internal table in cases:

- When generating temporary tables.
- When required that Hive should manage the lifecycle of the table.
- And when we don’t want table data after deletion.

#### 2. Hive External Table

We can use the external table in cases:

- When we are not creating the table based on the existing table.
- When required to use data outside of Hive. For example, the data files are read and processed by an existing program that does not lock the files.
- When we don’t want to delete the table data completely even after DROP.
- When the data should not be owned by Hive.

## Partitioning

**Apache Hive** organizes tables into **partitions**. Partitioning is a way of dividing a table into related parts based on the values of particular columns like date, city, and department.

Each table in the hive can have one or more partition keys to identify a particular partition. Using partition, it is easy to do queries on slices of the data.

[[[_bin\/images\/Data Engineering\/clip_image055.jpg]]](https://data-flair.training/blogs/wp-content/uploads/sites/2/2017/09/apache-hive-partitioning.jpg)

### Why is Partitioning Important?

In the current century, we know that the huge amount of data which is in the range of petabytes is getting stored in **HDFS**. So due to this, it becomes very difficult for Hadoop users to query this huge amount of data.

The Hive was introduced to lower down this burden of data querying. Apache Hive converts the SQL queries into **MapReduce** jobs and then submits it to the **Hadoop cluster**. When we submit a SQL query, Hive read the entire data-set.

So, it becomes inefficient to run **MapReduce jobs** over a large table. Thus this is resolved by creating partitions in tables. Apache Hive makes this job of implementing partitions very easy by creating partitions by its automatic partition scheme at the time of table creation.

In Partitioning method, all the table data is divided into multiple partitions. Each partition corresponds to a specific value(s) of partition column(s). It is kept as a sub-record inside the table’s record present in the HDFS.

Therefore, on querying a particular table, appropriate partition of the table is queried which contains the query value. Thus, this decreases the I/O time required by the query. Hence increases the performance speed.

### How to Create Partitions in Hive?

To create data partitioning in Hive following command is used-  
_CREATE TABLE table_name (column1 data_type, column2 data_type) PARTITIONED BY (partition1 data_type, partition2 data_type,….);_

### Hive Data Partitioning Example

Now let’s understand data partitioning in Hive with an example. Consider a table named **Tab1**. The table contains client detail like id, name, dept, and yoj( year of joining). Suppose we need to retrieve the details of all the clients who joined in 2012.

Then, the query searches the whole table for the required information. But if we partition the client data with the year and store it in a separate file, this will reduce the query processing time. The below example will help us to learn how to partition a file and its data-

The file name says file1 contains client data table:

[php]tab1/clientdata/file1  
id, name, dept, yoj  
1, sunny, SC, 2009  
2, animesh, HR, 2009  
3, sumeer, SC, 2010  
4, sarthak, TP, 2010[/php]  
Now, let us partition above data into two files using years  
[php]tab1/clientdata/2009/file2  
1, sunny, SC, 2009  
2, animesh, HR, 2009  
tab1/clientdata/2010/file3  
3, sumeer, SC, 2010  
4, sarthak, TP, 2010[/php]

Now when we are retrieving the data from the table, only the data of the specified partition will be queried. Creating a partitioned table is as follows:

[php]CREATE TABLE table_tab1 (id INT, name STRING, dept STRING, yoj INT) PARTITIONED BY (year STRING);  
LOAD DATA LOCAL INPATH tab1’/clientdata/2009/file2’OVERWRITE INTO TABLE studentTab PARTITION (year=’2009′);

  
LOAD DATA LOCAL INPATH tab1’/clientdata/2010/file3’OVERWRITE INTO TABLE studentTab PARTITION (year=’2010′);[/php]

### Types of Hive Partitioning

Till now we have discussed Introduction to Hive Partitions and How to create Hive partitions. Now we are going to introduce the types of data partitioning in Hive. There are two types of Partitioning in Apache Hive-

- Static Partitioning
- Dynamic Partitioning

#### I. Hive Static Partitioning

- Insert input data files individually into a partition table is Static Partition.
- Usually when loading files (big files) into **Hive tables** static partitions are preferred.
- Static Partition saves your time in loading data compared to dynamic partition.
- You “statically” add a partition in the table and move the file into the partition of the table.
- We can alter the partition in the static partition.
- You can get the partition column value from the filename, day of date etc without reading the whole big file.
- If you want to use the Static partition in the hive you should set property **set hive.mapred.mode = strict** This property set by default in hive-site.xml
- Static partition is in Strict Mode.
- You should use where clause to use limit in the static partition.
- You can perform Static partition on Hive Manage table or external table.

#### Ii. Hive Dynamic Partitioning

- Single insert to partition table is known as a dynamic partition.
- Usually, dynamic partition loads the data from the non-partitioned table.
- Dynamic Partition takes more time in loading data compared to static partition.
- When you have large data stored in a table then the Dynamic partition is suitable.
- If you want to partition a number of columns but you don’t know how many columns then also dynamic partition is suitable.
- Dynamic partition there is no required where clause to use limit.
- we can’t perform alter on the Dynamic partition.
- You can perform dynamic partition on hive external table and managed table.
- If you want to use the Dynamic partition in the hive then the mode is in non-strict mode.
- Here are Hive dynamic partition properties you should allow

Hive Partitioning – Advantages and Disadvantages  
a) Hive Partitioning Advantages

- Partitioning in Hive distributes execution load horizontally.
- In partition faster execution of queries with the low volume of data takes place. For example, search population from Vatican City returns very fast instead of searching entire world population.

#### b) Hive Partitioning Disadvantages

- There is the possibility of too many small partition creations- too many directories.
- Partition is effective for low volume data. But there some queries like group by on high volume of data take a long time to execute. For example, grouping population of China will take a long time as compared to a grouping of the population in Vatican City.
- There is no need for searching entire table column for a single record.

## Bucketing

**Hive Partitioning** provides a way of segregating hive table data into multiple files/directories. However, it only gives effective results in few scenarios. Such as:  
  
– When there is the limited number of partitions.  
– Or, while partitions are of comparatively equal size.  
  
Although, it is not possible in all scenarios. For example, when are partitioning our tables based geographic locations like country. Hence, some bigger countries will have large partitions (ex: 4-5 countries itself contributing 70-80% of total data).

While small countries data will create small partitions (remaining all countries in the world may contribute to just 20-30 % of total data). Hence, at that time Partitioning will not be ideal.

Then, to solve that problem of over partitioning, Hive offers Bucketing concept. It is another effective technique for decomposing table data sets into more manageable parts.

### Features of Bucketing in Hive

Basically, this concept is based on hashing function on the bucketed column. Along with mod (by the total number of buckets).

i. Where the hash_function depends on the type of the bucketing column.  
ii. However, the Records with the same bucketed column will always be stored in the same bucket.  
iii. Moreover,  to divide the table into buckets we use CLUSTERED BY clause.  
iv. Generally, in the table directory, each bucket is just a file, and Bucket numbering is 1-based.  
v. Along with Partitioning on Hive tables bucketing can be done and even without partitioning.  
vi. Moreover, Bucketed tables will create almost equally distributed data file parts.

### Advantages of Bucketing in Hive

i. On comparing with non-bucketed tables, Bucketed tables offer the efficient sampling.  
ii. Map-side joins will be faster on bucketed tables than non-bucketed tables, as the data files are equal sized parts.  
iii. Here also bucketed tables offer faster query responses than non-bucketed tables as compared to Similar to partitioning.  
iv. This concept offers the flexibility to keep the records in each bucket to be sorted by one or more columns.  
v. Since the join of each bucket becomes an efficient merge-sort, this makes map-side joins even more efficient.

### Limitations of Bucketing in Hive

i. However, it doesn’t ensure that the table is properly populated.  
ii. So, we need to handle Data Loading into buckets by our-self.

# **Spark**

Industries are using Hadoop extensively to analyze their data sets. The reason is that Hadoop framework is based on a simple programming model (MapReduce) and it enables a computing solution that is scalable, flexible, fault-tolerant and cost effective. Here, the main concern is to maintain speed in processing large datasets in terms of waiting time between queries and waiting time to run the program.

Spark was introduced by Apache Software Foundation for speeding up the Hadoop computational computing software process.

As against a common belief, **Spark is not a modified version of Hadoop** and is not, really, dependent on Hadoop because it has its own cluster management. Hadoop is just one of the ways to implement Spark.

Spark uses Hadoop in two ways – one is **storage** and second is **processing**. Since Spark has its own cluster management computation, it uses Hadoop for storage purpose only.

## Apache Spark

Apache Spark is a lightning-fast cluster computing technology, designed for fast computation. It is based on Hadoop MapReduce and it extends the MapReduce model to efficiently use it for more types of computations, which includes interactive queries and stream processing. The main feature of Spark is its **in-memory cluster computing** that increases the processing speed of an application.

Spark is designed to cover a wide range of workloads such as batch applications, iterative algorithms, interactive queries and streaming. Apart from supporting all these workload in a respective system, it reduces the management burden of maintaining separate tools.

## Evolution of Apache Spark

Spark is one of Hadoop’s sub project developed in 2009 in UC Berkeley’s AMPLab by Matei Zaharia. It was Open Sourced in 2010 under a BSD license. It was donated to Apache software foundation in 2013, and now Apache Spark has become a top level Apache project from Feb-2014.

## Features of Apache Spark

Apache Spark has following features.

·        Speed: Spark performs up to 100 times faster than MapReduce for processing large amounts of data. It is also able to divide the data into chunks in a controlled way.

·        Powerful Caching: Powerful caching and disk persistence capabilities are offered by a simple programming layer.

·        Deployment: Mesos, Hadoop via YARN, or Spark’s own cluster manager can all be used to deploy it.

·        Real-Time: Because of its in-memory processing, it offers real-time computation and low latency.

·        Polyglot: In addition to Java, Scala, Python, and R, Spark also supports all four of these languages. You can write Spark code in any one of these languages. Spark also provides a command-line interface in Scala and Python.

## Two Main Abstractions of Apache Spark

The Apache Spark architecture consists of two main abstraction layers:

Resilient Distributed Datasets (RDD):  
It is a key tool for data computation. It enables you to recheck data in the event of a failure, and it acts as an interface for immutable data. It helps in recomputing data in case of failures, and it is a data structure. There are two methods for modifying RDDs: transformations and actions.

Directed Acyclic Graph (DAG):  
The driver converts the program into a DAG for each job. The Apache Spark Eco-system includes various components such as the API core, Spark SQL, Streaming and real-time processing, MLIB, and Graph X. A sequence of connection between nodes is referred to as a driver. As a result, you can read volumes of data using the Spark shell. You can also use the Spark context -cancel, run a job, task (work), and job (computation) to stop a job.

## Spark Architecture

The Apache Spark base architecture diagram is provided in the following figure:

[[_bin\/images\/Data Engineering\/clip_image057.png]]

When the Driver Program in the Apache Spark architecture executes, it calls the real program of an application and creates a SparkContext. SparkContext contains all of the basic functions. The Spark Driver includes several other components, including a DAG Scheduler, Task Scheduler, Backend Scheduler, and Block Manager, all of which are responsible for translating user-written code into jobs that are actually executed on the cluster.

The Cluster Manager manages the execution of various jobs in the cluster. Spark Driver works in conjunction with the Cluster Manager to control the execution of various other jobs. The cluster Manager does the task of allocating resources for the job. Once the job has been broken down into smaller jobs, which are then distributed to worker nodes, SparkDriver will control the execution.  
Many worker nodes can be used to process an RDD created in the SparkContext, and the results can also be cached.

The Spark Context receives task information from the Cluster Manager and enqueues it on worker nodes.

The executor is in charge of carrying out these duties. The lifespan of executors is the same as that of the Spark Application. We can increase the number of workers if we want to improve the performance of the system. In this way, we can divide jobs into more coherent parts.

### Spark Architecture Applications

A high-level view of the architecture of the Apache Spark application is as follows:

#### The Spark Driver

The master node (process) in a driver process coordinates workers and oversees the tasks. Spark is split into jobs and scheduled to be executed on executors in clusters. Spark contexts (gateways) are created by the driver to monitor the job working in a specific cluster and to connect to a Spark cluster. In the diagram, the driver programmes call the main application and create a spark context (acts as a gateway) that jointly monitors the job working in the cluster and connects to a Spark cluster. Everything is executed using the spark context.

Each Spark session has an entry in the Spark context. Spark drivers include more components to execute jobs in clusters, as well as cluster managers. Context acquires worker nodes to execute and store data as Spark clusters are connected to different types of cluster managers. When a process is executed in the cluster, the job is divided into stages with gain stages into scheduled tasks.

#### The Spark Executors

An executor is responsible for executing a job and storing data in a cache at the outset. Executors first register with the driver programme at the beginning. These executors have a number of time slots to run the application concurrently. The executor runs the task when it has loaded data and they are removed in idle mode. The executor runs in the Java process when data is loaded and removed during the execution of the tasks. The executors are allocated dynamically and constantly added and removed during the execution of the tasks. A driver program monitors the executors during their performance. Users’ tasks are executed in the Java process.

#### Cluster Manager

A driver program controls the execution of jobs and stores data in a cache. At the outset, executors register with the drivers. This executor has a number of time slots to run the application concurrently. Executors read and write external data in addition to servicing client requests. A job is executed when the executor has loaded data and they have been removed in the idle state. The executor is dynamically allocated, and it is constantly added and deleted depending on the duration of its use. A driver program monitors executors as they perform users’ tasks. Code is executed in the Java process when an executor executes a user’s task.

#### Worker Nodes

The slave nodes function as executors, processing tasks, and returning the results back to the spark context. The master node issues tasks to the Spark context and the worker nodes execute them. They make the process simpler by boosting the worker nodes (1 to n) to handle as many jobs as possible in parallel by dividing the job up into sub-jobs on multiple machines. A Spark worker monitors worker nodes to ensure that the computation is performed simply. Each worker node handles one Spark task. In Spark, a partition is a unit of work and is assigned to one executor for each one.

[[_bin\/images\/Data Engineering\/clip_image059.png]]

The following points are worth remembering about this design:

1. There are multiple executor processes for each application, which run tasks on multiple threads over the course of the whole application. This allows applications to be isolated both on the scheduling side (drivers can schedule tasks individually) and the executor side (tasks from different apps can run in different JVMs). Therefore, data must be written to an external storage system before it can be shared across different Spark applications.
2. Even on a cluster manager that also supports other applications, Spark can be run if it can acquire executor processes and these communicate with each other. It’s relatively easy for Spark to operate even on a cluster manager if this can be done even with other applications (e.g. Mesos/YARN).
3. The driver program must listen for and accept incoming connections from its executors throughout its lifetime (e.g., [see spark.driver.port in the network config section](https://spark.apache.org/docs/latest/configuration.html#networking)). Workers must be able to connect to the driver program via the network.
4. The driver is responsible for scheduling tasks on the cluster. It should be run on the same local network as the worker nodes, preferably on the same machine. If you want to send requests to the cluster, it’s preferable to open an RPC and have the driver submit operations from nearby rather than running the driver far away from the worker nodes.

## Modes of Execution

You can choose from three different execution modes: local, shared, and dedicated. These determine where your app’s resources are physically located when you run your app. You can decide where to store resources locally, in a shared location, or in a dedicated location.

1. Cluster mode
2. Client mode
3. Local mode

Cluster mode: Cluster mode is the most frequent way of running Spark Applications. In cluster mode, a user delivers a pre-compiled JAR, Python script, or R script to a cluster manager. Once the cluster manager receives the pre-compiled JAR, Python script, or R script, the driver process is launched on a worker node inside the cluster, in addition to the executor processes. This means that the cluster manager is in charge of all Spark application-related processes.

Client mode: In contrast to cluster mode, where the Spark driver remains on the client machine that submitted the application, the Spark driver is removed in client mode and is therefore responsible for maintaining the Spark driver process on the client machine. These machines, usually referred to as gateway machines or edge nodes, are maintained on the client machine.

Local mode: Local mode runs the entire Spark Application on a single machine, as opposed to the previous two modes, which parallelized the Spark Application through threads on that machine. As a result, the local mode uses threads instead of parallelized threads. This is a common way to experiment with Spark, try out your applications, or experiment iteratively without having to make any changes on Spark’s end.

In practice, we do not recommend using local mode for running production applications.

## Spark Cluster Managers

There are several cluster managers supported by the system:

### Standalone

A Spark cluster manager is included with the software package to make setting up a cluster easy. The Resource Manager and Worker are the only Spark Standalone Cluster components that are independent. There is only one executor that runs tasks on each worker node in Standalone Cluster mode. When a client establishes a connection with the Standalone Master, requests resources, and begins the execution process, a Standalone Clustered master starts the execution process.

The client here is the application master, and it wants the resources from the resource manager. We have a Web UI to view all clusters and job statistics in the Cluster Manager.

[[_bin\/images\/Data Engineering\/clip_image061.png]]

### Apache Mesos

It can run Hadoop MapReduce and service apps as well as be a general cluster manager. Apache Mesos contributes to the development and management of application clusters by using dynamic resource sharing and isolation. It enables the deployment and administration of applications in large-scale cluster environments. 

The Mesos framework includes three components:

·        **Mesos Master**: A Mesos Master cluster provides fault tolerance (the capability to operate and recover from loss when a failure occurs). Because of the Mesos Master design, a cluster contains many Mesos Masters.

·        **Mesos Slave**: A Mesos Slave is an instance that delivers resources to the cluster. When a Mesos Master assigns a task, Mesos Slave does not assign resources.

·        **Mesos Frameworks**: Applications can request resources from the cluster so that the application can perform the tasks. Mesos Frameworks allow for this.

[[_bin\/images\/Data Engineering\/clip_image063.png]]

### Hadoop YARN

A key feature of Hadoop 2.0 is the improved resource manager. The Hadoop ecosystem relies on YARN to handle resources. It consists of the following two components:

·        **Resource Manager**: It controls the allocation of system resources on all applications. A Scheduler and an Application Manager are included. Applications receive resources from the Scheduler.

·        **Node Manager:** Each job or application needs one or more containers, and the Node Manager monitors these containers and their usage. Node Manager consists of an Application Manager and a Container Manager. Each task in the MapReduce framework runs in a container. The Node Manager monitors the containers and resource usage, and this is reported to the Resource Manager.

[[_bin\/images\/Data Engineering\/clip_image065.png]]

**Kubernetes**

A framework for deploying, scaling, and managing containerized applications that are open source.

There is a third-party project (not supported by the Spark project) that adds support for Nomad as a cluster manager.

## Components of Spark

The following illustration depicts the different components of Spark.

[[_bin\/images\/Data Engineering\/clip_image066.png]]

### Apache Spark Core

Spark Core is the underlying general execution engine for spark platform that all other functionality is built upon. It provides In-Memory computing and referencing datasets in external storage systems.

### Spark SQL

Spark SQL is a component on top of Spark Core that introduces a new data abstraction called SchemaRDD, which provides support for structured and semi-structured data.

### Spark Streaming

Spark Streaming leverages Spark Core's fast scheduling capability to perform streaming analytics. It ingests data in mini-batches and performs RDD (Resilient Distributed Datasets) transformations on those mini-batches of data.

### MLlib (Machine Learning Library)

MLlib is a distributed machine learning framework above Spark because of the distributed memory-based Spark architecture. It is, according to benchmarks, done by the MLlib developers against the Alternating Least Squares (ALS) implementations. Spark MLlib is nine times as fast as the Hadoop disk-based version of **Apache Mahout** (before Mahout gained a Spark interface).

### GraphX

GraphX is a distributed graph-processing framework on top of Spark. It provides an API for expressing graph computation that can model the user-defined graphs by using Pregel abstraction API. It also provides an optimized runtime for this abstraction.

## Resilient Distributed Datasets

Resilient Distributed Datasets (RDD) is a fundamental data structure of Spark. It is an immutable distributed collection of objects. Each dataset in RDD is divided into logical partitions, which may be computed on different nodes of the cluster. RDDs can contain any type of Python, Java, or Scala objects, including user-defined classes.

Formally, an RDD is a read-only, partitioned collection of records. RDDs can be created through deterministic operations on either data on stable storage or other RDDs. RDD is a fault-tolerant collection of elements that can be operated on in parallel.

There are two ways to create RDDs − **parallelizing** an existing collection in your driver program, or **referencing a dataset** in an external storage system, such as a shared file system, HDFS, HBase, or any data source offering a Hadoop Input Format.

Spark makes use of the concept of RDD to achieve faster and efficient MapReduce operations. Let us first discuss how MapReduce operations take place and why they are not so efficient.

### Data Sharing is Slow in MapReduce

MapReduce is widely adopted for processing and generating large datasets with a parallel, distributed algorithm on a cluster. It allows users to write parallel computations, using a set of high-level operators, without having to worry about work distribution and fault tolerance.

Unfortunately, in most current frameworks, the only way to reuse data between computations (Ex − between two MapReduce jobs) is to write it to an external stable storage system (Ex − HDFS). Although this framework provides numerous abstractions for accessing a cluster’s computational resources, users still want more.

Both **Iterative** and **Interactive** applications require faster data sharing across parallel jobs. Data sharing is slow in MapReduce due to **replication, serialization**, and **disk IO**. Regarding storage system, most of the Hadoop applications, they spend more than 90% of the time doing HDFS read-write operations.

### Iterative Operations on MapReduce

Reuse intermediate results across multiple computations in multi-stage applications. The following illustration explains how the current framework works, while doing the iterative operations on MapReduce. This incurs substantial overheads due to data replication, disk I/O, and serialization, which makes the system slow.

[[_bin\/images\/Data Engineering\/clip_image067.jpg]]

### Interactive Operations on MapReduce

User runs ad-hoc queries on the same subset of data. Each query will do the disk I/O on the stable storage, which can dominate application execution time.

The following illustration explains how the current framework works while doing the interactive queries on MapReduce.

[[_bin\/images\/Data Engineering\/clip_image068.jpg]]

### Data Sharing Using Spark RDD

Data sharing is slow in MapReduce due to **replication, serialization**, and **disk IO**. Most of the Hadoop applications, they spend more than 90% of the time doing HDFS read-write operations.

Recognizing this problem, researchers developed a specialized framework called Apache Spark. The key idea of spark is **R**esilient **D**istributed **D**atasets (RDD); it supports in-memory processing computation. This means, it stores the state of memory as an object across the jobs and the object is sharable between those jobs. Data sharing in memory is 10 to 100 times faster than network and Disk.

Let us now try to find out how iterative and interactive operations take place in Spark RDD.

### Iterative Operations on Spark RDD

The illustration given below shows the iterative operations on Spark RDD. It will store intermediate results in a distributed memory instead of Stable storage (Disk) and make the system faster.

**Note** − If the Distributed memory (RAM) is not sufficient to store intermediate results (State of the JOB), then it will store those results on the disk.

[[_bin\/images\/Data Engineering\/clip_image070.jpg]]

### Interactive Operations on Spark RDD

This illustration shows interactive operations on Spark RDD. If different queries are run on the same set of data repeatedly, this particular data can be kept in memory for better execution times.

[[_bin\/images\/Data Engineering\/clip_image071.jpg]]

By default, each transformed RDD may be recomputed each time you run an action on it. However, you may also **persist** an RDD in memory, in which case Spark will keep the elements around on the cluster for much faster access, the next time you query it. There is also support for persisting RDDs on disk, or replicated across multiple nodes.

### RDD Transformations

RDD transformations returns pointer to new RDD and allows you to create dependencies between RDDs. Each RDD in dependency chain (String of Dependencies) has a function for calculating its data and has a pointer (dependency) to its parent RDD.

Spark is lazy, so nothing will be executed unless you call some transformation or action that will trigger job creation and execution. Look at the following snippet of the word-count example.

Therefore, RDD transformation is not a set of data but is a step in a program (might be the only step) telling Spark how to get data and what to do with it.

Given below is a list of RDD transformations.

|   |   |
|---|---|
|**S.No**|**Transformations & Meaning**|
|**1**|**map(func)**<br><br>Returns a new distributed dataset, formed by passing each element of the source through a function **func**.|
|**2**|**filter(func)**<br><br>Returns a new dataset formed by selecting those elements of the source on which **func** returns true.|
|**3**|**flatMap(func)**<br><br>Similar to map, but each input item can be mapped to 0 or more output items (so _func_ should return a Seq rather than a single item).|
|**4**|**mapPartitions(func)**<br><br>Similar to map, but runs separately on each partition (block) of the RDD, so **func** must be of type Iterator<T> ⇒ Iterator<U> when running on an RDD of type T.|
|**5**|**mapPartitionsWithIndex(func)**<br><br>Similar to map Partitions, but also provides **func** with an integer value representing the index of the partition, so **func** must be of type (Int, Iterator<T>) ⇒ Iterator<U> when running on an RDD of type T.|
|**6**|**sample(withReplacement, fraction, seed)**<br><br>Sample a **fraction** of the data, with or without replacement, using a given random number generator seed.|
|**7**|**union(otherDataset)**<br><br>Returns a new dataset that contains the union of the elements in the source dataset and the argument.|
|**8**|**intersection(otherDataset)**<br><br>Returns a new RDD that contains the intersection of elements in the source dataset and the argument.|
|**9**|**distinct([numTasks])**<br><br>Returns a new dataset that contains the distinct elements of the source dataset.|
|**10**|**groupByKey([numTasks])**<br><br>When called on a dataset of (K, V) pairs, returns a dataset of (K, Iterable<V>) pairs.<br><br>**Note** − If you are grouping in order to perform an aggregation (such as a sum or average) over each key, using reduceByKey or aggregateByKey will yield much better performance.|
|**11**|**reduceByKey(func, [numTasks])**<br><br>When called on a dataset of (K, V) pairs, returns a dataset of (K, V) pairs where the values for each key are aggregated using the given reduce function _func_, which must be of type (V, V) ⇒ V. Like in groupByKey, the number of reduce tasks is configurable through an optional second argument.|
|**12**|**aggregateByKey(zeroValue)(seqOp, combOp, [numTasks])**<br><br>When called on a dataset of (K, V) pairs, returns a dataset of (K, U) pairs where the values for each key are aggregated using the given combine functions and a neutral "zero" value. Allows an aggregated value type that is different from the input value type, while avoiding unnecessary allocations. Like in groupByKey, the number of reduce tasks is configurable through an optional second argument.|
|**13**|**sortByKey([ascending], [numTasks])**<br><br>When called on a dataset of (K, V) pairs where K implements Ordered, returns a dataset of (K, V) pairs sorted by keys in ascending or descending order, as specified in the Boolean ascending argument.|
|**14**|**join(otherDataset, [numTasks])**<br><br>When called on datasets of type (K, V) and (K, W), returns a dataset of (K, (V, W)) pairs with all pairs of elements for each key. Outer joins are supported through leftOuterJoin, rightOuterJoin, and fullOuterJoin.|
|**15**|**cogroup(otherDataset, [numTasks])**<br><br>When called on datasets of type (K, V) and (K, W), returns a dataset of (K, (Iterable<V>, Iterable<W>)) tuples. This operation is also called group With.|
|**16**|**cartesian(otherDataset)**<br><br>When called on datasets of types T and U, returns a dataset of (T, U) pairs (all pairs of elements).|
|**17**|**pipe(command, [envVars])**<br><br>Pipe each partition of the RDD through a shell command, e.g. a Perl or bash script. RDD elements are written to the process's stdin and lines output to its stdout are returned as an RDD of strings.|
|**18**|**coalesce(numPartitions)**<br><br>Decrease the number of partitions in the RDD to numPartitions. Useful for running operations more efficiently after filtering down a large dataset.|
|**19**|**repartition(numPartitions)**<br><br>Reshuffle the data in the RDD randomly to create either more or fewer partitions and balance it across them. This always shuffles all data over the network.|
|**20**|**repartitionAndSortWithinPartitions(partitioner)**<br><br>Repartition the RDD according to the given partitioner and, within each resulting partition, sort records by their keys. This is more efficient than calling repartition and then sorting within each partition because it can push the sorting down into the shuffle machinery.|

## Actions

The following table gives a list of Actions, which return values.

|   |   |
|---|---|
|**S.No**|**Action & Meaning**|
|**1**|**reduce(func)**<br><br>Aggregate the elements of the dataset using a function **func** (which takes two arguments and returns one). The function should be commutative and associative so that it can be computed correctly in parallel.|
|**2**|**collect()**<br><br>Returns all the elements of the dataset as an array at the driver program. This is usually useful after a filter or other operation that returns a sufficiently small subset of the data.|
|**3**|**count()**<br><br>Returns the number of elements in the dataset.|
|**4**|**first()**<br><br>Returns the first element of the dataset (similar to take (1)).|
|**5**|**take(n)**<br><br>Returns an array with the first **n** elements of the dataset.|
|**6**|**takeSample (withReplacement,num, [seed])**<br><br>Returns an array with a random sample of **num** elements of the dataset, with or without replacement, optionally pre-specifying a random number generator seed.|
|**7**|**takeOrdered(n, [ordering])**<br><br>Returns the first **n** elements of the RDD using either their natural order or a custom comparator.|
|**8**|**saveAsTextFile(path)**<br><br>Writes the elements of the dataset as a text file (or set of text files) in a given directory in the local filesystem, HDFS or any other Hadoop-supported file system. Spark calls toString on each element to convert it to a line of text in the file.|
|**9**|**saveAsSequenceFile(path) (Java and Scala)**<br><br>Writes the elements of the dataset as a Hadoop SequenceFile in a given path in the local filesystem, HDFS or any other Hadoop-supported file system. This is available on RDDs of key-value pairs that implement Hadoop's Writable interface. In Scala, it is also available on types that are implicitly convertible to Writable (Spark includes conversions for basic types like Int, Double, String, etc).|
|**10**|**saveAsObjectFile(path) (Java and Scala)**<br><br>Writes the elements of the dataset in a simple format using Java serialization, which can then be loaded using SparkContext.objectFile().|
|**11**|**countByKey()**<br><br>Only available on RDDs of type (K, V). Returns a hashmap of (K, Int) pairs with the count of each key.|
|**12**|**foreach(func)**<br><br>Runs a function **func** on each element of the dataset. This is usually, done for side effects such as updating an Accumulator or interacting with external storage systems.<br><br>**Note** − modifying variables other than Accumulators outside of the foreach() may result in undefined behavior. See Understanding closures for more details.|

## Shared Variables

Spark contains two different types of shared variables − one is **broadcast variables** and second is **accumulators**.

- **Broadcast variables** − used to efficiently, distribute large values.
- **Accumulators** − used to aggregate the information of particular collection.

### Broadcast Variables

Broadcast variables allow the programmer to keep a read-only variable cached on each machine rather than shipping a copy of it with tasks. They can be used, for example, to give every node, a copy of a large input dataset, in an efficient manner. Spark also attempts to distribute broadcast variables using efficient broadcast algorithms to reduce communication cost.

Spark actions are executed through a set of stages, separated by distributed “shuffle” operations. Spark automatically broadcasts the common data needed by tasks within each stage.

The data broadcasted this way is cached in serialized form and is deserialized before running each task. This means that explicitly creating broadcast variables, is only useful when tasks across multiple stages need the same data or when caching the data in deserialized form is important.

Broadcast variables are created from a variable **v** by calling **SparkContext.broadcast(v)**. The broadcast variable is a wrapper around **v**, and its value can be accessed by calling the **value** method. The code given below shows this −

scala> val broadcastVar = sc.broadcast(Array(1, 2, 3))

**Output** −

broadcastVar: org.apache.spark.broadcast.Broadcast[Array[Int]] = Broadcast(0)

After the broadcast variable is created, it should be used instead of the value **v** in any functions run on the cluster, so that **v** is not shipped to the nodes more than once. In addition, the object **v** should not be modified after its broadcast, in order to ensure that all nodes get the same value of the broadcast variable.

### Accumulators

Accumulators are variables that are only “added” to through an associative operation and can therefore, be efficiently supported in parallel. They can be used to implement counters (as in MapReduce) or sums. Spark natively supports accumulators of numeric types, and programmers can add support for new types. If accumulators are created with a name, they will be displayed in **Spark’s UI**. This can be useful for understanding the progress of running stages (NOTE − this is not yet supported in Python).

An accumulator is created from an initial value **v** by calling **SparkContext.accumulator(v)**. Tasks running on the cluster can then add to it using the **add** method or the += operator (in Scala and Python). However, they cannot read its value. Only the driver program can read the accumulator’s value, using its **value** method.

The code given below shows an accumulator being used to add up the elements of an array −

scala> val accum = sc.accumulator(0)

scala> sc.parallelize(Array(1, 2, 3, 4)).foreach(x => accum += x)

If you want to see the output of above code then use the following command −

scala> accum.value

Output

res2: Int = 10

## Numeric RDD Operations

Spark allows you to do different operations on numeric data, using one of the predefined API methods. Spark’s numeric operations are implemented with a streaming algorithm that allows building the model, one element at a time.

These operations are computed and returned as a **StatusCounter** object by calling **status()** method.

The following is a list of numeric methods available in **StatusCounter**.

|   |   |
|---|---|
|**S.No**|**Methods & Meaning**|
|**1**|**count()**<br><br>Number of elements in the RDD.|
|**2**|**Mean()**<br><br>Average of the elements in the RDD.|
|**3**|**Sum()**<br><br>Total value of the elements in the RDD.|
|**4**|**Max()**<br><br>Maximum value among all elements in the RDD.|
|**5**|**Min()**<br><br>Minimum value among all elements in the RDD.|
|**6**|**Variance()**<br><br>Variance of the elements.|
|**7**|**Stdev()**<br><br>Standard deviation.|

If you want to use only one of these methods, you can call the corresponding method directly on RDD.

# **Yarn**

YARN can be thought of as analogous to an operating system for a cluster. A cluster is a set of loosely or tightly connected computers that work together to be viewed as a single system. The cluster represents the collection of resources, such as compute, memory, disk-space, and network bandwidth, that YARN must arbitrate among jobs that run on the cluster. Similar to how an operating system presides over the machine’s resources and distributes them among competing processes, YARN allocates cluster resources among competing jobs.

## Hadoop YARN Architecture and Component

YARN stands for Yet Another Resource Negotiator. It has two major responsibilities: 

1. Management of cluster resources such as compute, network, and memory 
2. Scheduling and monitoring of jobs 

YARN achieves these goals through two long-running daemons: 

1. Resource Manager 
2. Node Manager

The two components work in a master-slave relationship, where the Resource Manager(RM) is the master and the Node Managers the slave. A single Resource Manager runs in the cluster with one Node Manager per machine. Together, these two components make up the data-computation framework. Let’s discuss the resource manager first.

[[_bin\/images\/Data Engineering\/clip_image073.png]]

### Resource Manager

The Resource Manager is described in the official documentation as the ultimate authority that arbitrates resources among all the applications in the system. The resource manager consists of two parts:

- **Applications Manager:** is responsible for accepting job submissions and starting a container for an entity called the ApplicationMaster. It also restarts the ApplicationMaster container if the container fails. We’ll discuss the details around the ApplicationMaster shortly.

- **Scheduler:** The scheduler is responsible for allocating resources such as disk, CPU, and network running applications, subject to restrictions imposed by queues and capacity. The scheduler does not monitor the applications nor does it initiate restarts on application or hardware failures.

In Unix, a container is a process and in Linux a cgroup. Map and reduce tasks run inside a container. A single machine in the cluster can have multiple containers.

The astute reader would realize that the Resource Manager acts as a single point of failure. If the machine hosting the RM goes down, no jobs can get scheduled. To mitigate this shortcoming, high availability for YARN was introduced in Hadoop 2.4. A pair of Resource Managers runs in Active/Standby configuration to achieve high availability. If the active Resource Manager dies, then the standby one becomes the active and the cluster continues to function correctly. The transition from standby to active mode can be done manually by an administrator or automatically. For automatic transition, Zookeeper is required for election.

### Node Manager

The NodeManager is an agent that runs on every machine in the cluster. It is responsible for launching containers on that machine and managing the use of resources by the containers. It reports the usage back to the Scheduler component of the Resource Manager.

### Containers

A single node houses a set of CPU, RAM, and other CPU-hungry resources like containers. The life cycle of YARN containers is managed by container launch contexts and resources are made available to applications for certain purposes on a given host.

### Application Master

It maintains a registry of running applications and monitors their execution. Whenever a job is submitted to the framework, an Application Master is elected for it. It is in charge of allocating resources from the Resource Manager to the Node Manager, which then monitors and executes the tasks.

## YARN Architecture Features

YARN has become popular for the following reasons –

1. With the scalability of the resource manager of the YARN architecture, Hadoop may manage thousands of nodes and clusters.
2. YARN compatibility with Hadoop 1.0 is maintained by not affecting map-reduce applications.
3. Dynamic utilization of clusters in Hadoop is facilitated by YARN, which gives better cluster utilization.
4. Multi-tenancy enables an organization to gain the benefits of multiple engines at once.

## Application Workflow in Hadoop YARN

The first step of running a YARN application involves requesting the RM (resource manager) to create an Application Master(AM) process. A client submits a job and the RM finds a Node Manager that can launch a container to host the AM process. The AM process represents the client job/application. It can either run the job itself and return or request for additional resources from the RM. In the latter, the RM has Node Managers on other machines launch containers on behalf of the AM process to run the distributed computation. Nodes chosen for new container allocations allow the computation to execute as close as possible to the input data, also known as data locality. Ideally, the container is allocated to a node hosting a replica of the data block. The next preference is a node in the same rack as the input data block, and lastly any available node in the cluster. 

YARN applications run from a few seconds to several days. The jobs to applications mapping can happen in three ways:

1. **One job per application:** This is the simplest model.
2. **Several jobs per application:** This is suitable for running several jobs (maybe related) as a workflow or in a single user session. The benefit is that containers can be reused within jobs and intermediate data between jobs can be cached in memory.
3. **Perpetually running application:** In this model, an application that acts as a coordinator keeps running, even forever and is shared amongst various users. Apache Slider and Impala are two applications that employ this strategy. In the case of Apache Slider, a long-running application master launches other applications on the cluster. An always-on application master reduces the latency to execute a job because the overhead of starting an application master is eliminated.

## Conclusion

YARN is designed to be a highly scalable, distributed system with fault-tolerant and load-balanced components. YARN is an ideal choice for running distributed applications where a large number of tasks need to be executed in parallel. YARN helps in scaling your application up by introducing a concept called resource allocation. It allows you to allocate resources to your tasks depending on their importance. YARN also provides real-time metrics, monitoring, and alerting. It helps in real-time monitoring of your application and alerts you if there is any task failure.