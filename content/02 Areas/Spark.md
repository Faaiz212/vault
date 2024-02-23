---
aliases: 
id: 20240222200246
title: "Spark"
created: 2024-02-23T01:02:46.957Z
tags:
  - areas
  - type/litnote
---

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

![[_bin/images/Data Engineering/clip_image057.png]]

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

![[_bin/images/Data Engineering/clip_image059.png]]

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

![[_bin/images/Data Engineering/clip_image061.png]]

### Apache Mesos

It can run Hadoop MapReduce and service apps as well as be a general cluster manager. Apache Mesos contributes to the development and management of application clusters by using dynamic resource sharing and isolation. It enables the deployment and administration of applications in large-scale cluster environments. 

The Mesos framework includes three components:

·        **Mesos Master**: A Mesos Master cluster provides fault tolerance (the capability to operate and recover from loss when a failure occurs). Because of the Mesos Master design, a cluster contains many Mesos Masters.

·        **Mesos Slave**: A Mesos Slave is an instance that delivers resources to the cluster. When a Mesos Master assigns a task, Mesos Slave does not assign resources.

·        **Mesos Frameworks**: Applications can request resources from the cluster so that the application can perform the tasks. Mesos Frameworks allow for this.

![[_bin/images/Data Engineering/clip_image063.png]]

### Hadoop YARN

A key feature of Hadoop 2.0 is the improved resource manager. The Hadoop ecosystem relies on YARN to handle resources. It consists of the following two components:

·        **Resource Manager**: It controls the allocation of system resources on all applications. A Scheduler and an Application Manager are included. Applications receive resources from the Scheduler.

·        **Node Manager:** Each job or application needs one or more containers, and the Node Manager monitors these containers and their usage. Node Manager consists of an Application Manager and a Container Manager. Each task in the MapReduce framework runs in a container. The Node Manager monitors the containers and resource usage, and this is reported to the Resource Manager.

![[_bin/images/Data Engineering/clip_image065.png]]

**Kubernetes**

A framework for deploying, scaling, and managing containerized applications that are open source.

There is a third-party project (not supported by the Spark project) that adds support for Nomad as a cluster manager.

## Components of Spark

The following illustration depicts the different components of Spark.

![[_bin/images/Data Engineering/clip_image066.png]]

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

![[_bin/images/Data Engineering/clip_image067.jpg]]

### Interactive Operations on MapReduce

User runs ad-hoc queries on the same subset of data. Each query will do the disk I/O on the stable storage, which can dominate application execution time.

The following illustration explains how the current framework works while doing the interactive queries on MapReduce.

![[_bin/images/Data Engineering/clip_image068.jpg]]

### Data Sharing Using Spark RDD

Data sharing is slow in MapReduce due to **replication, serialization**, and **disk IO**. Most of the Hadoop applications, they spend more than 90% of the time doing HDFS read-write operations.

Recognizing this problem, researchers developed a specialized framework called Apache Spark. The key idea of spark is **R**esilient **D**istributed **D**atasets (RDD); it supports in-memory processing computation. This means, it stores the state of memory as an object across the jobs and the object is sharable between those jobs. Data sharing in memory is 10 to 100 times faster than network and Disk.

Let us now try to find out how iterative and interactive operations take place in Spark RDD.

### Iterative Operations on Spark RDD

The illustration given below shows the iterative operations on Spark RDD. It will store intermediate results in a distributed memory instead of Stable storage (Disk) and make the system faster.

**Note** − If the Distributed memory (RAM) is not sufficient to store intermediate results (State of the JOB), then it will store those results on the disk.

![[_bin/images/Data Engineering/clip_image070.jpg]]

### Interactive Operations on Spark RDD

This illustration shows interactive operations on Spark RDD. If different queries are run on the same set of data repeatedly, this particular data can be kept in memory for better execution times.

![[_bin/images/Data Engineering/clip_image071.jpg]]

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

