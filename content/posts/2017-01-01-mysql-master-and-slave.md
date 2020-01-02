---
layout: post
title:  "mysql setting master and slave"
date:   2017-01-07 21:38:22
categories: technique
tags: [linux,mysql]
---

### 1. 主设置（master）
修改mysql配置文件，一般在/etc/mysql/my.conf

```
server-id=1 //设置mysql的id标识
log-bin=/var/lib/mysql/mysql-bin  //log-bin的日志文件，主从备份就是用这个日志记录来实现的
#binlog-do-db=mysql1 #需要备份的数据库名，如果备份多个数据库，重复设置这个选项 即可
#binlog-ignore-db=mysql2 #不需要备份的数据库名，如果备份多个数据库，重复设置这 个选项即可
#log-slave-updates=1 #这个参数当从库又作为其他从库的主库时一定要加上，否则不会给更新的记录写到binglog里二进制文件里
#slave-skip-errors=1 #是跳过错误，继续执行复制操作(可选)

```
在主mysql中增加2个用来同步的账号

```
mysql>grant replication slave on *.* to 'sync-1'@'%' identified by '123456';
mysql>grant replication slave on *.* to 'sync-2'@'%' identified by '123456';

```
重启msql

```
mysql>show master status; //可以查看主mysql状态
```

### 2. 从设置（slave）
修改mysql配置文件 my.conf，两个从节点配置方式都一样。

```
server-id=2
#log-bin=/var/lib/mysql/mysql-bi //从mysql可以不用设置日志文件
```
在从mysql中增加命令参数,master_log_file 和master_log_pos 可以在master mysql中用 show master status查询到

```
mysql>change master to master_host='192.168.145.222',master_user='sync-1',master_password='123456',master_log_file='mysql-bin.000001',master_log_pos=308;  
mysql>start slave //启动
mysql>show slave status\G //查询状态，Slave_IO_Running 和Slave_IO_Running都为yes表示成功
```

### 3. 设置中的出现的问题
#### Last_Errno: 1146
设置出从的时候，我的主mysql已经有一张表了，当时创建表的binlog二进制日志就没有记录，从mysql无法写入数据，这时候只有手动导入数据库文件到从mysql中；
#### Last_Errno: 1062
Error 'Duplicate entry 'xxxxx' for key 'PRIMARY'' on query

主键冲突，

```
# on slave
mysql> stop slave;
mysql> flush privileges;

# on master rest master
mysql> reset master;

# on slave;
mysql> reset slave;
mysql> start slave;
```
[kenlyau.github.io][link]

[link]:    https://kenlyau.github.io
