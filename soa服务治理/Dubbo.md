
Dubbo是一个分布式服务框架，致力于提供高性能和透明化的RPC远程服务调用方案，是阿里巴巴SOA服务化治理方案的核心框架。  
每天为2,000+个服务提供3,000,000,000+次访问量支持，并被广泛应用于阿里巴巴集团的各成员站点。

### 入门
1. [DUBBO](http://dubbo.io/)

### [用户指南](http://dubbo.io/User+Guide-zh.htm)
#### [配置参考手册](http://dubbo.io/User+Guide-zh.htm#UserGuide-zh-%E9%85%8D%E7%BD%AE%E5%8F%82%E8%80%83%E6%89%8B%E5%86%8C)

#### [Telnet命令参考手册](http://dubbo.io/User+Guide-zh.htm#UserGuide-zh-Telnet%E5%91%BD%E4%BB%A4%E5%8F%82%E8%80%83%E6%89%8B%E5%86%8C)
```
telnet localhost 20880
```

help：显示telnet命令的帮助信息  
help xxx：显示xxx命令的详细帮助信息
```
help

Please input "help [command]" show detail.
 status [-l]                      - Show status. 显示状态列表
 pwd                              - Print working default service. 显示当前缺省服务
 trace [service] [method] [times] - Trace the service. 跟踪服务的调用情况
 exit                             - Exit the telnet. 退出
 help [command]                   - Show help. 显示命令帮助信息
 invoke [service.]method(args)    - Invoke the service method. 调用服务的方法
 count [service] [method] [times] - Count the service. 统计服务的调用情况
 clear [lines]                    - Clear screen. 清屏
 ls [-l] [service]                - List services and methods. 显示服务列表和方法列表
 log level                        - Change log level or show log. 修改日志级别或查看日志
 ps [-l] [port]                   - Print server ports and connections. 显示服务端口列表和连接信息
 cd [service]                     - Change default service. 改变缺省服务(/：根目录)
```

ls：显示服务列表  
ls -l：显示服务详细信息列表  
ls -l XxxService：显示服务的方法详细信息列表
```
ls
com.xxx.service.OcxMailTaskService

ls -l
com.xxx.service.OcxMailTaskService -> dubbo://xxx.xxx.xxx.xxx:20880/com.xxx.service.OcxMailTaskService?accepts=1000&anyhost=true&application=ocx-provider&architecture=open-api&callback.connections=200&callback.timeout=300&default.accesslog=true&default.cluster=failover&default.delay=-1&default.group=product&default.layer=api&default.loadbalance=leastactive&default.retries=1&default.timeout=1000&dubbo=2.5.3&environment=develop&getTaskStatus.connections=300&getTaskStatus.retries=1&getTaskStatus.timeout=3000&interface=com.xxx.service.OcxMailTaskService&logger=slf4j&methods=submit,getTaskStatus,callback&organization=Credit-Division&owner=dannong&pid=6656&retries=0&revision=1.0.2&side=provider&threadpool=cached&threads=500&timeout=1000&timestamp=1494833677585

ls -l com.xxx.service.OcxMailTaskService
com.xxx.bean.OcxTaskStatusDTO getTaskStatus(java.lang.String)
int callback(com.xxx.mail.ForceTaskStatusParam)
com.xxx.mail.OcxMailTaskResponse submit(com.xxx.mail.OcxMailTaskParam)
```

ps -l：显示服务地址列表  
ps -l 20880：显示端口上的连接详细信息

cd XxxService：改变缺省服务，当设置了缺省服务，凡是需要输入服务名作为参数的命令，都可以省略服务参数  

trace XxxService 10：跟踪10次服务任意方法的调用情况  
trace XxxService xxxMethod 10：跟踪10次服务方法的调用情况
```
trace com.xxx.service.OcxMailTaskService 10

/xxx.xxx.xxx.xxx:18634 -> com.xxx.service.OcxMailTaskService.getTaskStatus(["da177fa347cc3098b5293fc4d888fd39"]) -> {"result":"{\"msg\":\"success\",\"status\":200,\"taskStatus\":{\"2017052621185dd6be3c3b4b0040f8719eb8fcb32725ph2\":{\"action\":\"getInitAction\",\"clientTaskResponse\":{\"taskData\":\"\",\"taskType\":\"None\"},\"details\":{},\"progress\":\"10\",\"stage\":\"import_bill\",\"statistics\":{\"failNum\":\"0\",\"totalNum\":\"0\",\"successNum\":\"0\"},\"status\":\"FAILURE\",\"tid\":\"2017052621185dd6be3c3b4b0040f8719eb8fcb32725ph2\"}}}","ocxTaskId":"da177fa347cc3098b5293fc4d888fd39","referenceId":"2017052621185dd6be3c3b4b0040f8719eb8fcb32725ph2","ocxTaskState":"NEW"}
elapsed: 8 ms.
```

count XxxService 10：统计10次服务任意方法的调用情况  
count XxxService xxxMethod 10：统计10次服务方法的调用情况
```
count com.xxx.service.OcxMailTaskService 10

+---------------+-------+--------+--------+---------+-----+
| method        | total | failed | active | average | max |
+---------------+-------+--------+--------+---------+-----+
| getTaskStatus | 0     | 0      | 0      | 0ms     | 0ms |
| callback      | 0     | 0      | 0      | 0ms     | 0ms |
| submit        | 0     | 0      | 0      | 0ms     | 0ms |
+---------------+-------+--------+--------+---------+-----+
```

invoke XxxService.xxxMethod({"prop": "value"})：调用服务的方法  
invoke xxxMethod({"prop": "value"})：调用服务的方法(自动查找包含此方法的服务)
```
invoke com.xxx.service.OcxMailTaskService.getTaskStatus("dbe0a435e53e6e77e59302c41288ab7b")
Use default service com.xxx.service.OcxMailTaskService.
{"result":"{\"msg\":\"success\",\"status\":200,\"taskStatus\":{\"2017052621103fe3d48d5d2dbdd818ecdf7b3e65e711ph2\":{\"action\":\"persistenceAction\",\"clientTaskResponse\":{\"taskData\":\"\",\"taskType\":\"None\"},\"details\":{},\"failureType\":\"None\",\"progress\":\"100\",\"stage\":\"finish\",\"statistics\":{\"failNum\":\"0\",\"totalNum\":\"27\",\"successNum\":\"27\"},\"status\":\"SUCCESS\",\"tid\":\"2017052621103fe3d48d5d2dbdd818ecdf7b3e65e711ph2\"}}}","ocxTaskId":"dbe0a435e53e6e77e59302c41288ab7b","referenceId":"2017052621103fe3d48d5d2dbdd818ecdf7b3e65e711ph2","ocxTaskState":"NEW"}
elapsed: 8 ms.

invoke getTaskStatus("dbe0a435e53e6e77e59302c41288ab7b")
```

status -l：显示状态列表
```
status -l
+------------+--------+--------------------------------------------------------+
| resource   | status | message                                                |
+------------+--------+--------------------------------------------------------+
| threadpool | OK     | Pool status:OK, max:500, core:0, largest:9, active:1, task:1421920, service port: 20880;Pool status:OK, max:2147483647, core:0, largest:2, active:0, task:64563, service port: 20888 |
| datasource | OK     | dataSourcejdbc:mysql://xxx.xxx.xxx.xxx/test?useUnicode=true&useOldAliasMetadataBehavior=true&zeroDateTimeBehavior=convertToNull&characterEncoding=utf-8(MySQL-5.6.24-72.2-log) |
| load       | OK     | load:0.11,cpu:4                                        |
| memory     | OK     | max:1973M,total:1973M,used:474M,free:1499M             |
| server     | OK     | /xxx.xxx.xxx.xxx:20880(clients:3)                      |
| registry   | OK     | zkserver1.xxx.info(connected)                          |
| spring     | OK     |                                                        |
| summary    | OK     |                                                        |
+------------+--------+--------------------------------------------------------+
```


### [开发指南](http://dubbo.io/Developer+Guide-zh.htm)

