

JVM启动参数配置
=============
>  

> jps - Java Virtual Machine Process Status Tool


## mo gu jie

JVM应用实例启动参数
```
$ jps -lmv
28597 org.apache.catalina.startup.Bootstrap -Djboss.server.home.dir=/home/mapp/mogulive/.default -Djboss.server.home.url=file:/home/mapp/mogulive/.default start 
-Djava.util.logging.config.file=/home/mapp/mogulive/.default/conf/logging.properties -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager 
-Xms4g -Xmx4g -XX:PermSize=96m -XX:MaxPermSize=256m -Xmn2g -XX:SurvivorRatio=10 
-XX:+UseConcMarkSweepGC -XX:+UseCMSCompactAtFullCollection -XX:CMSMaxAbortablePrecleanTime=5000 -XX:+CMSClassUnloadingEnabled -XX:CMSInitiatingOccupancyFraction=80 -XX:+DisableExplicitGC 
-verbose:gc -Xloggc:/home/mapp/logs/gc.log -XX:+PrintGCDetails -XX:+PrintGCDateStamps 
-XX:+UseCompressedOops -Djava.awt.headless=true 
-XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=/home/mapp/logs/java.hprof 
-XX:MaxDirectMemorySize=1g -XX:+UseCMSInitiatingOccupancyOnly -XX:+ExplicitGCInvokesConcurrent 
-Dsun.rmi.dgc.server.gcInterval=2592000000 -Dsun.rmi.dgc.client.gcInterval=2592000000 
-Dsun.net.client.defaultConnectTimeout=10000 -Dsun.net.client.defaultReadTimeout=30000 
-XX:-OmitStackTraceInFastThrow -Dproject.name=mogulive 
-Djava.endorsed.dirs=/usr/local/tomcat/endorsed -Dcatalina.base=/home/map
```

参数选项含义
```
# Tomcat启动引导程序
28597 org.apache.catalina.startup.Bootstrap -Djboss.server.home.dir=/home/mapp/mogulive/.default -Djboss.server.home.url=file:/home/mapp/mogulive/.default start 
# 日志
-Djava.util.logging.config.file=/home/mapp/mogulive/.default/conf/logging.properties -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager 
# 堆空间，年轻代
-Xms4g -Xmx4g -XX:PermSize=96m -XX:MaxPermSize=256m -Xmn2g -XX:SurvivorRatio=10 
# GC垃圾收集器，CMS垃圾回收算法
-XX:+UseConcMarkSweepGC -XX:+UseCMSCompactAtFullCollection -XX:CMSMaxAbortablePrecleanTime=5000 -XX:+CMSClassUnloadingEnabled -XX:CMSInitiatingOccupancyFraction=80 -XX:+DisableExplicitGC 
# GC日志
-verbose:gc -Xloggc:/home/mapp/logs/gc.log -XX:+PrintGCDetails -XX:+PrintGCDateStamps 
-XX:+UseCompressedOops -Djava.awt.headless=true 
# OOM内存溢出时转储堆空间内存数据
-XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=/home/mapp/logs/java.hprof 
# 最大对外内存大小
-XX:MaxDirectMemorySize=1g -XX:+UseCMSInitiatingOccupancyOnly -XX:+ExplicitGCInvokesConcurrent 
-Dsun.rmi.dgc.server.gcInterval=2592000000 -Dsun.rmi.dgc.client.gcInterval=2592000000 
# 网络客户端连接超时与处理请求读超时的默认值
-Dsun.net.client.defaultConnectTimeout=10000 -Dsun.net.client.defaultReadTimeout=30000 
-XX:-OmitStackTraceInFastThrow -Dproject.name=mogulive 
# Tomcat参数选项
-Djava.endorsed.dirs=/usr/local/tomcat/endorsed -Dcatalina.base=/home/map
```

GC日志文件首行输出的所有JVM参数
```
Java HotSpot(TM) 64-Bit Server VM (25.72-b15) for linux-amd64 JRE (1.8.0_72-b15), built on Dec 22 2015 22:00:07 by "java_re" with gcc 4.3.0 20080428 (Red Hat 4.3.0-8)
Memory: 4k page, physical 8059152k(4496156k free), swap 0k(0k free)
CommandLine flags: -XX:+CMSClassUnloadingEnabled -XX:CMSInitiatingOccupancyFraction=80 -XX:CMSMaxAbortablePrecleanTime=5000 -XX:+CMSParallelRemarkEnabled -XX:+CMSScavengeBeforeRemark -XX:+ExplicitGCInvokesConcurrent 
-XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=/home/mapp/logs/java.hprof 
-XX:InitialCodeCacheSize=134217728 -XX:InitialHeapSize=4294967296 -XX:MaxDirectMemorySize=1073741824 -XX:MaxHeapSize=4294967296 -XX:MaxMetaspaceSize=268435456 -XX:MaxNewSize=2147483648 -XX:MetaspaceSize=268435456 -XX:NewSize=2147483648 -XX:OldPLABSize=16 
-XX:+PrintGC -XX:+PrintGCDateStamps -XX:+PrintGCDetails -XX:+PrintGCTimeStamps 
-XX:ReservedCodeCacheSize=268435456 -XX:SurvivorRatio=10 
-XX:+UseCMSCompactAtFullCollection -XX:+UseCMSInitiatingOccupancyOnly -XX:+UseCompressedClassPointers -XX:+UseCompressedOops -XX:+UseConcMarkSweepGC -XX:+UseParNewGC
```


