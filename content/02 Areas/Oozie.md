---
aliases: 
id: 20240223171407
title: "Oozie"
created: 2024-02-23T22:14:07.698Z
tags:
  - areas
  - type/litnote
---

areas:[[Hadoop Ecosystem]]

# Oozie

### Oozie

![[_bin/images/Data Engineering/clip_image048.jpg]]

Oozie is a workflow scheduler system used to manage Hadoop jobs. It consists of two parts:

Workflow engine - This consists of Directed Acyclic Graphs (DAGs), which specify a sequence of actions to be executed

Coordinator engine - The engine is made up of workflow jobs triggered by time and data availability

As seen from the flowchart below, the process begins with the MapReduce jobs. This action can either be successful, or it can end in an error. If it is successful, the client is notified by an email. If the action is unsuccessful, the client is similarly notified, and the action is terminated. 

![[_bin/images/Data Engineering/clip_image049.jpg]]
