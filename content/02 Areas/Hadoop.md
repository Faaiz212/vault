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

## What is Hadoop?

Hadoop is a framework that uses distributed storage and parallel processing to store and manage big data. It is the software most used by data analysts to handle big data, and its [market size continues to grow.](https://www.businesswire.com/news/home/20201112005841/en/Global-Hadoop-Market-2020-to-2027---by-Component-Deployment-Model-Organization-Size-and-End-user---ResearchAndMarkets.com "market size continues to grow.") There are three components of Hadoop:

Hadoop HDFS - [Hadoop Distributed File System (HDFS)](https://www.simplilearn.com/tutorials/hadoop-tutorial/hdfs "Hadoop Distributed File System (HDFS)") is the storage unit.

Hadoop MapReduce - [Hadoop MapReduce](https://www.simplilearn.com/tutorials/hadoop-tutorial/mapreduce "Hadoop MapReduce") is the processing unit.

Hadoop YARN - [Yet Another Resource Negotiator (YARN)](https://www.simplilearn.com/tutorials/hadoop-tutorial/yarn "Yet Another Resource Negotiator (YARN)") is a resource management unit.

## The Rise of Big Data

Back in the day, there was limited data generation. Hence, storing and processing data was done with a single storage unit and a processor, respectively. In the blink of an eye, data generation increases by leaps and bounds. Not only did it increase in volume but also its variety. Therefore, a single processor was incapable of processing high volumes of different varieties of data. Speaking of varieties of data, you can have structured, semi-structured and unstructured data. 

![[_bin/images/Data Engineering/clip_image001.jpg]]

This chart is analogous to how Jack found it hard to harvest different types of fruits single-handedly. Thus, just like Jack’s approach, analysts needed multiple processors to process various data types.

Multiple machines help process data parallelly. However, the storage unit became a bottleneck resulting in a network overhead generation

![[_bin/images/Data Engineering/clip_image002.jpg]]

To address this issue, the storage unit is distributed amongst each of the processors. The distribution resulted in storing and accessing data efficiently and with no network overheads. As seen below, this method is called parallel processing with distributed storage.

![[_bin/images/Data Engineering/clip_image003.jpg]]

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

![[_bin/images/Data Engineering/clip_image005.jpg]]

The name node is responsible for the workings of the data nodes. It also stores the metadata.

The data nodes read, write, process, and replicate the data. They also send signals, known as heartbeats, to the name node. These heartbeats show the status of the data node.

![[_bin/images/Data Engineering/clip_image007.jpg]]

Consider that 30TB of data is loaded into the name node. The name node distributes it across the data nodes, and this data is replicated among the data notes. You can see in the image above that the blue, grey, and red data are replicated among the three data nodes.

Replication of the data is performed three times by default. It is done this way, so if a commodity machine fails, you can replace it with a new machine that has the same data.

## Detailed Explanation:

Introduction:

- Hadoop Distributed File System ([[HDFS]]): Designed for commodity hardware, fault-tolerant, high throughput access to large data sets.

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

![[_bin/images/Data Engineering/clip_image009.jpg]]

- Uses Java for portability, with NameNode typically running on a dedicated machine and DataNodes distributed across the cluster.

File System Namespace:

- Supports hierarchical organization with directories and files.

- NameNode maintains namespace and replication factor of files, records changes in the EditLog.

Data Replication:

- Files stored as blocks replicated for fault tolerance.

- Replication factor configurable per file, maintained by NameNode, ensures reliability and availability.

![[_bin/images/Data Engineering/clip_image011.jpg]]

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

![[_bin/images/Data Engineering/clip_image013.jpg]]

The input dataset is first split into chunks of data. In this example, the input has three lines of text with three separate entities - “bus car train,” “ship ship train,” “bus ship car.” The dataset is then split into three chunks, based on these entities, and processed parallelly.

In the map phase, the data is assigned a key and a value of 1. In this case, we have one bus, one car, one ship, and one train.

These key-value pairs are then shuffled and sorted together based on their keys. At the reduce phase, the aggregation takes place, and the final output is obtained.

Hadoop YARN is the next concept we shall focus on in the What is Hadoop article.

### Hadoop YARN

Hadoop YARN stands for Yet Another Resource Negotiator. It is the resource management unit of Hadoop and is available as a component of Hadoop version 2.

Hadoop YARN acts like an OS to Hadoop. It is a file system that is built on top of HDFS.

It is responsible for managing cluster resources to make sure you don't overload one machine.

It performs job scheduling to make sure that the jobs are scheduled in the right place

![[_bin/images/Data Engineering/clip_image015.jpg]]

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

![[_bin/images/Data Engineering/clip_image016.jpg]]

In the traditional approach, all data was stored in a single central database. With the rise of big data, a single database was not enough to handle the task. The solution was to use a distributed approach to store the massive volume of information. Data was divided up and allocated to many individual databases. [HDFS](https://www.simplilearn.com/tutorials/hadoop-tutorial/hdfs "HDFS") is a specially designed file system for storing huge datasets in commodity hardware, storing information in different formats on various machines. 

![[_bin/images/Data Engineering/clip_image017.jpg]]

There are two components in HDFS:

NameNode - NameNode is the master daemon. There is only one active NameNode. It manages the DataNodes and stores all the metadata.

DataNode   - DataNode is the slave daemon. There can be multiple DataNodes. It stores the actual data.

So, we spoke of HDFS storing data in a distributed fashion, but did you know that the storage system has certain specifications? HDFS splits the data into multiple blocks, defaulting to a maximum of 128 MB. The default block size can be changed depending on the processing speed and the data distribution. Let’s have a look at the example below:

![[_bin/images/Data Engineering/clip_image018.jpg]]

As seen from the above image, we have 300 MB of data. This is broken down into 128 MB, 128 MB, and 44 MB. The final block handles the remaining needed storage space, so it doesn’t have to be sized at 128 MB. This is how data gets stored in a distributed manner in HDFS.

Now that you have an overview of HDFS, it is also vital for you to understand what it sits on and how the HDFS cluster is managed. That is done by YARN, and that’s what we’re looking at next.

### YARN (Yet Another Resource Negotiator)

![[_bin/images/Data Engineering/clip_image019.jpg]]

[YARN](https://www.simplilearn.com/tutorials/hadoop-tutorial/yarn "YARN") is an acronym for Yet Another Resource Negotiator. It handles the cluster of nodes and acts as Hadoop’s resource management unit. YARN allocates RAM, memory, and other resources to different applications.

![[_bin/images/Data Engineering/clip_image020.jpg]]

### YARN Has Two Components:

ResourceManager (Master) - This is the master daemon. It manages the assignment of resources such as CPU, memory, and network bandwidth.

NodeManager (Slave) - This is the slave daemon, and it reports the resource usage to the Resource Manager.

Let us move on to MapReduce, Hadoop’s processing unit.

MapReduce

![[_bin/images/Data Engineering/clip_image022.jpg]]

Hadoop data processing is built on [MapReduce](https://www.simplilearn.com/tutorials/hadoop-tutorial/mapreduce "MapReduce"), which processes large volumes of data in a parallelly distributed manner. With the help of the figure below, we can understand how MapReduce works:

![[_bin/images/Data Engineering/clip_image023.jpg]]

As we see, we have our big data that needs to be processed, with the intent of eventually arriving at an output. So in the beginning, input data is divided up to form the input splits. The first phase is the Map phase, where data in each split is passed to produce output values. In the shuffle and sort phase, the mapping phase’s output is taken and grouped into blocks of similar data. Finally, the output values from the shuffling phase are aggregated. It then returns a single output value. 

In summary, HDFS, MapReduce, and YARN are the three components of Hadoop. Let us now dive deep into the data collection and ingestion tools, starting with Sqoop.

### Sqoop

![[_bin/images/Data Engineering/clip_image025.jpg]]

[Sqoop](https://www.simplilearn.com/tutorials/hadoop-tutorial/sqoop "Sqoop") is used to transfer data between Hadoop and external datastores such as relational databases and enterprise data warehouses. It imports data from external datastores into HDFS, Hive, and HBase.

As seen below, the client machine gathers code, which will then be sent to Sqoop. The Sqoop then goes to the Task Manager, which in turn connects to the enterprise data warehouse, documents based systems, and RDBMS. It can map those tasks into Hadoop.

![[_bin/images/Data Engineering/clip_image026.jpg]]

### Flume

![[_bin/images/Data Engineering/clip_image027.jpg]]

Flume is another data collection and ingestion tool, a distributed service for collecting, aggregating, and moving large amounts of log data. It ingests online streaming data from social media, logs files, web server into HDFS.

![[_bin/images/Data Engineering/clip_image028.jpg]]

As you can see below, data is taken from various sources, depending on your organization’s needs. It then goes through the source, channel, and sink. The sink feature ensures that everything is in sync with the requirements. Finally, the data is dumped into HDFS.

![[_bin/images/Data Engineering/clip_image030.jpg]]

Let us now have a look at Hadoop’s scripting languages and query languages.

### Pig

![[_bin/images/Data Engineering/clip_image032.jpg]]

[Apache Pig](https://www.simplilearn.com/tutorials/hadoop-tutorial/pig "Apache Pig") was developed by Yahoo researchers, targeted mainly towards non-programmers. It was designed with the ability to analyze and process large datasets without using complex Java codes. It provides a high-level data processing language that can perform numerous operations without getting bogged down with too many technical concepts.

It consists of:

Pig Latin - This is the language for scripting 

Pig Latin Compiler - This converts Pig Latin code into executable code

Pig also provides Extract, Transfer, and Load (ETL), and a platform for building data flow. Did you know that ten lines of Pig Latin script equals approximately 200 lines of MapReduce job? Pig uses simple, time-efficient steps to analyze datasets. Let’s take a closer look at Pig’s architecture. 

![[_bin/images/Data Engineering/clip_image033.jpg]]

Programmers write scripts in Pig Latin to analyze data using Pig. Grunt Shell is Pig’s interactive shell, used to execute all Pig scripts. If the Pig script is written in a script file, the Pig Server executes it. The parser checks the syntax of the Pig script, after which the output will be a DAG (Directed Acyclic Graph). The DAG (logical plan) is passed to the logical optimizer. The compiler converts the DAG into MapReduce jobs. The MapReduce jobs are then run by the Execution Engine. The results are displayed using the “DUMP” statement and stored in HDFS using the “STORE” statement.

Next up on the language list is Hive.

### Hive

![[_bin/images/Data Engineering/clip_image034.jpg]]

[Hive](https://www.simplilearn.com/tutorials/hadoop-tutorial/hive "Hive") uses SQL (Structured Query Language) to facilitate the reading, writing, and management of large datasets residing in distributed storage. The hive was developed with a vision of incorporating the concepts of tables and columns with SQL since users were comfortable with writing queries in SQL. 

Apache Hive has two major components:

Hive Command Line  

JDBC/ ODBC driver

The Java Database Connectivity (JDBC) application is connected through JDBC Driver, and the Open Database Connectivity (ODBC) application is connected through ODBC Driver. Commands are executed directly in CLI. Hive driver is responsible for all the queries submitted, performing the three steps of compilation, optimization, and execution internally. It then uses the MapReduce framework to process queries.

Hive’s architecture is shown below:

![[_bin/images/Data Engineering/clip_image035.jpg]]

### Spark

![[_bin/images/Data Engineering/clip_image036.jpg]]

Spark is a huge framework in and of itself, an open-source distributed computing engine for processing and analyzing vast volumes of real-time data. It runs 100 times faster than MapReduce. Spark provides an in-memory computation of data, used to process and analyze real-time streaming data such as stock market and banking data, among other things.

![[_bin/images/Data Engineering/clip_image037.jpg]]

As seen from the above image, the MasterNode has a driver program. The Spark code behaves as a driver program and creates a SparkContext, which is a gateway to all of the Spark functionalities. Spark applications run as independent sets of processes on a cluster. The driver program and Spark context take care of the job execution within the cluster. A job is split into multiple tasks that are distributed over the worker node. When an RDD is created in the Spark context, it can be distributed across various nodes. Worker nodes are slaves that run different tasks. The Executor is responsible for the execution of these tasks. Worker nodes execute the tasks assigned by the Cluster Manager and return the results to the SparkContext.

Let us now move to the field of Hadoop Machine Learning and its different permutations. 

### Mahout

![[_bin/images/Data Engineering/clip_image038.jpg]]

Mahout is used to create scalable and distributed machine learning algorithms such as clustering, linear regression, classification, and so on. It has a library that contains built-in algorithms for collaborative filtering, classification, and clustering.  
  
![[_bin/images/Data Engineering/clip_image039.jpg]]

### Ambari

![[_bin/images/Data Engineering/clip_image040.jpg]]

Next up, we have Apache Ambari. It is an open-source tool responsible for keeping track of running applications and their statuses. Ambari manages, monitors, and provisions Hadoop clusters. Also, it also provides a central management service to start, stop, and configure Hadoop services.

As seen in the following image, the Ambari web, which is your interface, is connected to the Ambari server. Apache Ambari follows a master/slave architecture. The master node is accountable for keeping track of the state of the infrastructure. For doing this, the master node uses a database server that can be configured during the setup time. Most of the time, the Ambari server is located on the MasterNode, and is connected to the database. This is where agents look into the host server. Agents run on all the nodes that you want to manage under Ambari. This program occasionally sends heartbeats to the master node to show its aliveness. By using Ambari Agent, the Ambari Server is able to execute many tasks.

![[_bin/images/Data Engineering/clip_image041.jpg]]

We have two more data streaming services, Kafka and Apache Storm.

### Kafka

![[_bin/images/Data Engineering/clip_image043.jpg]]

Kafka is a distributed streaming platform designed to store and process streams of records. It is written in Scala. It builds real-time streaming data pipelines that reliably get data between applications, and also builds real-time applications that transform data into streams. 

Kafka uses a messaging system for transferring data from one application to another. As seen below, we have the sender, the message queue, and the receiver involved in data transfer. 

![[_bin/images/Data Engineering/clip_image044.jpg]]

### Storm

![[_bin/images/Data Engineering/clip_image045.jpg]]

The storm is an engine that processes real-time streaming data at a very high speed. It is written in Clojure. A storm can handle over 1 million jobs on a node in a fraction of a second. It is integrated with Hadoop to harness higher throughputs. 

Now that we have looked at the various data ingestion tools and streaming services let us take a look at the security frameworks in the Hadoop ecosystem. 

### Ranger

![[_bin/images/Data Engineering/clip_image046.jpg]]

Ranger is a framework designed to enable, monitor, and manage data security across the Hadoop platform. It provides centralized administration for managing all security-related tasks. Ranger standardizes authorization across all [Hadoop components](https://www.simplilearn.com/tutorials/hadoop-tutorial/what-is-hadoop "Hadoop components"), and provides enhanced support for different authorization methods like role-based access control, and attributes based access control, to name a few.

### Knox

![[_bin/images/Data Engineering/clip_image047.jpg]]

Apache Knox is an application gateway used in conjunction with Hadoop deployments, interacting with REST APIs and UIs. The gateway delivers three types of user-facing services:

Proxying Services - This provides access to Hadoop via proxying the HTTP request

Authentication Services - This gives authentication for REST API access and WebSSO flow for user interfaces

Client Services - This provides client development either via scripting through DSL or using the Knox shell classes

Let us now take a look at the workflow system, Oozie. 

### Oozie

![[_bin/images/Data Engineering/clip_image048.jpg]]

Oozie is a workflow scheduler system used to manage Hadoop jobs. It consists of two parts:

Workflow engine - This consists of Directed Acyclic Graphs (DAGs), which specify a sequence of actions to be executed

Coordinator engine - The engine is made up of workflow jobs triggered by time and data availability

As seen from the flowchart below, the process begins with the MapReduce jobs. This action can either be successful, or it can end in an error. If it is successful, the client is notified by an email. If the action is unsuccessful, the client is similarly notified, and the action is terminated. 

![[_bin/images/Data Engineering/clip_image049.jpg]]

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
