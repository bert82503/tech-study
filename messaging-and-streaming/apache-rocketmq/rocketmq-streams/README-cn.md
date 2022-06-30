

RocketMQ Streams
======
> https://github.com/apache/rocketmq-streams/blob/main/README-chinese.md


# Features
* 轻量级部署：可以单独部署，也支持集群部署
* 多种类型的数据输入以及输出


# Architecture
* 整体架构： 介绍RocketMQ-streams总体构成
* 构建拓扑图： 介绍如何通过DataStream将各个算子添加进入计算拓扑
* 启动：介绍计算拓扑图如何启动，消费数据流入之前需要做哪些准备工作
* 数据的流转：介绍数据进入计算拓扑的流转过程，以及各种系统消息的作用原理
* Window算子解析： 介绍有状态算子window实例化、数据处理、窗口触发过程


# Core API
rocketmq-stream 实现了一系列高级的API，可以让用户很方便地编写流计算的程序，实现自己的业务需求。

### StreamBuilder
StreamBuilder 用于构建流任务的源

* dataStream(nameSpaceName, pipelineName) 返回DataStreamSource实例，用于分段编程实现流计算任务

### DataStream API
#### Source
DataStreamSource 是分段式编程的源头类，用于对接各种数据源，从各大消息队列中获取数据；

#### transform
transform 允许在流计算过程中对输入源的数据进行修改，进行下一步的操作；
DataStream API中包括DataStream, JoinStream, SplitStream, WindowStream等多个transform类；

DataStream实现了一系列常见的流计算算子

#### Strategy
策略机制主要用来控制计算引擎运行过程中的底层逻辑，如window存储方式，后续还会增加对state、双流join等的控制；
所有的控制策略通过with算子传入，可以同时传入多个策略类型；

