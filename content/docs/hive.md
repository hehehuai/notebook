---
title: "hive"
date: 2021-12-27T14:41:32+08:00
weight: 3
draft: true
---
# sql
 * hql
 




# 数据仓库的分层架构
源数据层(ODS)
数据仓库层(Dw)
应用层(DA或者App)
为什么数据分层？
用空间换取时间，存在大量数据冗余
把一个复杂操作分成多个简单数据处理流程

# hive 优缺点
* 优点
操作简单，采用HQL语句，不用写mapreduce，支持自定义语法。
* 缺点
查询时间延迟很严重。
不支持事务


#hadoop
hdfs dfs -ls /

hdfs dfs -put /tmp /hadoop
hdfs dfs -get /hadoop /tmp
hdfs dfs -rm file

# presto
优点
* 基于内存操作，尽量减少落盘操作，计算更快，近乎实时
* 支持多种数据源,不同数据源关联查询
* sql支持
缺点:
* 并发完全把所有数据加载到内存，边加载边处理
* join数据会产生大量临时数据，导致执行速度变慢



show schemas;
use xx;
show tables;
