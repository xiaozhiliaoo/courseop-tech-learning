# Kafka简介

## 笔记

### Kafka

Kafka是事件处理平台，提供了事件存储能力Kafka的Log，事件计算KSQLDB，Kafka Stream。

Kafka Ecosystem: Kafka,Kafka Stream,Kafka Connect,KSQLDB.

事件处理中出现了问题，那么Materialize可以是发邮件，也可以是存到存储系统中。

kafka发送消息是k，v类型的。没发送一个消息，offset+1
m
https://developer.confluent.io/learn-kafka/event-sourcing/event-driven-vs-state-based/

软件设计方法：

state-based（databases+ synchronous network call）

event-based（data at rest + data in motion + event sourcing + CQRS + event streaming）

CRUD：Databases

CR：Event Sourcing

Topic：Event：Key:Partition,Schema

Table：Row：Primary Key,Shard,Schema

Index：Document：_id,Shard,Mapping

Collection：Document:DocumentId,Shard,Schema

Kafka Queue is Log:Append Only and Durable,Reading Message never delete. Other Message is Queue. Message is Bounded
Buffer can be deleted. Topic is Log. Not Queue. Topic(DLT) is Queue(DLQ).

same key -> same partition -> in order ,key is null -> round robin ,key is nonull -> hash function

rewind,reprocess,replayable,reblance,

consumer group protocol(join+leave)

### Kafka Connector

Consumer+Materialize = Kafka Connect ,Consumer+Stateful = Kafka Stream ,Consumer+Stateless = Kafka Consumer

数据是流动的处理平台(Kafka)和数据是静止的处理平台(MySQL)

DLQ:Dead Letter Queue

### Kafka Stream

KTable:Last Updated Value

Kafka Core: Log+Event

Kafka Stream = KStream,KTable,Serialization,Joins,Stateful Operations,Windowing,Times,Processor,

Joins:Stream-Stream(Windows),Stream-Table,Table-Table

Stateless:filter,map, Stateful(use pre event):group by key,reduce,aggregation(sum,count,avg,max,min),join

Time Windows: https://kafka.apache.org/30/javadoc/org/apache/kafka/streams/kstream/TimeWindows.html

Session Windows: https://kafka.apache.org/30/javadoc/org/apache/kafka/streams/kstream/SessionWindows.html

SlidingWindows: https://kafka.apache.org/30/javadoc/org/apache/kafka/streams/kstream/SlidingWindows.html

### ksqlDB

ksqlDB:distributed compute layer
kafka:distributed storage layer

Streams：unbounded series of event. Table: the current state of event

Stateful Aggregations (Materialized Views)

ksqlDB can build a materialized view of state

Kafka is a database turned inside out


### Data Mesh

software architecture vs data architecture

service mesh vs data mesh




## 配置

### broker配置

default.replication.factor

unclean.leader.election.enable

min.insync.replicas

## producer配置

acks(0,1,all)

[retries](https://kafka.apache.org/documentation/#producerconfigs_retries)

## 设计

## 实现



## 其他

[Kafka vs. Pulsar vs. RabbitMQ](https://www.confluent.io/kafka-vs-pulsar/)

