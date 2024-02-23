---
aliases: 
id: 20240222200144
title: "Hive"
created: 2024-02-23T01:01:44.387Z
tags:
  - areas
  - type/litnote
---


# **Hive**

No one can better explain what Hive in Hadoop is than [the creators of Hive](https://hive.apache.org/index.html "the creators of Hive") themselves: "The Apache Hive™ data warehouse software facilitates reading, writing, and managing large datasets residing in distributed storage using SQL. The structure can be projected onto data already in storage."

In other words, Hive is an open-source system that processes structured data in Hadoop, residing on top of the latter for summarizing Big Data, as well as facilitating analysis and queries.

Now that we have investigated what is Hive in Hadoop, let’s look at the features and characteristics.

## Architecture of Hive

![[_bin/images/Data Engineering/clip_image051.jpg]]

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

[![[_bin/images/Data Engineering/clip_image053.jpg]]](https://data-flair.training/blogs/wp-content/uploads/sites/2/2017/09/Hive-internal-table-vs-external-table.jpg)

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

[![[_bin/images/Data Engineering/clip_image055.jpg]]](https://data-flair.training/blogs/wp-content/uploads/sites/2/2017/09/apache-hive-partitioning.jpg)

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
