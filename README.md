# Awesome Hadoop [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

这是Awesome系列Hadoop及其生态资源的一览表。其他系列比如 [Awesome PHP](https://github.com/ziadoz/awesome-php), [Awesome Python](https://github.com/vinta/awesome-python)
大数据生态也有一份更完整的列表 [Awesome Bigdata](https://github.com/onurakpolat/awesome-bigdata)，中文翻译参见阿里云栖社区 [《史上最全的“大数据”学习资源》](https://yq.aliyun.com/articles/37308)

- [Awesome Hadoop](#awesome-hadoop)
	- [Hadoop](#hadoop)
	- [YARN作业调度](#yarn作业调度)
	- [NoSQL](#nosql)
	- [类SQL处理框架](#类sql处理框架)
	- [数据管理](#数据管理)
	- [工作流、生命周期、治理](#工作流-生命周期-治理)
	- [数据摄取和集成](#数据摄取和集成)
	- [领域专用语言DSL](#领域专用语言dsl)
	- [开发库和工具](#开发库和工具)
	- [实时数据处理](#实时数据处理)
	- [分布式计算和编程](#分布式计算和编程)
	- [Packaging, Provisioning and Monitoring](#packaging-provisioning-and-monitoring)
	- [Monitoring](#monitoring)
	- [Search](#search)
	- [Security](#security)
	- [Benchmark](#benchmark)
	- [Machine learning and Big Data analytics](#machine-learning-and-big-data-analytics)
	- [Misc.](#misc)
- [Resources](#resources)
	- [Websites](#websites)
	- [Presentations](#presentations)
	- [Books](#books)
	- [Hadoop and Big Data Events](#hadoop-and-big-data-events)
- [Other Awesome Lists](#other-awesome-lists)

## Hadoop

* [Apache Hadoop](http://hadoop.apache.org/) - 分布式处理架构，结合了 Common工具、MapReduce（并行处理）、YARN（作业调度）和HDFS（分布式文件系统）

* [Apache Tez](http://tez.apache.org/) - Tez构建于Hadoop YARN之上，是一个通用的数据流编程框架。通过提供强力和灵活的引擎，执行任意DAG(有向无环图 Direct Acyclic Graph)类型作业，来批量或者交互式的处理数据。Tez已经被Hive、 Pig、其他Hadoop生态体系内的框架和一些商用软件（比如ETL工具）所采用，用以替换Hadoop MapReduce作为基础执行引擎/计算框架。

* [SpatialHadoop](http://spatialhadoop.cs.umn.edu/) - SpatialHadoop是一个开源的MapReduce扩展,专门用于在ApacheHadoop集群上处理空间数据

* [GIS Tools for Hadoop](http://esri.github.io/gis-tools-for-hadoop/) - 为Hadoop框架提供大数据空间分析功能

* [Elasticsearch Hadoop](https://github.com/elastic/elasticsearch-hadoop) - 通俗来讲就是，将具有海量数据存储和深度处理能力的Hadoop，与实时搜索和分析的Elasticsearch连接起来。https://www.elastic.co/products/hadoop

* [dumbo](https://github.com/klbostee/dumbo) - Python模块，方便编写和运行Hadoop程序。

* [hadoopy](https://github.com/bwhite/hadoopy) - 用Cython编写的Python MapReduce库

* [mrjob](https://github.com/Yelp/mrjob/) - mrjob是一个Python 2.5+包，用以编写和运行Hadoop Streaming作业

* [pydoop](http://pydoop.sourceforge.net/) - Pydoop提供了Hadoop API的Python包

* [hdfs-du](https://github.com/twitter/hdfs-du) - HDFS的交互式可视化的WEB UI, 来自twitter。

* [White Elephant](https://github.com/linkedin/white-elephant) - Hadoop日志的聚合和仪表盘，可视化Hadoop集群跨用户的使用情况UI，来自Linkedin

* [Kiji Project](http://www.kiji.org/)
* [Genie](https://github.com/Netflix/genie) - Genie是Netflix开源的提供Hadoop, Hive, Pig作业和资源调度工具。

* [Apache Kylin](http://kylin.incubator.apache.org/) - eBay开源的一款分布式分析引擎，可以在Hadoop支持的含量数据集上提供SQL接口和多维度的分析（OLAP）。
场景在预计算,用户指定dimensions和要计算的metric，kylin通过MR将结果保存在HBase中，后续读取直接读HBase。
适合那种业务清楚的知道自己要分析什么的场景。查询模式比较固定，只不过所查看的时间不同的场景。注意的点是要避免维度灾难。
其核心是Cube，cube是一种预计算技术，基本思路是预先对数据作多维索引，查询时只扫描索引而不访问原始数据从而提速。

* [Crunch](https://github.com/jondot/crunch) - Go编写的工具包，用于ETL和特征提取

* [Apache Ignite](http://ignite.apache.org/) - 分布式内存型计算平台

## YARN作业调度
YARN是一个分布式的资源管理系统，用以提高分布式的集群环境下的资源利用率，这些资源包括内存、IO、网络、磁盘等。其产生的原因是为了解决原MapReduce框架的不足。新的 Hadoop MapReduce 框架命名为 MapReduceV2 或者叫 Yarn。

* [Apache Slider](http://slider.incubator.apache.org/) - Apache内部孵化的二级项目，目的是将用户的已有服务或者应用直接部署到YANR上。Slider自带了HBase On YARN，Storm On YARN 和Accumulo On YARN三个实现。

* [Apache Twill](http://twill.apache.org/) - Twill也是内部孵化项目，目前已经是顶级项目。它是为简化YARN上应用程序开发而成立的项目，该项目把与YARN相关的重复性的工作封装成库，使得用户可以专注于自己的应用程序逻辑。

* [mpich2-yarn](https://github.com/alibaba/mpich2-yarn) - YARN上运行 MPICH2 程序，来自Alibaba。
（注：MPI 消息传递接口(Message Passing Interface)基于消息传递的并行程序，MPI并不是一种新的开发语言，它是一个定义了可以被C、C++和Fortran程序调用的函数库。
消息传递指的是并行执行的各个进程具有自己独立的堆栈和代码段，作为互不相关的多个程序独立执行，进程之间的信息交互完全通过显示地调用通信函数来完成。）

## NoSQL
*下一代数据库Not Only SQL，更多面向如下几点：非关系型，分布式，开源和水平扩展。*

* [Apache HBase](http://hbase.apache.org) - Apache HBase
非典型的列式数据库，只是按照列族来分割文件，但是存储是Key-Value，必须基于RowId来查询才快。
* [Apache Phoenix](http://phoenix.apache.org/) - A SQL skin over HBase supporting secondary indices
* [happybase](https://github.com/wbolster/happybase) - A developer-friendly Python library to interact with Apache HBase.
* [Hannibal](https://github.com/sentric/hannibal) - Hannibal is tool to help monitor and maintain HBase-Clusters that are configured for manual splitting.
* [Haeinsa](https://github.com/VCNC/haeinsa) - Haeinsa is linearly scalable multi-row, multi-table transaction library for HBase
* [hindex](https://github.com/Huawei-Hadoop/hindex) - Secondary Index for HBase
* [Apache Accumulo](https://accumulo.apache.org/) - The Apache Accumulo™ sorted, distributed key/value store is a robust, scalable, high performance data storage and retrieval system.
* [OpenTSDB](http://opentsdb.net/) - The Scalable Time Series Database
* [Apache Cassandra](http://cassandra.apache.org/)
* [Apache Kudu](https://kudu.apache.org/) - Kudu provides a combination of fast inserts/updates and efficient columnar scans to enable multiple real-time analytic workloads across a single storage layer, complementing HDFS and Apache HBase.

Kudu目标是很快的分析数据，其希望弥补HDFS和HBase之间的gap，前者是重离线批量，后者重在线随机。
整体而言，Kudu似乎想做一个集合OLTP/OLAP的东西，在线写入，高可用，可选的一致性，即时快速的扫描分析，但是目前感觉定位偏向OLAP。

* [Druid](http://druid.io/) - Druid is an open-source analytics data store designed for business intelligence (OLAP) queries on event data. Druid provides low latency (real-time) data ingestion, flexible data exploration, and fast data aggregation. High-performance, column-oriented, distributed data store.

Druid是一个实时处理时序数据的Olap数据库，因为它的索引首先按照时间分片，查询的时候也是按照时间线去路由索引。
功能介于PowerDrill和Dremel之间，它几乎实现了Dremel的所有功能，并且从PowerDrill吸收一些有趣的数据格式。
用于大数据实时查询和分析的高容错、高性能开源分布式系统，旨在快速处理大规模的数据，并能够实现快速查询和分析。
数据集由三种组件构成， Timestamp列， Dimension列和Metric列([Druid Documentation](http://druid.io/docs/0.9.2/design/index.html))

## 类SQL处理框架

* [Apache Hive](http://hive.apache.org) - The Apache Hive data warehouse software facilitates reading, writing, and managing large datasets residing in distributed storage using SQL

Hive是Facebook开源的一个数据仓库或者说基于类SQL语言的查询分析工具，用于读、写、管理位于分布式存储内的海量数据。
Hive背后可以选择不同的引擎，比如hive on tez, hive on mr, hive on yarn, hive on spark等；
Hive也可以做其他框架的数据源比如spark on hive，和上面hive on spark的区别就是互为提供方而已。

* [Apache Phoenix](http://phoenix.apache.org) A SQL skin over HBase supporting secondary indices

Phoenix 可以当做 HBase 的 SQL 驱动，完全JAVA编写。Phoenix 使得HBase支持通过 JDBC 的方式进行访问，并将你的 SQL 查询转成 HBase 的扫描和相应的动作。
让Hadoop为低延迟的应用程序提供OLTP和业务分析功能，支持二级索引。
可以与Hadoop产品集成，比如Spark, Hive, Pig, Flume, MapReduce。

* [Apache HAWQ (incubating)](http://hawq.incubator.apache.org/) - Apache HAWQ is a Hadoop native SQL query engine that combines the key technological advantages of MPP database with the scalability and convenience of Hadoop
* [Lingual](http://www.cascading.org/projects/lingual/) - SQL interface for Cascading (MR/Tez job generator)
* [Cloudera Impala](http://impala.io/)

Impala是Cloudera在受到Google的Dremel启发下开发的实时交互SQL大数据查询工具，其本质上是一个MPP数据库(Massively Parallel Processing，适合小集群100以内，低并发的50左右的场景)
Hive适合于长时间的批处理查询分析，而Impala适合于实时交互式SQL查询，**Impala给数据分析人员提供了快速实验、验证想法的大数据分析工具。**
可以先使用hive进行数据转换处理，之后使用Impala在Hive处理后的结果数据集上进行快速的数据分析。

* [Presto](https://prestodb.io/) - Distributed SQL Query Engine for Big Data. Open sourced by Facebook.

分布式大数据SQL查询引擎，Facebook开源产品。适用于交互式分析查询，数据量支持GB到PB字节。
JAVA8写的，代码质量非常高。设计：纯内存，没有容错，一个task失败就整个query fail。需要注意调整内存相关，线程数等参数，容易OOM。benchmark还行。支持标准SQL。
Presto背后所使用的执行模式与Hive有根本的不同，它没有使用MapReduce，大部分场景下比hive快一个数量级，其中的关键是所有的处理都在内存中完成。

* [Apache Tajo](http://tajo.apache.org/) - Data warehouse system for Apache Hadoop
* [Apache Drill](https://drill.apache.org/) - Schema-free SQL Query Engine

Drill 是基于 Google Dremel的开源实现。
On a broader category level, Drill, Impala, Hive and Spark SQL all fit into the SQL-on-Hadoop category. But in terms of differentiation capabilities, Drill has the ability to allow data exploration on datasets without having to define any schema definitions upfront in the Hive metastore. Whether your data is text files, JSON files, or whatever other file formats, Drill is built to work with schema that is dynamic, as well as data that is complex. Drill differs from Impala in that it can handle nested data better, and it can also work with data without having to define schema definitions upfront. From a performance standpoint, Drill and Impala are targeting interactive use cases, so both are optimized in terms of performance and SLAs.
上述表达的Drill场景也就是schema-free这个特性。

* [Apache Trafodion](http://trafodion.apache.org/)
* [Apache Spack SQL](http://spark.apache.org/sql/) - Spark SQL is Apache Spark's module for working with structured data. Seamlessly mix SQL queries with Spark programs. Connect to any data source the same way. 

Run unmodified Hive queries on existing data. Connect through JDBC or ODBC. 
基于Spark平台上的一个OLAP框架，本质上也是基于DAG的MPP，基本思路是增加机器来并行计算，从而提高查询速度。

## 数据管理

* [Apache Calcite](http://calcite.apache.org/) - A Dynamic Data Management Framework
* [Apache Atlas](http://atlas.incubator.apache.org/) - Metadata tagging & lineage capture suppoting complex business data taxonomies
* [Apache Parquet](http://parquet.apache.org) - Parquet源自于Google Dremel系统，不同于Drill是Dremel的完整开源实现， Parquet只是Dremel中的数据存储引擎。
Parquet最初的设计动机是存储嵌套式数据，比如Protocolbuffer，thrift，json等，将这类数据存储成列式格式，以方便对其高效压缩和编码，且使用更少的IO操作取出需要的数据，这也是Parquet相比于Apache ORC的优势，它能够透明地将Protobuf和thrift类型的数据进行列式存储，在Protobuf和thrift被广泛使用的今天，与Parquet进行集成，是一件非容易和自然的事情。 
除了上述优势外，相比于ORC, Parquet没有太多其他可圈可点的地方，比如它不支持update操作（数据写成后不可修改），不支持ACID等。

## 工作流/生命周期/治理

* [Apache Oozie](http://oozie.apache.org) - Apache Oozie
* [Azkaban](http://azkaban.github.io/)
* [Apache Falcon](http://falcon.apache.org/) - Data management and processing platform
* [Apache NiFi](http://nifi.apache.org/) - A dataflow system
* [Apache AirFlow](https://github.com/apache/incubator-airflow) - Airflow is a workflow automation and scheduling system that can be used to author and manage data pipelines
* [Luigi](http://luigi.readthedocs.org/en/latest/) - Python package that helps you build complex pipelines of batch jobs

## 数据摄取和集成

* [Apache Flume](http://flume.apache.org) - Apache Flume
* [Suro](https://github.com/Netflix/suro) - Netflix's distributed Data Pipeline
* [Apache Sqoop](http://sqoop.apache.org) - Apache Sqoop
* [Apache Kafka](http://kafka.apache.org/) - Apache Kafka
* [Gobblin from LinkedIn](https://github.com/linkedin/gobblin) - Universal data ingestion framework for Hadoop

## 领域专用语言DSL
*DSL = Domain Specific Language*

* [Apache Pig](http://pig.apache.org) - Yahoo!出品，用于处理数据分析程序的高级查询语言
* [Apache DataFu](http://datafu.incubator.apache.org/) - 由LinkedIn开发的针对Hadoop和Pig的用户定义的函数集合
* [vahara](https://github.com/thedatachef/varaha) - Machine learning and natural language processing with Apache Pig
* [packetpig](https://github.com/packetloop/packetpig) - Open Source Big Data Security Analytics
* [akela](https://github.com/mozilla-metrics/akela) - Mozilla's utility library for Hadoop, HBase, Pig, etc.
* [seqpig](http://seqpig.sourceforge.net/) - Simple and scalable scripting for large sequencing data set(ex: bioinfomation) in Hadoop 
* [Lipstick](https://github.com/Netflix/Lipstick) - Pig workflow visualization tool. [Introducing Lipstick on A(pache) Pig](http://techblog.netflix.com/2013/06/introducing-lipstick-on-apache-pig.html)
* [PigPen](https://github.com/Netflix/PigPen) - PigPen is map-reduce for Clojure, or distributed Clojure. It compiles to Apache Pig, but you don't need to know much about Pig to use it.

## 开发库和工具

* [Kite Software Development Kit](http://kitesdk.org/) - A set of libraries, tools, examples, and documentation
* [gohadoop](https://github.com/hortonworks/gohadoop) - Native go clients for Apache Hadoop YARN.
* [Hue](http://gethue.com/) - A Web interface for analyzing data with Apache Hadoop.
* [Apache Zeppelin](https://zeppelin.incubator.apache.org/) - A web-based notebook that enables interactive data analytics
* [Jumbune](https://github.com/impetus-opensource/jumbune) - Jumbune is an open-source product built for analyzing Hadoop cluster and MapReduce jobs.
* [Apache Thrift](http://thrift.apache.org/)
* [Apache Avro](http://avro.apache.org/) - 数据序列化系统
* [Elephant Bird](https://github.com/twitter/elephant-bird) - Twitter's collection of LZO and Protocol Buffer-related Hadoop, Pig, Hive, and HBase code.
* [Spring for Apache Hadoop](http://projects.spring.io/spring-hadoop/)
* [hdfs - A native go client for HDFS](https://github.com/colinmarc/hdfs)
* [Oozie Eclipse Plugin](https://marketplace.eclipse.org/content/oozie-eclipse-plugin) - A graphical editor for editing Apache Oozie workflows inside Eclipse.
* [Hydrosphere Mist](https://github.com/Hydrospheredata/mist) - a service for exposing Apache Spark analytics jobs and machine learning models as realtime, batch or reactive web services.
* snakebite

## 实时数据处理

* [Apache Beam](https://beam.apache.org/) - 为统一的模型以及一套用于定义和执行数据处理工作流的特定SDK语言；
* [Apache Storm](http://storm.apache.org/) - Twitter流处理框架，也可用于YARN；
* [Apache Samza](http://samza.apache.org/) - 基于Kafka和YARN的流处理框架；
* [Apache Spark Streaming](http://spark.apache.org/streaming/) - 流处理框架。
* [Apache Flink](https://flink.apache.org/) - 针对流数据和批数据的分布式处理引擎，Java实现。link 可以支持本地的快速迭代，以及一些环形的迭代任务。并且 Flink 可以定制化内存管理。
在这点，如果要对比 Flink 和 Spark 的话，Flink 并没有将内存完全交给应用层。这也是为什么 Spark 相对于 Flink，更容易出现 OOM 的原因（out of memory）。
就框架本身与应用场景来说，Flink 更相似与 Storm，支持毫秒级计算，而Spark则只能支持秒级计算。

## 分布式计算和编程

* [Apache Spark](http://spark.apache.org/) - 内存集群计算框架，包括Spark SQL, Spark Streaming, MLlib机器学习和GraphX图计算等库
* [Spark Packages](http://spark-packages.org/) - A community index of packages for Apache Spark
* [SparkHub](https://sparkhub.databricks.com/) - A community site for Apache Spark
* [Apache Crunch](http://crunch.apache.org) - 一个简单的Java API，用于执行在普通的MapReduce实现时比较单调的连接、数据聚合等任务；
* [Cascading](http://www.cascading.org/) - Cascading is the proven application development platform for building data applications on Hadoop.
* [Apache Flink](https://flink.apache.org/) - 针对流数据和批数据的分布式处理引擎，Java实现。link 可以支持本地的快速迭代，以及一些环形的迭代任务。并且 Flink 可以定制化内存管理。
在这点，如果要对比 Flink 和 Spark 的话，Flink 并没有将内存完全交给应用层。这也是为什么 Spark 相对于 Flink，更容易出现 OOM 的原因（out of memory）。
就框架本身与应用场景来说，Flink 更相似与 Storm，支持毫秒级计算，而Spark则只能支持秒级计算

* [Apache Apex (incubating)](http://apex.incubator.apache.org/) - Enterprise-grade unified stream and batch processing engine.

## Packaging, Provisioning and Monitoring

* [Apache Bigtop](http://bigtop.apache.org/) - Apache Bigtop: Packaging and tests of the Apache Hadoop ecosystem 
* [Apache Ambari](http://ambari.apache.org/) - Apache Ambari
* [Ganglia Monitoring System](http://ganglia.sourceforge.net/)
* [ankush](https://github.com/impetus-opensource/ankush) - A big data cluster management tool that creates and manages clusters of different technologies.
* [Apache Zookeeper](http://zookeeper.apache.org/) - Apache Zookeeper
* [Apache Curator](http://curator.apache.org/) - ZooKeeper client wrapper and rich ZooKeeper framework
* [Buildoop](https://github.com/keedio/buildoop) - Hadoop Ecosystem Builder
* [Deploop](http://deploop.github.io/) - The Hadoop Deploy System
* [Jumbune](http://www.jumbune.org/) - An open source MapReduce profiling, MapReduce flow debugging, HDFS data quality validation and Hadoop cluster monitoring tool.
* [inviso](https://github.com/Netflix/inviso) - Inviso is a lightweight tool that provides the ability to search for Hadoop jobs, visualize the performance, and view cluster utilization.

## Search

* [ElasticSearch](https://www.elastic.co/)
* [Apache Solr](http://lucene.apache.org/solr/)
* [SenseiDB](http://www.senseidb.com/) - Open-source, distributed, realtime, semi-structured database
* [Banana](https://github.com/LucidWorks/banana) - Kibana port for Apache Solr

## Search Engine Framework

* [Apache Nutch](http://nutch.apache.org/) - Apache Nutch is a highly extensible and scalable open source web crawler software project.

## Security

* [Apache Ranger](http://ranger.incubator.apache.org/) - Ranger is a framework to enable, monitor and manage comprehensive data security across the Hadoop platform.
* [Apache Sentry](https://sentry.incubator.apache.org/) - An authorization module for Hadoop
* [Apache Knox Gateway](https://knox.apache.org/) - A REST API Gateway for interacting with Hadoop clusters.
* [Project Rhino](https://github.com/intel-hadoop/project-rhino) - Intel's open source effort to enhance the existing data protection capabilities of the Hadoop ecosystem to address security and compliance challenges, and contribute the code back to Apache.

## Benchmark

* [Big Data Benchmark](https://amplab.cs.berkeley.edu/benchmark/)
* [HiBench](https://github.com/intel-hadoop/HiBench)
* [Big-Bench](https://github.com/intel-hadoop/Big-Data-Benchmark-for-Big-Bench)
* [hive-benchmarks](https://github.com/yhuai/hive-benchmarks)
* [hive-testbench](https://github.com/cartershanklin/hive-testbench) - Testbench for experimenting with Apache Hive at any data scale.
* [YCSB](https://github.com/brianfrankcooper/YCSB) - The Yahoo! Cloud Serving Benchmark (YCSB) is an open-source specification and program suite for evaluating retrieval and maintenance capabilities of computer programs. It is often used to compare relative performance of NoSQL database management systems.

## Machine learning and Big Data analytics

* [Apache Mahout](http://mahout.apache.org)
* [Oryx 2](https://github.com/OryxProject/oryx) - Lambda architecture on Spark, Kafka for real-time large scale machine learning
* [MLlib](https://spark.apache.org/mllib/) - MLlib is Apache Spark's scalable machine learning library.
* [R](http://www.r-project.org/) - R is a free software environment for statistical computing and graphics.
* [RHadoop](https://github.com/RevolutionAnalytics/RHadoop/wiki) including RHDFS, RHBase, RMR2, plyrmr
* [RHive](https://github.com/nexr/RHive) RHive, for launching Hive queries from R
* [Apache Lens](http://lens.apache.org/)
* [Apache SINGA (incubating)](https://singa.incubator.apache.org/) - SINGA is a general distributed deep learning platform for training big deep learning models over large datasets

## Misc.

* Hive Plugins
 * UDF
     * http://nexr.github.io/hive-udf/
     * https://github.com/edwardcapriolo/hive_cassandra_udfs
     * https://github.com/livingsocial/HiveSwarm
     * https://github.com/ThinkBigAnalytics/Hive-Extensions-from-Think-Big-Analytics
     * https://github.com/karthkk/udfs
     * https://github.com/twitter/elephant-bird - Twitter
     * https://github.com/lovelysystems/ls-hive
     * https://github.com/stewi2/hive-udfs
     * https://github.com/klout/brickhouse
     * https://github.com/markgrover/hive-translate (PostgreSQL translate())
     * https://github.com/deanwampler/HiveUDFs
     * https://github.com/myui/hivemall (Machine Learning UDF/UDAF/UDTF)
     * https://github.com/edwardcapriolo/hive-geoip (GeoIP UDF)
     * https://github.com/Netflix/Surus
 * Storage Handler
     * https://github.com/dvasilen/Hive-Cassandra
     * https://github.com/yc-huang/Hive-mongo
     * https://github.com/balshor/gdata-storagehandler
     * https://github.com/karthkk/hive-hbase-json
     * https://github.com/sunsuk7tp/hive-hbase-integration
     * https://bitbucket.org/rodrigopr/redisstoragehandler
     * https://github.com/zhuguangbin/HiveJDBCStorageHanlder
     * https://github.com/chimpler/hive-solr
     * https://github.com/bfemiano/accumulo-hive-storage-manager
 * SerDe
     * https://github.com/rcongiu/Hive-JSON-Serde
     * https://github.com/mochi/hive-json-serde
     * https://github.com/ogrodnek/csv-serde
     * https://github.com/parag/HiveJsonSerde
     * https://github.com/electrum/hive-serde - JSON
     * https://github.com/karthkk/hive-hbase-json
 * Libraries and tools
     * https://github.com/forward3d/rbhive
     * https://github.com/synctree/activerecord-hive-adapter
     * https://github.com/hrp/sequel-hive-adapter
     * https://github.com/forward/node-hive
     * https://github.com/recruitcojp/WebHive
     * [shib](https://github.com/tagomoris/shib) - WebUI for query engines: Hive and Presto
     * [clive](https://github.com/bmuller/clive) - Clojure library for interacting with Hive via Thrift
     * https://github.com/anjuke/hwi
     * https://code.google.com/a/apache-extras.org/p/hipy/
     * https://github.com/dmorel/Thrift-API-HiveClient2 (Perl - HiveServer2)
     * [PyHive](https://github.com/dropbox/PyHive) - Python interface to Hive and Presto
     * https://github.com/recruitcojp/OdbcHive
     * [Hive-Sharp](https://bitbucket.org/vadim/hive-sharp)
     * [HiveRunner](https://github.com/klarna/HiveRunner) - An Open Source unit test framework for hadoop hive queries based on JUnit4
     * [Beetest](https://github.com/kawaa/Beetest) - A super simple utility for testing Apache Hive scripts locally for non-Java developers.
     * [Hive_test](https://github.com/edwardcapriolo/hive_test)- Unit test framework for hive and hive-service
* Flume Plugins
 * [Flume MongoDB Sink](https://github.com/leonlee/flume-ng-mongodb-sink)
 * [Flume HornetQ Channel](https://github.com/btoddb/flume-ng-hornetq-channel)
 * [Flume MessagePack Source](https://github.com/leonlee/flume-ng-msgpack-source)
 * [Flume RabbitMQ source and sink](https://github.com/jcustenborder/flume-ng-rabbitmq)
 * [Flume UDP Source](https://github.com/whitepages/flume-udp-source)
 * [Stratio Ingestion](https://github.com/Stratio/Ingestion) - Custom sinks: Cassandra, MongoDB, Stratio Streaming and JDBC
 * [Flume Custom Serializers](https://github.com/relistan/flume-serializers)
 * [Real-time analytics in Apache Flume](https://github.com/jrkinley/flume-interceptor-analytics)
 * [.Net FlumeNG Clients](https://github.com/marksl/DotNetFlumeNG.Clients)

# Resources
Various resources, such as books, websites and articles.

## Websites
*Useful websites and articles*

* [Hadoop Weekly](http://www.hadoopweekly.com/)
* [The Hadoop Ecosystem Table](http://hadoopecosystemtable.github.io/)
* [Hadoop 1.x vs 2](http://www.slideshare.net/RommelGarcia2/hadoop-1x-vs-2)
* [Apache Hadoop YARN: Yet Another Resource Negotiator](http://www.socc2013.org/home/program/a5-vavilapalli.pdf)
* [Introducing Apache Hadoop YARN](http://hortonworks.com/blog/introducing-apache-hadoop-yarn/)
* [Apache Hadoop YARN - Background and an Overview](http://hortonworks.com/blog/apache-hadoop-yarn-background-and-an-overview/)
* [Apache Hadoop YARN - Concepts and Applications](http://hortonworks.com/blog/apache-hadoop-yarn-concepts-and-applications/)
* [Apache Hadoop YARN - ResourceManager](http://hortonworks.com/blog/apache-hadoop-yarn-resourcemanager/)
* [Apache Hadoop YARN - NodeManager](http://hortonworks.com/blog/apache-hadoop-yarn-nodemanager/)
* [Migrating to MapReduce 2 on YARN (For Users)](http://blog.cloudera.com/blog/2013/11/migrating-to-mapreduce-2-on-yarn-for-users/)
* [Migrating to MapReduce 2 on YARN (For Operators)](http://blog.cloudera.com/blog/2013/11/migrating-to-mapreduce-2-on-yarn-for-operators/)
* [Hadoop and Big Data: Use Cases at Salesforce.com](https://developer.salesforce.com/blogs/engineering/2013/03/hadoop-use-cases-at-salesforce-com.html)
* [All you wanted to know about Hadoop, but were too afraid to ask: genealogy of elephants.](https://blogs.apache.org/bigtop/entry/all_you_wanted_to_know)
* [What is Bigtop, and Why Should You Care?](https://blogs.apache.org/bigtop/entry/bigtop_and_why_should_you)
* [Hadoop - Distributions and Commercial Support](http://wiki.apache.org/hadoop/Distributions%20and%20Commercial%20Support)
* [Ganglia configuration for a small Hadoop cluster and some troubleshooting](http://hakunamapdata.com/ganglia-configuration-for-a-small-hadoop-cluster-and-some-troubleshooting/)
* [Hadoop illuminated](http://hadoopilluminated.com/) - Open Source Hadoop Book
* [NoSQL Database](http://nosql-database.org/)
* [10 Best Practices for Apache Hive](https://www.qubole.com/blog/big-data/hive-best-practices/)
* [Hadoop Operations at Scale](http://hortonworks.com/blog/apache-hadoop-operations-scale/)
* [AWS BigData Blog](http://blogs.aws.amazon.com/bigdata/)
* [Hadoop360](http://www.hadoop360.com/)
* [How to monitor Hadoop metrics](https://www.datadoghq.com/blog/monitor-hadoop-metrics/)

## Presentations

* [Hadoop Summit Presentations](http://www.slideshare.net/Hadoop_Summit) - Slide decks from Hadoop Summit
* [Hadoop 24/7](http://www.slideshare.net/allenwittenauer/aw-apachecon2009-15342917)
* [An example Apache Hadoop Yarn upgrade](http://www.slideshare.net/mikejf12/an-example-apache-hadoop-yarn-upgrade)
* [Apache Hadoop In Theory And Practice](http://www.slideshare.net/AdamKawa/hadoop-intheoryandpractice)
* [Hadoop Operations at LinkedIn](http://www.slideshare.net/allenwittenauer/2013-hadoopsummitemea)
* [Hadoop Performance at LinkedIn](http://www.slideshare.net/allenwittenauer/2012-lihadoopperf)
* [Docker based Hadoop provisioning](http://www.slideshare.net/JanosMatyas/docker-based-hadoop-provisioning)

## Books

* [Hadoop: The Definitive Guide](http://www.amazon.com/gp/product/1449311520/ref=as_li_ss_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=1449311520&linkCode=as2&tag=matratsblo-20)
* [Hadoop Operations](http://www.amazon.com/gp/product/1449327052/ref=as_li_ss_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=1449327052&linkCode=as2&tag=matratsblo-20)
* [Apache Hadoop Yarn](http://www.amazon.com/dp/0321934504?tag=matratsblo-20)
* [HBase: The Definitive Guide](http://shop.oreilly.com/product/0636920014348.do)
* [Programming Pig](http://shop.oreilly.com/product/0636920018087.do)
* [Programming Hive](http://shop.oreilly.com/product/0636920023555.do)
* [Hadoop in Practice, Second Edition](http://www.manning.com/holmes2/)
* [Hadoop in Action, Second Edition](http://www.manning.com/lam2/)

## Hadoop and Big Data Events
* [ApacheCon](http://www.apachecon.com/)
* [Strata + Hadoop World](http://conferences.oreilly.com/strata)
* [Hadoop Summit](http://hadoopsummit.org/)

# Other Awesome Lists
Other amazingly awesome lists can be found in the [awesome-awesomeness](https://github.com/bayandin/awesome-awesomeness) and [awesome](https://github.com/sindresorhus/awesome) list.
