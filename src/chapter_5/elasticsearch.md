# ElasticSearch



## 学习进度

看到这里了：https://www.elastic.co/guide/cn/elasticsearch/guide/current/routing-value.html



## 笔记

[es历史](https://www.elastic.co/about/history-of-elasticsearch)


[shay banon](https://www.elastic.co/blog/author/shay-banon)

Near Real Time

[节点类型](https://www.elastic.co/guide/en/elasticsearch/reference/current/modules-node.html)

打分机制：从TF-IDF改成BM25，也叫[similarity](https://www.elastic.co/guide/en/elasticsearch/reference/current/index-modules-similarity.html) ，scoring，ranking

oversharding问题,如何创建分片数？

如何知道数据在集群中的哪个节点？

es和mysql数据模型区别？

结构化搜索和全文搜索

全文搜索：传统数据库确实很难搞定的任务，传统数据库要么匹配，要么不匹配，es有相关性打分。

PB级别，数百台服务器

一个分片是一个 Lucene 的实例，以及它本身就是一个完整的搜索引擎

每个字段的所有数据都是默认被索引的

index是逻辑概念，面向用户，shard是物理概念，面向机器，应用程序关心索引，而不是分片

Elasticsearch中文档是不可改变的，不能修改它们，在内部，Elasticsearch 已将旧文档标记为已删除，并增加一个全新的文档，并且会重新进行索引。

更新文档：标记删除，创建文档，重新索引，检索-修改-重建索引












Data Replication:Primary-Backup

in-sync shard（可以被选中为primary的shard）




## Internals

https://www.elastic.co/blog/found-elasticsearch-internals
https://www.elastic.co/blog/found-elasticsearch-networking




## 遇到问题

1.forbidden-12-index-read-only-allow-delete-api?

某个节点的磁盘满了，需要运维清理下磁盘



## Course

https://github.com/xiaozhiliaoo/geektime-ELK

