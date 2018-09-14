

ZooKeeper客户端连接到ZK服务器的日志剖析
=========================


## 1. 本地环境

```java
# 通过 zkCli.sh 连接到ZK服务器（localhost:2181）
➜  ~ /usr/local/zookeeper-3.4/bin/zkCli.sh -server localhost:2181
# 连接到ZK服务器中
Connecting to localhost:2181
# ZooKeeper主线程（main）
# 客户端环境信息（Environment@100）
## 客户端ZooKeeper版本（zookeeper-3.4.9）
2018-09-14 22:49:37,480 [myid:] - INFO  [main:Environment@100] - Client environment:zookeeper.version=3.4.9-1757313, built on 08/23/2016 06:50 GMT
## 客户端主机名（192.168.1.4）
2018-09-14 22:49:37,492 [myid:] - INFO  [main:Environment@100] - Client environment:host.name=192.168.1.4
## JDK信息
### Java版本（jdk-1.8.0_112）
2018-09-14 22:49:37,492 [myid:] - INFO  [main:Environment@100] - Client environment:java.version=1.8.0_112
2018-09-14 22:49:37,494 [myid:] - INFO  [main:Environment@100] - Client environment:java.vendor=Oracle Corporation
### Java主目录
2018-09-14 22:49:37,495 [myid:] - INFO  [main:Environment@100] - Client environment:java.home=/Library/Java/JavaVirtualMachines/jdk1.8.0_112.jdk/Contents/Home/jre
### Java类路径
2018-09-14 22:49:37,495 [myid:] - INFO  [main:Environment@100] - Client environment:java.class.path=/usr/local/zookeeper-3.4/bin/../build/classes:/usr/local/zookeeper-3.4/bin/../build/lib/*.jar:/usr/local/zookeeper-3.4/bin/../lib/slf4j-log4j12-1.6.1.jar:/usr/local/zookeeper-3.4/bin/../lib/slf4j-api-1.6.1.jar:/usr/local/zookeeper-3.4/bin/../lib/netty-3.10.5.Final.jar:/usr/local/zookeeper-3.4/bin/../lib/log4j-1.2.16.jar:/usr/local/zookeeper-3.4/bin/../lib/jline-0.9.94.jar:/usr/local/zookeeper-3.4/bin/../zookeeper-3.4.9.jar:/usr/local/zookeeper-3.4/bin/../src/java/lib/*.jar:/usr/local/zookeeper-3.4/bin/../conf:
### Java库路径
2018-09-14 22:49:37,495 [myid:] - INFO  [main:Environment@100] - Client environment:java.library.path=/Users/dannong/Library/Java/Extensions:/Library/Java/Extensions:/Network/Library/Java/Extensions:/System/Library/Java/Extensions:/usr/lib/java:.
### Java I/O临时目录
2018-09-14 22:49:37,495 [myid:] - INFO  [main:Environment@100] - Client environment:java.io.tmpdir=/var/folders/0y/kzmh046n3bqb07pwdrq_zy_r0000gn/T/
2018-09-14 22:49:37,495 [myid:] - INFO  [main:Environment@100] - Client environment:java.compiler=<NA>
## 操作系统信息
2018-09-14 22:49:37,499 [myid:] - INFO  [main:Environment@100] - Client environment:os.name=Mac OS X
2018-09-14 22:49:37,499 [myid:] - INFO  [main:Environment@100] - Client environment:os.arch=x86_64
2018-09-14 22:49:37,499 [myid:] - INFO  [main:Environment@100] - Client environment:os.version=10.12
## 用户信息
2018-09-14 22:49:37,499 [myid:] - INFO  [main:Environment@100] - Client environment:user.name=dannong
2018-09-14 22:49:37,499 [myid:] - INFO  [main:Environment@100] - Client environment:user.home=/Users/dannong
2018-09-14 22:49:37,500 [myid:] - INFO  [main:Environment@100] - Client environment:user.dir=/Users/dannong
# ZooKeeper实例（ZooKeeper@438）
## 启动客户端连接(服务地址，连接超时时间，状态与事件监视器)（connectString=localhost:2181 sessionTimeout=30000 watcher=ZooKeeperMain$MyWatcher@4459eb14）
2018-09-14 22:49:37,501 [myid:] - INFO  [main:ZooKeeper@438] - Initiating client connection, connectString=localhost:2181 sessionTimeout=30000 watcher=org.apache.zookeeper.ZooKeeperMain$MyWatcher@4459eb14
Welcome to ZooKeeper!
# 客户端消息发送线程（main-SendThread(localhost:2181)）
## 打开与服务器(localhost/127.0.0.1:2181)的套接字连接
2018-09-14 22:49:37,536 [myid:] - INFO  [main-SendThread(localhost:2181):ClientCnxn$SendThread@1032] - Opening socket connection to server localhost/127.0.0.1:2181. Will not attempt to authenticate using SASL (unknown error)
JLine support is enabled
## 已建立到服务器的套接字连接，启动会话
2018-09-14 22:49:37,658 [myid:] - INFO  [main-SendThread(localhost:2181):ClientCnxn$SendThread@876] - Socket connection established to localhost/127.0.0.1:2181, initiating session
## 会话在服务器上建立完成，会话ID(sessionid = 0x16583ade44f0038)，协商超时时间(negotiated timeout = 30000)
2018-09-14 22:49:37,682 [myid:] - INFO  [main-SendThread(localhost:2181):ClientCnxn$SendThread@1299] - Session establishment complete on server localhost/127.0.0.1:2181, sessionid = 0x16583ade44f0038, negotiated timeout = 30000

# 状态与事件监视器
WATCHER::

## 监视的状态事件(SyncConnected)
WatchedEvent state:SyncConnected type:None path:null
[zk: localhost:2181(CONNECTED) 0] ls /
[cells, zookeeper, dubbo_test]
[zk: localhost:2181(CONNECTED) 1] quit
# 退出中
Quitting...
# ZooKeeper主线程（main）
## 会话已关闭（会话ID：0x16583ade44f0038）
2018-09-14 22:49:43,580 [myid:] - INFO  [main:ZooKeeper@684] - Session: 0x16583ade44f0038 closed
# 事件处理线程（main-EventThread）
## 事件处理线程关闭会话（会话ID：0x16583ade44f0038）
2018-09-14 22:49:43,583 [myid:] - INFO  [main-EventThread:ClientCnxn$EventThread@519] - EventThread shut down for session: 0x16583ade44f0038
```

