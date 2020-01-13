+++
categories = "tech"
date = 2020-01-12T16:00:00Z
draft = true
layout = "post"
tags = ["database", "postgresql"]
title = "postgresql-setup"

+++
\# postgresql 环境搭建2节点

\### 安装postgresql10 debian9系统

官网安装文档 [https://www.postgresql.org/download/linux/debian/](https://www.postgresql.org/download/linux/debian/ "https://www.postgresql.org/download/linux/debian/")

\`\`\`

\# 配置postgresql 源

sudo apt-get install postgresql-10

\`\`\`

\### postgresql 常用命令

\`\`\`

\# 需要切换到postgres账号

su - postgres

\# 进入命令模式

psql

\# 退出命令行

\\q

\# 创建用户

CREATE USER dbuser WITH PASSWORD 'xxxxxx';

\# 创建用户数据库

CREATE DATABASE exampledb OWNER dbuser;

\# 数据库授权

GRANT ALL PRIVILEGES ON DATABASE exampledb TO dbuser;

\# 导入sql文件

psql -U username -d database -f sqlfile.sql;

\# 查看数据库列表

\\l 

\\list

\# 展示当前数据库下的所有表

\\d

\# 展示表对应的字段信息

\\d tablename

\# 创建角色带权限

\# 1可以创建数据库的用户

create role username login password '123456' createdb;

\# 2可以创建角色的用户

create role username login password '123456' createrole;

\# 3可以登录的用户

create role username login password '123456' login;

\`\`\`

\### postgresql 连接配置

\`\`\`

\# /etc/postgresql/10/main/pg_hba.conf

host      all                 all            192.168.0.1/24          md5

\# /etc/postgresql/10/main/postgresql.conf

listen_addresses='*'

\`\`\`

\# 主从复制

注意

database system identifier differs between the primary and standby

从库和主库基础数据不一致，先同步两个库的数据