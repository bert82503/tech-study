
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

包含如下这些命令：
* ls
* ps
* cd
* pwd
* trace
* count
* invoke
* status
* log
* help
* clear
* exit

help：显示telnet命令的帮助信息  
help xxx：显示xxx命令的详细帮助信息
```
dubbo>help
Please input "help [command]" show detail.
 status [-l]                      - Show status.
 pwd                              - Print working default service.
 trace [service] [method] [times] - Trace the service.
 exit                             - Exit the telnet.
 help [command]                   - Show help.
 invoke [service.]method(args)    - Invoke the service method.
 count [service] [method] [times] - Count the service.
 clear [lines]                    - Clear screen.
 ls [-l] [service]                - List services and methods.
 log level                        - Change log level or show log
 ps [-l] [port]                   - Print server ports and connections.
 cd [service]                     - Change default service.
```

status -l：显示状态列表
```
dubbo>status -l
+------------+--------+--------------------------------------------------------+
| resource   | status | message                                                |
+------------+--------+--------------------------------------------------------+
| threadpool | OK     | Pool status:OK, max:500, core:0, largest:9, active:1, task:1421920, service port: 20880;Pool status:OK, max:2147483647, core:0, largest:2, active:0, task:64563, service port: 20888 |
| datasource | OK     | crtDataSourcejdbc:mysql://xxx.xxx.xxx.xxx:3306/wac_crt?useUnicode=true&useOldAliasMetadataBehavior=true&zeroDateTimeBehavior=convertToNull&characterEncoding=utf-8(MySQL-5.6.24-72.2-log) |
| load       | OK     | load:0.11,cpu:4                                        |
| memory     | OK     | max:1973M,total:1973M,used:474M,free:1499M             |
| server     | OK     | /xxx.xxx.xxx.xxx:20880(clients:3)                           |
| registry   | OK     | zkserver1.xxx.info:12181(connected)                  |
| spring     | OK     |                                                        |
| summary    | OK     |                                                        |
+------------+--------+--------------------------------------------------------+
```

ls：显示服务列表  
ls -l：显示服务详细信息列表  
ls -l XxxService：显示服务的方法详细信息列表
```
dubbo>ls
com.xxx.service.OcxUserService
com.xxx.service.OcxMailTaskService

dubbo>ls -l
com.xxx.service.OcxMailTaskService -> dubbo://xxx.xxx.xxx.xxx:20880/com.xxx.service.OcxMailTaskService?accepts=1000&anyhost=true&application=ocx-provider&architecture=open-api&callback.connections=200&callback.timeout=300&default.accesslog=true&default.cluster=failover&default.delay=-1&default.group=product&default.layer=api&default.loadbalance=leastactive&default.retries=1&default.timeout=1000&dubbo=2.5.3&environment=develop&getTaskStatus.connections=300&getTaskStatus.retries=1&getTaskStatus.timeout=3000&interface=com.xxx.service.OcxMailTaskService&logger=slf4j&methods=submit,getTaskStatus,callback&organization=Credit-Division&owner=dannong&pid=6656&retries=0&revision=1.0.2&side=provider&threadpool=cached&threads=500&timeout=1000&timestamp=1494833677585

dubbo>ls -l com.xxx.service.OcxMailTaskService
com.xxx.bean.OcxTaskStatusDTO getTaskStatus(java.lang.String)
int callback(com.xxx.mail.ForceTaskStatusParam)
com.xxx.mail.OcxMailTaskResponse submit(com.xxx.mail.OcxMailTaskParam)
```

cd XxxService：改变缺省服务，当设置了缺省服务，凡是需要输入服务名作为参数的命令，都可以省略服务参数  
pwd：显示当前缺省服务

invoke XxxService.xxxMethod({"prop": "value"})：调用服务的方法  
invoke xxxMethod({"prop": "value"})：调用服务的方法(自动查找包含此方法的服务)
```
dubbo>invoke com.xxx.service.OcxMailTaskService.getTaskStatus("dbe0a435e53e6e77e59302c41288ab7b")
Use default service com.xxx.service.OcxMailTaskService.
{"result":"{\"msg\":\"success\",\"status\":200,\"taskStatus\":{\"2017052621103fe3d48d5d2dbdd818ecdf7b3e65e711ph2\":{\"action\":\"persistenceAction\",\"clientTaskResponse\":{\"taskData\":\"\",\"taskType\":\"None\"},\"details\":{},\"failureType\":\"None\",\"progress\":\"100\",\"stage\":\"finish\",\"statistics\":{\"failNum\":\"0\",\"totalNum\":\"27\",\"successNum\":\"27\"},\"status\":\"SUCCESS\",\"tid\":\"2017052621103fe3d48d5d2dbdd818ecdf7b3e65e711ph2\"}}}","ocxTaskId":"dbe0a435e53e6e77e59302c41288ab7b","referenceId":"2017052621103fe3d48d5d2dbdd818ecdf7b3e65e711ph2","ocxTaskState":"NEW"}
elapsed: 8 ms.

dubbo>invoke getTaskStatus("dbe0a435e53e6e77e59302c41288ab7b")
```

trace XxxService 10：跟踪10次服务任意方法的调用情况  
trace XxxService xxxMethod 10：跟踪10次服务方法的调用情况
```
dubbo>trace com.xxx.service.OcxMailTaskService 10

/xxx.xxx.xxx.xxx:18634 -> com.xxx.service.OcxMailTaskService.getTaskStatus(["da177fa347cc3098b5293fc4d888fd39"]) -> {"result":"{\"msg\":\"success\",\"status\":200,\"taskStatus\":{\"2017052621185dd6be3c3b4b0040f8719eb8fcb32725ph2\":{\"action\":\"getInitAction\",\"clientTaskResponse\":{\"taskData\":\"\",\"taskType\":\"None\"},\"details\":{},\"progress\":\"10\",\"stage\":\"import_bill\",\"statistics\":{\"failNum\":\"0\",\"totalNum\":\"0\",\"successNum\":\"0\"},\"status\":\"FAILURE\",\"tid\":\"2017052621185dd6be3c3b4b0040f8719eb8fcb32725ph2\"}}}","ocxTaskId":"da177fa347cc3098b5293fc4d888fd39","referenceId":"2017052621185dd6be3c3b4b0040f8719eb8fcb32725ph2","ocxTaskState":"NEW"}
elapsed: 8 ms.
```

count XxxService 10：统计10次服务任意方法的调用情况  
count XxxService xxxMethod 10：统计10次服务方法的调用情况
```
dubbo>count com.xxx.service.OcxMailTaskService 10
dubbo>
+---------------+-------+--------+--------+---------+-----+
| method        | total | failed | active | average | max |
+---------------+-------+--------+--------+---------+-----+
| getTaskStatus | 0     | 0      | 0      | 0ms     | 0ms |
| callback      | 0     | 0      | 0      | 0ms     | 0ms |
| submit        | 0     | 0      | 0      | 0ms     | 0ms |
+---------------+-------+--------+--------+---------+-----+
```

ps -l：显示服务地址列表  
ps -l 20880：显示端口上的连接详细信息

```
dubbo>pwd
/

exit
```


### [开发指南](http://dubbo.io/Developer+Guide-zh.htm)

