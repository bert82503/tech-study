

Nacos 动态配置实战
======
> https://nacos.io/zh-cn/
> 
> https://github.com/alibaba/nacos

# Nacos: Dynamic Naming and Configuration Service
an easy-to-use **dynamic** **service discovery, configuration and service management platform** for building cloud native applications.

### 功能
#### 动态配置服务
#### 服务发现及管理
#### 动态DNS服务

[Nacos 快速开始](https://nacos.io/zh-cn/docs/quick-start.html)

## 一、初始化数据库表
MySQL

[MySQL Community Server (Archived Versions)](https://downloads.mysql.com/archives/community/)
```shell
 ~ mysql -V
mysql  Ver 8.0.33 for macos13 on arm64 (MySQL Community Server - GPL)
 ~ mysqld -V
/usr/local/mysql-8.0.33-macos13-arm64/bin/mysqld  Ver 8.0.33 for macos13 on arm64 (MySQL Community Server - GPL)

```

### 1.cmd命令行客户端
```shell
# 密码建议在下一行输入
mysql -h localhost -P 3306 -u root -p

mysql -h localhost -P 3306 -u root -p12345678

```

### 2.创建用户与授权
https://dev.mysql.com/doc/refman/8.0/en/create-user.html
https://dev.mysql.com/doc/refman/8.0/en/grant.html
```mysql
CREATE USER 'username'@'host' IDENTIFIED BY 'password';
# 创建用户
CREATE USER 'nacos'@'localhost' IDENTIFIED BY 'nacos';

# 授权
GRANT ALL ON *.* TO 'nacos'@'localhost';

# 删除用户
DROP USER 'nacos'@'localhost';

```

### 3.创建数据库
https://dev.mysql.com/doc/refman/8.0/en/create-database.html
```mysql
# 创建数据库
CREATE DATABASE IF NOT EXISTS `nacos`
    DEFAULT CHARACTER SET utf8
    DEFAULT COLLATE utf8_bin;

# 删除数据库
DROP DATABASE `nacos`;

```

### 4.创建数据表
https://dev.mysql.com/doc/refman/8.0/en/create-table.html
```mysql
# 切换数据库
USE `nacos`;

# 创建数据表
# nacos/conf/mysql-schema.sql

```


## 二、启动Nacos服务器
### 1.增加`nacos/conf/application.properties`的数据源配置
```properties

#*************** Config Module Related Configurations ***************#
### If use MySQL as datasource:
### Deprecated configuration property, it is recommended to use `spring.sql.init.platform` replaced.
# spring.datasource.platform=mysql
# spring.sql.init.platform=mysql
spring.sql.init.platform=mysql

### Count of DB:
# db.num=1
db.num=1

### Connect URL of DB:
# db.url.0=jdbc:mysql://127.0.0.1:3306/nacos?characterEncoding=utf8&connectTimeout=1000&socketTimeout=3000&autoReconnect=true&useUnicode=true&useSSL=false&serverTimezone=UTC
# db.user.0=nacos
# db.password.0=nacos
db.url.0=jdbc:mysql://127.0.0.1:3306/nacos?characterEncoding=utf8&connectTimeout=1000&socketTimeout=3000&autoReconnect=true&useUnicode=true&useSSL=false&serverTimezone=Asia/Shanghai&zeroDateTimeBehavior=convertToNull&allowPublicKeyRetrieval=true
db.user.0=nacos
db.password.0=nacos

```

### 2.启动Nacos服务器
```shell
unzip nacos-server-2.2.3.zip
# 移动文件夹
sudo mv nacos-server-2.2.3 /usr/local

cd /usr/local
# 创建软链接
sudo ln -s nacos-server-2.2.3 nacos
# 变更软链接的所有者和分组
sudo chown -R lihuagang:staff nacos

# 启动独立服务器
cd nacos/bin
sh startup.sh -m standalone

```

