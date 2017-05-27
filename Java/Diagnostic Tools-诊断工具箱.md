
### Java在线问题诊断工具
#### [Greys](https://github.com/oldmanpushcart/greys-anatomy)
```
线上系统为何经常出错？数据库为何屡遭黑手？
业务调用为何频频失败？连环异常堆栈案，究竟是哪次调用所为？
数百台服务器意外雪崩背后又隐藏着什么？是软件的扭曲还是硬件的沦丧？
走进科学带你了解Greys，Java线上问题诊断工具。
```

Greys是一个JVM进程执行过程中的异常诊断工具，可以在`不中断程序执行`的情况下轻松完成JVM相关问题排查工作。

##### 目标群体
* 有时候突然一个问题反馈上来，需要`入参`才能完成定位，但恰恰没有任何日志。回去加上重新部署，一杯咖啡时间过去了，是不是很崩溃？
* 当你经过反复这样几次折腾之后变得聪明了，在代码的所有入参和出参的地方都加上debug日志，但这次问题似乎暴露在`别人的代码`中了...是不是很无奈？
* 突然遇到线上一个`性能问题`无法确定到底是`哪个环节的耗时`，只能反复抓jstack猜，还有没有办法可以好好的过日子啦？

遇到以上问题时，你就是我们这类工具的目标客户，此类工具能利用Java 6的`Instrumentation特性，动态增强你所指定的类`，获取你想要到的信息。

##### 特点
* ClassLoader隔离
```
隔离目标类与Greys的ClassLoader，可以放心大胆地使用，不会干扰到现有业务代码所使用的三方类库。
```
* 运行时加载，无需重启JVM进行CT式诊断
* 常见问题定位命令化
```
Greys与BTrace、HouseMD等同类软件最大的不同在于，她拥有我多年来业务代码疑难杂症定位的常用技术手段，并将这些排查思路和技巧命令化，将我的问题定位经验Share给大家。
```
* OGNL表达式展开变量、过滤条件（方便查看`入参、出参、异常、当前对象的各种属性细节`）
```
Greys最有利的武器是她的Groovy表达式，能让你在感受到HouseMD集成功能便利的同时，也能发挥出自定义BTrace脚本的灵活。
```
* 多用户同时访问
```
Greys采用的思路是做观察者，其所设置的断点不允许阻塞正常业务的流程，但你可以观察到断点所拦截到的所有信息。
```
* 高性能
```
精心用ASM设计了字节码增强，核心的数据结构用数组针对实际场景做裁剪优化。可以放心地用在高负载要求下的JVM环境。
```
* 常用分析命令集成，`monitor、trace、ptrace`等
```
作者将5年来对线上业务问题定位的经验浓缩到了这几个命令中，希望这些经验积累能帮助到更多的人。
```
* 时间隧道，`tt`命令能以时间维度纪录下监控期内的每一次调用状态
* 多人并行协作
```
能让多人同时远程到同一进程上执行不同的指令、脚本，非常适合团队一起进行线上问题排查与跟踪。
```

Greys定位是`专业的JVM的业务问题定位工具`。

##### 不适合的场景
Greys并不万能，我也没有计划让她能成为万能的问题定位工具。所以如果你在某些场合能用上更专业的工具，我会非常乐意推荐你使用。
* 性能环境下的`性能损耗定位`
```
性能分析需要有更专业的软件，我自己常用的则是JProfiler。Greys虽然性能损耗很小，但其分析的维度太少，所以只适合做简单的性能损耗定位。当你用过专业的性能分析软件之后，就会发现什么叫专业！
```
* 开发环境下的远程Debug
* 线上环境大规模部署
```
与BTrace一样，Greys获取到的权限太高，如果线上大规模部署会遭受黑客的攻击，而今天我为了实现简单是没有做过多的鉴权控制。
```
* JDK类库分析
* 其它不适合场景
```
BTrace、HouseMD、Greys、JavOSize此类工具都会对Perm区、CodeCache（影响JIT）产生干扰，如果你的程序对这两块非常敏感，也请不要在这些场合下使用。
```

座右铭：让程序解决繁琐的事情

##### 内置功能
* 查看已加载的类、方法信息
* `方法执行`监控（`调用量、成功失败率、响应时间`）
* `方法执行数据观测、记录与回放`（`入参、返回值、异常信息`）
* `方法性能`开销渲染（`跟踪指定路径中的方法调用轨迹、耗时`）
* 查看方法调用堆栈

