# Hazelcast简介

Hazelcast is a streaming and memory-first application platform for fast, stateful, data-intensive workloads on-premises,
at the edge or as a fully managed cloud service.

产品有：Hazelcast Management Center，IMDG，Jet

# 学习进度

# 提供的新架构，解决方案

# 笔记

内存计算大图：数仓方向Databend，apache arrow，Hadoop->Spark,HDFS->Alluxio,Arrow,HANA,HazelCast, Redis,VoltDB 这些技术的关系。IMDG到底是什么？

内存计算的含义是：IMDG+JET

Apache Beam和Jet组合起来？

IMDG(DataGrid-distributed data) IMDB(DataBase) IMDS(DataStore) IMCG(ComputeGrid-Jet)

使用方式Java Member和Java Client，其他语言只有Client。

Near Cache是client-server模式的二级缓存。

HZ核心设计文档：https://github.com/hazelcast/hazelcast/blob/master/docs/design/template.md

Bridging Between Java 8 Streams and Hazelcast Jet

In-Memory Storage/In-Memory Compute/Real-Time Processing

Distributed Data Design(Partitioning and Replication)： AP:Replication(lazy replication), primary-copy, best-effort, no
strong consistency but monotonic reads guarantee, anti-entropy,at-least-once, CP: Consensus algorithms Raft

嵌入式是否支持”跨应用”发现彼此？

membership具体细节，如何加入和如何退出，以及数据迁移细节官方文档涉及比较少。

Build Distributed System

Core Object：Config,DistributedObject,Node,NodeState,Cluster,HazelcastInstance

FD:PhiAccrualFailureDetector,PhiAccrualClusterFailureDetector,DeadlineClusterFailureDetector,PingFailureDetector

## Jet

Hazelcast Jet no dependency on disk storage, it keeps all of its operational state in the RAM of the cluster


## 竞品

https://www.gartner.com/reviews/market/in-memory-data-grids

Apache Ignite，Pivotal Gemfire，Terracotta BigMemory，JBoss Data Grid，GigaSpaces，Oracle Coherence SAP HANA？timesten

an alternative to Coherence and Terracotta

## Starter

https://docs.hazelcast.com/hazelcast/5.1/pipelines/spring-boot

# 参考

## Paper

[Phi Accrual Failure Detector](https://www.computer.org/csdl/proceedings-article/srds/2004/22390066/12OmNvT2phv)

[Group membership and view synchrony in partitionable asynchronous distributed systems: specifications](https://dl.acm.org/doi/pdf/10.1145/250007.250010)

## Repository

https://github.com/xiaozhiliaoo/hazelcast

https://github.com/xiaozhiliaoo/hazelcast-code-samples

https://github.com/xiaozhiliaoo/hazelcast-jet

https://github.com/xiaozhiliaoo/hazelcast-practice

## 链接

Redis和Hazelcast对比：https://hazelcast.com/compare-with-redis/

Jet和Spark对比：https://hazelcast.com/blog/how-hazelcast-jet-compares-to-apache-spark/