## wa cai
> Spring Boot应用JAR包

JVM应用实例启动参数
```
$ jps -lmv
26477 ./lib/magnum-provider-0.14.0.jar 
-verbose:gc -Xloggc:/data/program/com.xxx.loan/magnum-provider/0.14.0/gc_log/gc.log -XX:+PrintGCDetails -XX:+PrintGCDateStamps -XX:+UseGCLogFileRotation -XX:NumberOfGCLogFiles=20 -XX:GCLogFileSize=50m 
-XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=/data/program/com.xxx.loan/magnum-provider/0.14.0/java.hprof 
-XX:ErrorFile=/data/program/com.xxx.loan/magnum-provider/0.14.0/java_error.log -Djava.awt.headless=true 
-Djava.security.egd=file:/dev/./urandom 
-DLOG_HOME=/data/program/logs/com.xxx.loan/magnum-provider/app_log -Dapp.log.dir=/data/program/logs/com.xxx.loan/magnum-provider/app_log 
-Dserver.tomcat.access-log-enabled=true -Dserver.tomcat.basedir=/data/program/com.xxx.loan/magnum-provider 
-Dmanagement.port=-1 -Dendpoints.shutdown.enabled=true -Dshell.telnet.enabled=false -Dcom.sun.management.jmxremote.authenticate=false -Dcom.sun.management.jmxremote.ssl=false 
-Xms2g -Xmx2g -XX:MetaspaceSize=38m -XX:MaxMetaspaceSize=380m -XX:NewSize=600m -XX:MaxNewSize=750m 
-XX:+UseConcMarkSweepGC -XX:CMSMaxAbort
```

参数选项含义
```
# Spring Boot应用JAR包
26477 ./lib/magnum-provider-0.14.0.jar 
# GC日志
-verbose:gc -Xloggc:/data/program/com.xxx.loan/magnum-provider/0.14.0/gc_log/gc.log -XX:+PrintGCDetails -XX:+PrintGCDateStamps -XX:+UseGCLogFileRotation -XX:NumberOfGCLogFiles=20 -XX:GCLogFileSize=50m 
# OOM内存溢出时转储堆空间内存数据
-XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=/data/program/com.xxx.loan/magnum-provider/0.14.0/java.hprof 
# JVM发送错误时输出的现场状态数据文件
-XX:ErrorFile=/data/program/com.xxx.loan/magnum-provider/0.14.0/java_error.log -Djava.awt.headless=true 
# 安全的随机数
-Djava.security.egd=file:/dev/./urandom 
# 应用日志
-DLOG_HOME=/data/program/logs/com.xxx.loan/magnum-provider/app_log -Dapp.log.dir=/data/program/logs/com.xxx.loan/magnum-provider/app_log 
# Tomcat参数选项
-Dserver.tomcat.access-log-enabled=true -Dserver.tomcat.basedir=/data/program/com.xxx.loan/magnum-provider 
# 应用安全方面配置
-Dmanagement.port=-1 -Dendpoints.shutdown.enabled=true -Dshell.telnet.enabled=false -Dcom.sun.management.jmxremote.authenticate=false -Dcom.sun.management.jmxremote.ssl=false 
# 堆空间，元数据区，新生代
-Xms2g -Xmx2g -XX:MetaspaceSize=38m -XX:MaxMetaspaceSize=380m -XX:NewSize=600m -XX:MaxNewSize=750m 
# GC垃圾收集器，CMS垃圾回收算法
-XX:+UseConcMarkSweepGC -XX:CMSMaxAbort
```

GC日志文件首行输出的所有JVM参数
```
Java HotSpot(TM) 64-Bit Server VM (25.121-b13) for linux-amd64 JRE (1.8.0_121-b13), built on Dec 12 2016 16:36:53 by "java_re" with gcc 4.3.0 20080428 (Red Hat 4.3.0-8)
Memory: 4k page, physical 4054300k(2710012k free), swap 1015804k(1011872k free)
CommandLine flags: -XX:+CMSClassUnloadingEnabled -XX:CMSInitiatingOccupancyFraction=80 -XX:CMSMaxAbortablePrecleanTime=5000 
-XX:ErrorFile=/data/program/com.xxx.loan/magnum-provider/0.14.0/java_error.log -XX:GCLogFileSize=52428800 
-XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=/data/program/com.xxx.loan/magnum-provider/0.14.0/java.hprof 
-XX:InitialHeapSize=2147483648 -XX:+ManagementServer -XX:MaxHeapSize=2147483648 -XX:MaxMetaspaceSize=398458880 -XX:MaxNewSize=786432000 -XX:MaxTenuringThreshold=6 -XX:MetaspaceSize=39845888 -XX:NewSize=629145600 
-XX:NumberOfGCLogFiles=20 -XX:OldPLABSize=16 
-XX:+PrintGC -XX:+PrintGCDateStamps -XX:+PrintGCDetails -XX:+PrintGCTimeStamps -XX:+UseCMSInitiatingOccupancyOnly 
-XX:+UseCompressedClassPointers -XX:+UseCompressedOops 
-XX:+UseConcMarkSweepGC -XX:+UseGCLogFileRotation -XX:+UseParNewGC 
```