ZooKeeper客户端线程模型：ZooKeeper主线程（main），客户端消息发送线程（main-SendThread(localhost:2181)），事件处理线程（main-EventThread）


## 2. 生产环境

```java
# 通过 zkCli.sh 连接到ZK服务器
[dannong@jumper-160-105-hzqsh 01:37:03 ~]$ zookeeper-3.4.11/bin/zkCli.sh -server zkserver1.xxx.info:12181
# 连接到ZK服务器中
Connecting to zkserver1.xxx.info:12181
# ZooKeeper主线程（main）
# 客户端环境信息（Environment@100）
## 客户端ZooKeeper版本（zookeeper-3.4.11）
2018-09-15 01:37:07,632 [myid:] - INFO  [main:Environment@100] - Client environment:zookeeper.version=3.4.11-37e277162d567b55a07d1755f0b31c32e93c01a0, built on 11/01/2017 18:06 GMT
## 客户端主机名
2018-09-15 01:37:07,637 [myid:] - INFO  [main:Environment@100] - Client environment:host.name=jumper-160-105-hzqsh.node.hzqsh.xxx.sdc
## JDK信息
### Java版本（jdk-1.8.0_45）
2018-09-15 01:37:07,637 [myid:] - INFO  [main:Environment@100] - Client environment:java.version=1.8.0_45
2018-09-15 01:37:07,640 [myid:] - INFO  [main:Environment@100] - Client environment:java.vendor=Oracle Corporation
### Java主目录
2018-09-15 01:37:07,640 [myid:] - INFO  [main:Environment@100] - Client environment:java.home=/data/program/java8/jre
### Java类路径
2018-09-15 01:37:07,640 [myid:] - INFO  [main:Environment@100] - Client environment:java.class.path=/home/dannong/zookeeper-3.4.11/bin/../build/classes:/home/dannong/zookeeper-3.4.11/bin/../build/lib/*.jar:/home/dannong/zookeeper-3.4.11/bin/../lib/slf4j-log4j12-1.6.1.jar:/home/dannong/zookeeper-3.4.11/bin/../lib/slf4j-api-1.6.1.jar:/home/dannong/zookeeper-3.4.11/bin/../lib/netty-3.10.5.Final.jar:/home/dannong/zookeeper-3.4.11/bin/../lib/log4j-1.2.16.jar:/home/dannong/zookeeper-3.4.11/bin/../lib/jline-0.9.94.jar:/home/dannong/zookeeper-3.4.11/bin/../lib/audience-annotations-0.5.0.jar:/home/dannong/zookeeper-3.4.11/bin/../zookeeper-3.4.11.jar:/home/dannong/zookeeper-3.4.11/bin/../src/java/lib/*.jar:/home/dannong/zookeeper-3.4.11/bin/../conf:
### Java库路径
2018-09-15 01:37:07,640 [myid:] - INFO  [main:Environment@100] - Client environment:java.library.path=/usr/java/packages/lib/amd64:/usr/lib64:/lib64:/lib:/usr/lib
### Java I/O临时目录
2018-09-15 01:37:07,640 [myid:] - INFO  [main:Environment@100] - Client environment:java.io.tmpdir=/tmp
2018-09-15 01:37:07,640 [myid:] - INFO  [main:Environment@100] - Client environment:java.compiler=<NA>
## 操作系统信息
2018-09-15 01:37:07,640 [myid:] - INFO  [main:Environment@100] - Client environment:os.name=Linux
2018-09-15 01:37:07,641 [myid:] - INFO  [main:Environment@100] - Client environment:os.arch=amd64
2018-09-15 01:37:07,641 [myid:] - INFO  [main:Environment@100] - Client environment:os.version=2.6.32-642.6.2.el6.x86_64
## 用户信息
2018-09-15 01:37:07,641 [myid:] - INFO  [main:Environment@100] - Client environment:user.name=dannong
2018-09-15 01:37:07,641 [myid:] - INFO  [main:Environment@100] - Client environment:user.home=/home/dannong/
2018-09-15 01:37:07,641 [myid:] - INFO  [main:Environment@100] - Client environment:user.dir=/home/dannong
# ZooKeeper实例（ZooKeeper@441）
## 启动客户端连接(服务地址，连接超时时间，状态与事件监视器)（connectString=zkserver1.xxx.info:12181 sessionTimeout=30000 watcher=ZooKeeperMain$MyWatcher@7aec35a）
2018-09-15 01:37:07,643 [myid:] - INFO  [main:ZooKeeper@441] - Initiating client connection, connectString=zkserver1.xxx.info:12181 sessionTimeout=30000 watcher=org.apache.zookeeper.ZooKeeperMain$MyWatcher@7aec35a
Welcome to ZooKeeper!
JLine support is enabled
# 客户端消息发送线程（main-SendThread(zk-160-17-hzqsh.node.hzqsh.xxx.sdc:12181)）
## 打开与服务器(zk-160-17-hzqsh.node.hzqsh.xxx.sdc/10.1.160.17:12181)的套接字连接
2018-09-15 01:37:07,681 [myid:] - INFO  [main-SendThread(zk-160-17-hzqsh.node.hzqsh.xxx.sdc:12181):ClientCnxn$SendThread@1035] - Opening socket connection to server zk-160-17-hzqsh.node.hzqsh.xxx.sdc/10.1.160.17:12181. Will not attempt to authenticate using SASL (unknown error)
## 已建立到服务器的套接字连接，启动会话
2018-09-15 01:37:07,775 [myid:] - INFO  [main-SendThread(zk-160-17-hzqsh.node.hzqsh.xxx.sdc:12181):ClientCnxn$SendThread@877] - Socket connection established to zk-160-17-hzqsh.node.hzqsh.xxx.sdc/10.1.160.17:12181, initiating session
## 会话在服务器上建立完成，会话ID(sessionid = 0xa0b6cdc896826e6)，协商超时时间(negotiated timeout = 30000)
2018-09-15 01:37:07,785 [myid:] - INFO  [main-SendThread(zk-160-17-hzqsh.node.hzqsh.xxx.sdc:12181):ClientCnxn$SendThread@1302] - Session establishment complete on server zk-160-17-hzqsh.node.hzqsh.xxx.sdc/10.1.160.17:12181, sessionid = 0xa0b6cdc896826e6, negotiated timeout = 30000

# 状态与事件监视器
WATCHER::

## 监视的状态事件(SyncConnected)
WatchedEvent state:SyncConnected type:None path:null
[zk: zkserver1.xxx.info:12181(CONNECTED) 0] ls /
[dubbo_test, zipkin, zookeeper, cells]
[zk: zkserver1.xxx.info:12181(CONNECTED) 1] quit
# 退出中
Quitting...
# ZooKeeper主线程（main）
## 会话已关闭（会话ID：0xa0b6cdc896826e6）
2018-09-15 01:37:14,324 [myid:] - INFO  [main:ZooKeeper@687] - Session: 0xa0b6cdc896826e6 closed
# 事件处理线程（main-EventThread）
## 事件处理线程关闭会话（会话ID：0xa0b6cdc896826e6）
2018-09-15 01:37:14,327 [myid:] - INFO  [main-EventThread:ClientCnxn$EventThread@520] - EventThread shut down for session: 0xa0b6cdc896826e6
```

ZooKeeper客户端线程模型：ZooKeeper主线程（main），客户端消息发送线程（main-SendThread(zk-160-17-hzqsh.node.hzqsh.xxx.sdc:12181)），事件处理线程（main-EventThread）

