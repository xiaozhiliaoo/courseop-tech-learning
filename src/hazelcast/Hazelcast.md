# Hazelcast简介

Hazelcast is a streaming and memory-first application platform for fast, stateful, data-intensive workloads on-premises,
at the edge or as a fully managed cloud service.

产品有：Hazelcast Management Center，IMDG，Jet

# 学习进度

# 提供的新架构，解决方案

# 笔记

cache, distributed lock, key-value store, pub/sub, computing platform,

cache pattern: https://hazelcast.com/blog/a-hitchhikers-guide-to-caching-patterns/
cache read-through MapLoader write-through MapStore Write-Behind write-delay-seconds

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

HZ的AP需要结合复制，一致性，选举去理解。而CP则需要结合线性一致性，共识去理解。

https://www.gartner.com/reviews/market/in-memory-data-grids

对比：https://hazelcast.com/resources/#topic=competitive
Apache Ignite，Pivotal Gemfire，Terracotta BigMemory，JBoss Data Grid，GigaSpaces，Oracle Coherence SAP HANA？timesten

https://www.oracle.com/java/coherence/

an alternative to Coherence and Terracotta

Distributed Snapshots: Chandy-Lamport algorithm JET using it?

讲座：https://hazelcast.com/blog/tech-talk-series/

hz和beam结合例子：https://hazelcast.com/blog/running-apache-beam-on-hazelcast-jet/

Testing the CP Subsystem with Jepsen：https://hazelcast.com/blog/testing-the-cp-subsystem-with-jepsen/
linearizable

CP：https://hazelcast.com/blog/author/ensarbasri/

https://github.com/jepsen-io/jepsen/tree/main/hazelcast

CP group Each CP group executes the Raft consensus algorithm independently

Beam缩写：Batch + strEAM

SQL基于calcite解析。

API文档：https://docs.hazelcast.org/docs/4.2.5/javadoc/，其中关于FencedLock很有意思。

缓存选择：IMap还是ReplicatedMap？为什么ReplicatedMap没有MapLoader和MapStore接口？

IMap+Near Cache

Replicated Map：anti-entropy update operations to all members in the cluster eventually consistent system with
read-your-writes and monotonic-reads consistency

Replicated Map：Mutli-Master IMap：Single Master

Akka的AP提供的是CRDT，HZ的AP提供的是数据结构。

AP数据结构，意味着线性一致性。意味着不一致就不可用。

分布式锁在CP意味着什么？AP意味着什么？这里的强一致性并不是数据。

HZ是PACELC种PA，EC完美案例。

(必读Daniel Abadi文章)Hazelcast和神话般的PA/EC系统：http://dbmsmusings.blogspot.com/2017/10/hazelcast-and-mythical-paec-system.html

PA/EC:系统的基本问题如下：尽管分区是一个罕见的事件，但它们并非不可能。任何建立在PA系统之上的应用都必须有相应的机制来处理这些分区事件中出 现的不一致。但是，一旦他们有了这些机制，为什么不在正常运行期间受益，并获得更好的延时呢？

https://en.wikipedia.org/wiki/PACELC_theorem

IAtomicLong的(incrementAndGet,compareAndSet )意味着分布式的compare-and-set。单机原子变量实现很复杂了。CAS操作。意味着共识。那意味着CAS可以实现非阻塞的锁。
那么为什么不能实现并发的强一致性MAP/LIST？参考juc思路。

AP数据结构并不依赖共识。

如何实现线性化的compareAndSet与全序关系广播等价于共识问题。

HZ的CP官方说是线性一致性。

HZ AP复制模型。primary-backup.primary挂了，怎么选举primary？leader选举不一定需要共识。

CP Subsystem：Unsafe mode，CP group，CP member，

Akka无主，实现了集群单例，主节点选举。

选举不一定需要共识，虽然表面看是对某些事情达成一致。

主节点选举，集群单例，分布式锁，分布式事务与共识关系。

分布式互斥与共识算法。共识和线性化有关系，但是分布式系统在不保证线性化时候，共识并不是必须的。

共识可以解决选主，原子提交，互斥。但是选主，原子提交，选主不一定是共识。




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