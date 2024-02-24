---
aliases: 
id: 20240222201357
title: "Pig"
created: 2024-02-23T01:13:57.750Z
tags:
  - areas
  - type/litnote
---

Areas:: [[Hadoop Ecosystem]]

---

# Pig



[Apache Pig](https://www.simplilearn.com/tutorials/hadoop-tutorial/pig "Apache Pig") was developed by Yahoo researchers, targeted mainly towards non-programmers. It was designed with the ability to analyze and process large datasets without using complex Java codes. It provides a high-level data processing language that can perform numerous operations without getting bogged down with too many technical concepts.

It consists of:

Pig Latin - This is the language for scripting 

Pig Latin Compiler - This converts Pig Latin code into executable code

Pig also provides Extract, Transfer, and Load (ETL), and a platform for building data flow. Did you know that ten lines of Pig Latin script equals approximately 200 lines of MapReduce job? Pig uses simple, time-efficient steps to analyze datasets. Let’s take a closer look at Pig’s architecture. 

![[_bin/images/Data Engineering/clip_image033.jpg]]

Programmers write scripts in Pig Latin to analyze data using Pig. Grunt Shell is Pig’s interactive shell, used to execute all Pig scripts. If the Pig script is written in a script file, the Pig Server executes it. The parser checks the syntax of the Pig script, after which the output will be a DAG (Directed Acyclic Graph). The DAG (logical plan) is passed to the logical optimizer. The compiler converts the DAG into MapReduce jobs. The MapReduce jobs are then run by the Execution Engine. The results are displayed using the “DUMP” statement and stored in HDFS using the “STORE” statement.

Next up on the language list is Hive.