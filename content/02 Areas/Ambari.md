---
aliases: 
id: 20240223171059
title: "Ambari"
created: 2024-02-23T22:10:59.992Z
tags:
  - areas
  - type/litnote
---

# Ambari

areas:[[Hadoop Ecosystem]]

### Ambari

![[_bin/images/Data Engineering/clip_image040.jpg]]

Next up, we have Apache Ambari. It is an open-source tool responsible for keeping track of running applications and their statuses. Ambari manages, monitors, and provisions Hadoop clusters. Also, it also provides a central management service to start, stop, and configure Hadoop services.

As seen in the following image, the Ambari web, which is your interface, is connected to the Ambari server. Apache Ambari follows a master/slave architecture. The master node is accountable for keeping track of the state of the infrastructure. For doing this, the master node uses a database server that can be configured during the setup time. Most of the time, the Ambari server is located on the MasterNode, and is connected to the database. This is where agents look into the host server. Agents run on all the nodes that you want to manage under Ambari. This program occasionally sends heartbeats to the master node to show its aliveness. By using Ambari Agent, the Ambari Server is able to execute many tasks.

![[_bin/images/Data Engineering/clip_image041.jpg]]

We have two more data streaming services, [[Kafka]] and [[Apache Storm]].
