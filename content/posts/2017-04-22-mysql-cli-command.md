---
layout: post
title:  "mysql 常用命令解读"
date:   2017-04-22 10:38:22
categories: technique
tags: [linux,mysql]
---

- $ mysql -u root -p;
// 输入口令进入mysql控制台

- $ show databases;
// 显示数据库

- $ create database 数据库名;
// 创建数据库

- $ drop database 数据库名;
// 删除数据库

- $ use 数据库名;
// 使用数据库

- $ create table 表名 (字段1 类型1, .... 字段n 类型n);
// 创建表

- $ drop table 表名
// 删除表

- $ grant all privileges on 数据库名.* to 用户名@权限范围 identified by '密码';
// 创建用户并分配管理权限
// 权限范围：1,%,任何地方都可以访问；2,localhost,本地访问权限；3,ip,制定ip可以访问

- $ create user 用户名@权限范围 identified by '密码';
// 创建用户

- $ mysqldump -u root -p 密码 数据库名 > 导出数据库名
// 导出数据库

- $ mysqldump -u root -p 密码 -d -add-drop-table 数据库名 > 数据库名
// 导出数据库结构

### 实例
```
drop database if exists school; //如果存在SCHOOL则删除
create database school; //建立库SCHOOL
use school; //打开库SCHOOL
create table teacher //建立表TEACHER
(
    id int(3) auto_increment not null primary key,
    name char(10) not null,
    address varchar(50) default ''深圳'',
    year date
); //建表结束

//以下为插入字段
insert into teacher values('''',''glchengang'',''深圳一中'',''1976-10-10'');
insert into teacher values('''',''jack'',''深圳一中'',''1975-12-23'');

```

[kenlyau.github.io][link]

[link]:    https://kenlyau.github.io
