# Cassandra

# 进度

# 笔记

先读bigtable(2006)，dynamo(2007)，cassandra(2009)的paper.

范式：one table serve many queries 反范式：one table serve one query

数据建模cassandra风格: 数据查询在一起，存储应该在一起，保持分区和结果集小，使用高基数的key,表是为了查询而建的，没有全表扫描

https://en.wikipedia.org/wiki/Apache_Cassandra

read path和write path发生了什么？

compaction类型minor，major，user defined，scrub 和策略：STCS，LCS，TWCS

多维hashmap

读取很快，简单的查询模型，数据在一起查询那么应该存在一起，使用高基数的key，

数据时间 ttl

cassandra datastax driver三种模式：statement，mapper，accessor + spring data cassandra

column families 也叫 tables

副本修复方式：read repair,hinted handoff

## 运维

### compaction

gc_grace_seconds=10d

### hints

max_hint_windowin_ms=3h

## 常见错误

1. [Invalid query] message="ORDER BY is only supported when the partition key is restricted by an EQ or an IN."。

   order by 操作必须在分区key是 == 或者 in的时候下才可以使用


2. [Invalid query] message="Order by currently only support the ordering of columns following their declared order in
   the PRIMARY KEY"。

   	orderby必须是主键指定的顺序。

# 参考

dbdb.io: https://dbdb.io/db/cassandra

https://github.com/xiaozhiliaoo/cassandra-practice

java客户端：https://docs.datastax.com/en/developer/java-driver/4.13/

spring-data-cassandra: https://docs.spring.io/spring-data/cassandra/docs/current/reference/html/#preface

scylladb:C++写的cassandra.  https://www.scylladb.com/resources/introduction-to-apache-cassandra/

## paper

Backup and Recovery Mechanisms of Cassandra Database: A Review

