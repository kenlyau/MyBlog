---
layout: post
title:  "install rethinkdb on raspberry-pi"
date:   2017-07-07 23:47:09 +0800
categories: technique
tags: [rethinkdb,raspberry-pi]
---

raspberry-pi 安装 rethinkdb 需要进行编译安装
> https://www.rethinkdb.com/docs/install/raspbian/

```
#安装依赖
$ sudo apt-get install g++ protobuf-compiler libprotobuf-dev libboost-dev curl m4 wget libssl-dev

#下载源文件
$ wget https://download.rethinkdb.com/dist/rethinkdb-2.3.5.$ tgz
tar xf rethinkdb-2.3.5.tgz

#编译安装
$ cd rethinkdb-2.3.5
$ ./configure --with-system-malloc --allow-fetch
$ make ALLOW_WARNINGS=1
$ sudo make install ALLOW_WARNINGS=1

```

树莓派编译安装成功后，默认安装配置文件位置在 '/usr/local/etc/rethinkdb'

```
$ cd /usr/local/etc/rethinkdb
$ cp default.conf.sample instance.d/default.conf
$ vim instance.d/default.conf

# 修改配置文件
# runuser=rethinkdb
# rungroup=rethinkdb
runuser=pi
rungroup=pi

# server-name=server1
server-name=dbs1

#从服务器配置加入到主服务器ip,主服务器不需配置
#join=xxx:29015
```

可执行二进制文件位置在 '/usr/local/bin/rethinkdb'


写入运行脚本 /etc/init.d/rethinkdb
> https://raw.githubusercontent.com/rethinkdb/rethinkdb/next/packaging/assets/init/rethinkdb

下载到/etc/init.d/目录下，执行 'chmod +x rethinkdb'

```
$ vim rethinkdb
# 修复配置
# 可执行二进制程序
rtdbbin=/usr/local/bin/rethinkdb;
# 配置文件目录
rtdbconfigdir=/usr/local/etc/rethinkdb;
```

启动服务
```
$ sudo /etc/init.d/rethinkdb start
```
