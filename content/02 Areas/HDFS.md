---
aliases: 
id: 20240223164620
title: "HDFS"
created: 2024-02-23T21:46:20.251Z
tags:
  - areas
  - type/litnote
---
# HDFS

areas: [[Hadoop]]

## Hadoop HDFS

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

### Detailed Explanation:

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


