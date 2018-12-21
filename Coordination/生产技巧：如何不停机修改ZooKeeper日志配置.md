

生产技巧：如何不停机修改ZooKeeper日志配置
=========================
> 周立，2018.11.30

偶然看到2017年8月写的**工作日志**，希望对大家的工作有参考价值。

由于`Kafka集群`的运维兄弟没对线上环境ZooKeeper做处理，
因此`zookeeper.out文件会不断增大，没几天时间，文件已经有6G。`【问题】
故而需要做一些改进，避免这种情况。


### 准备工作

**需注意，如果ZooKeeper集群只有3个实例，那么日志修改务必先修改`follower节点`的配置，再修改`leader节点`的配置，
否则可能会`导致问题`。**


### 修改日志

下面我们来修改日志输出：

1、修改`conf/log4j.properties`，找到：
```
# Define some default values that can be overridden by system properties
zookeeper.root.logger=INFO, CONSOLE
```
改为：
```properties
# Define some default values that can be overridden by system properties
zookeeper.root.logger=INFO, ROLLINGFILE
```

2、修改`bin/zkEnv.sh`，找到：
```
if [ "x${ZOO_LOG4J_PROP}" = "x" ]
then
    ZOO_LOG4J_PROP="INFO,CONSOLE"
fi
```
改为：
```
if [ "x${ZOO_LOG4J_PROP}" = "x" ]
then
    ZOO_LOG4J_PROP="INFO,ROLLINGFILE"
fi
```


**注意：建议在最后修改`leader节点`，避免修改日志中途有额外的`选举操作`，影响线上性能。**


### 参考文档
* [ZooKeeper在线迁移](https://blog.csdn.net/lirenzuo/article/details/71080063)


[原文](http://www.itmuch.com/work/change-zk-log-dir/)