##### 安装
```
curl -sLk http://ompc.oss.aliyuncs.com/greys/install.sh | sh
```

[FAQ-常见问题答疑](https://github.com/oldmanpushcart/greys-anatomy/wiki/FAQ)

[快速入门](https://github.com/oldmanpushcart/greys-anatomy/wiki/Getting-Started)
##### 启动
```
jps -lmv

./greys.sh <PID>[@IP:PORT]
```

##### [重要命令](https://github.com/oldmanpushcart/greys-anatomy/wiki/greys-pdf#greys%E5%91%BD%E4%BB%A4%E8%AF%A6%E8%A7%A3)
help：查看命令的帮助文档，每个命令和参数都有很详细的说明
```
help
+----------+----------------------------------------------------------------------------------+
|       sc | Search all the classes loaded by JVM                                             |
+----------+----------------------------------------------------------------------------------+
|       sm | Search the method of classes loaded by JVM                                       |
+----------+----------------------------------------------------------------------------------+
|  monitor | Monitor the execution of specified Class and its method (方法执行监控)             |
+----------+----------------------------------------------------------------------------------+
|    watch | Display the details of specified class and method (方法执行数据观测)                |
+----------+----------------------------------------------------------------------------------+
|       tt | Time Tunnel (方法执行数据的时间隧道，记录下指定方法每次调用的入参和返回信息，并能对这些不同的时间下调用进行观测) |
+----------+----------------------------------------------------------------------------------+
|    stack | Display the stack trace of specified class and method (输出当前方法被调用的调用路径)  |
+----------+----------------------------------------------------------------------------------+
|   ptrace | Display the detailed thread path stack of specified class and method (强化版的trace命令。通过指定渲染路径，并可记录路径中所有方法的入参、返回值；与tt命令联动) |
+----------+----------------------------------------------------------------------------------+
|       js | Enhanced JavaScript                                                              |
+----------+----------------------------------------------------------------------------------+
|    trace | Display the detailed thread stack of specified class and method (渲染方法内部调用路径，并输出方法路径上的每个节点上耗时) |
+----------+----------------------------------------------------------------------------------+
|  session | Display current session information                                              |
+----------+----------------------------------------------------------------------------------+
|     quit | Quit Greys console (退出Greys客户端)                                               |
+----------+----------------------------------------------------------------------------------+
|  version | Display Greys version                                                            |
+----------+----------------------------------------------------------------------------------+
|      jvm | Display the target JVM information (查看当前JVM的信息)                              |
+----------+----------------------------------------------------------------------------------+
|    reset | Reset all the enhanced classes (重置增强类，将被Greys增强过的类全部还原)                |
+----------+----------------------------------------------------------------------------------+
|      asm | Display class bytecode by asm format (以ASM格式显示类的字节码)                       |
+----------+----------------------------------------------------------------------------------+
| shutdown | Shut down Greys server and exit the console                                      |
+----------+----------------------------------------------------------------------------------+
|     help | Display Greys Help (显示命令的帮助文档，每个命令和参数都有很详细的说明)                    |
+----------+----------------------------------------------------------------------------------+
|      top | Display The Threads Of Top CPU TIME (显示最耗CPU的Top N个线程)                      |
+----------+----------------------------------------------------------------------------------+
```

monitor：对方法的调用进行监控
```
# [c:]：统计周期
monitor -c 5 *OcxMailTaskService getTaskStatus
Press Ctrl+D to abort.

+---------------------+---------------------------------------------------------------+---------------+-------+---------+------+-----------+------------+------------+------------+
| TIMESTAMP           | CLASS                                                         | METHOD        | TOTAL | SUCCESS | FAIL | FAIL-RATE | AVG-RT(ms) | MIN-RT(ms) | MAX-RT(ms) |
+---------------------+---------------------------------------------------------------+---------------+-------+---------+------+-----------+------------+------------+------------+
| 2017-05-27 18:09:36 | com.xxx.service.impl.OcxMailTaskServiceImpl | getTaskStatus | 4     | 4       | 0    | 00.00%    | 09.00      | 8          | 10         |
+---------------------+---------------------------------------------------------------+---------------+-------+---------+------+-----------+------------+------------+------------+
```

trace：渲染和统计整个调用链路上的所有性能开销和追踪调用链路
```
# [n:]：命令执行次数
trace -n 3 *OcxMailTaskService getTaskStatus '#cost>10'

`---+Tracing for : thread_name="DubboServerHandler-xxx.xxx.xxx.xxx:20880-thread-4753" thread_id=0x5726;is_daemon=true;priority=5;
    `---+[49,49ms]com.xxx.service.impl.OcxMailTaskServiceImpl:getTaskStatus()
        +---[0,0ms]org.apache.commons.lang3.StringUtils:isBlank(@172)
        +---[1,1ms]com.xxx.service.OcxTaskService:get(@178)
        +---[1,0ms]java.util.Optional:isPresent(@179)
        +---[1,0ms]java.util.Optional:get(@182)
        +---[1,0ms]com.xxx.service.impl.OcxMailTaskServiceImpl:convert(@183)
        +---[4,1ms]com.xxx.bean.OcxTaskStatusDTO:getOcxTaskState(@184)
        +---[4,0ms]com.xxx.bean.OcxTaskStateEnum:isTerminal(@185)
        +---[4,0ms]com.xxx.bean.OcxTaskDTO:getReferenceId(@188)
        +---[49,45ms]com.xxx.mail.ForceHttpClient:taskStatus(@189)
        `---[49,0ms]com.xxx.bean.OcxTaskStatusDTO:setResult(@190)

# 进一步追踪最大耗时的方法
trace -n 3 *ForceHttpClient taskStatus

`---+Tracing for : thread_name="DubboServerHandler-xxx.xxx.xxx.xxx:20880-thread-4753" thread_id=0x5726;is_daemon=true;priority=5;
    `---+[11,11ms]com.xxx.mail.ForceHttpClient:taskStatus()
        +---[1,0ms]org.apache.commons.lang3.StringUtils:isEmpty(@130)
        +---[1,0ms]java.lang.StringBuilder:<init>(@134)
        +---[1,0ms]com.xxx.mail.ForceHttpClient:getMailLoginUrl(@134)
        +---[1,0ms]java.lang.StringBuilder:append(@134)
        +---[1,0ms]java.lang.StringBuilder:append(@134)
        +---[1,0ms]java.lang.StringBuilder:append(@134)
        +---[1,0ms]java.lang.StringBuilder:append(@134)
        +---[1,0ms]java.lang.StringBuilder:toString(@134)
        +---[1,0ms]org.slf4j.Logger:debug(@136)
        +---[11,10ms]com.xxx.http.HttpClientUtil:doGet(@137)
        `---[11,0ms]org.slf4j.Logger:debug(@138)
```
注意：`trace`能方便地帮助你定位和发现因`RT高`而导致的性能问题缺陷，但其每次只能跟踪一级方法的调用链路，目前暂时没有精力去解决往下几个层级的调用。

ptrace：trace命令的强化版，通过指定渲染路径来完成对方法执行路径的渲染过程
```
```

watch：方便地观察到指定方法的调用情况（入参、返回值、抛出异常）
```
watch -f -n 5 *OcxMailTaskService getTaskStatus params[0]+returnObj '#cost>10'
```

tt：记录下当时方法调用的所有入参和返回值、抛出的异常会对整个问题的思考与判断非常有帮助（[时间隧道](https://github.com/oldmanpushcart/greys-anatomy/wiki/TimeTunnel)）
时间隧道命令是我在使用`watch`命令进行问题排查的时候衍生出来的想法。
watch虽然很方便和灵活，但需要提前想清楚观察表达式的拼写，这对排查问题而言要求太高。  
因为很多时候我们`并不清楚问题出自于何方，只能靠蛛丝马迹进行猜测`。  
这个时候`如果能记录下当时方法调用的所有入参和返回值、抛出的异常会对整个问题的思考与判断非常有帮助`。
```
# 记录方法的调用
tt -t -n 5 *OcxMailTaskService getTaskStatus -w params[0]+returnObj '#cost>10'

# 检索调用记录
tt -l

# 查看调用信息
tt -i 1022
```

stack：输出当前方法被调用的调用路径
```
stack -n 5 *OcxMailTaskService getTaskStatus
```

##### 心路感悟-[李夏驰-杜琨-菜鸟](https://github.com/oldmanpushcart)
多年的问题排查经验我没有过多的分享，一个Java程序员个中的苦闷也无从分享，  
一切我都融入到了这款软件的命令中，希望这些沉淀能帮助到可能需要到的你少走一些弯路。  
同时我也非常期待你们对她的反馈，这样我将感到非常开心和有成就感。

