---
layout: post
title:  "install postgresql on raspberry-pi"
date:   2017-12-28 22:06:29
categories: technique
tags: 
- database
- postgresql
---
### 安装
1. sudo apt-get install postgresql-9.4

2. sudo cp /etc/postgresql/9.4/main/pg_hba.conf /etc/postgresql/9.4/main/pg_hba.conf.bak

  host     all     all     192.168.0.0/24     md5
  
  修改可访问ip限制

3. sudo cp /etc/postgresql/9.4/main/postgresql.conf /etc/postgresql/9.4/main/postgresql.conf.bak

  listen_addresses = 'localhost'

  To:

  listen_addresses = '*'
  
  修改postgresql启动绑定ip

4. sudo /etc/init.d/postgresql restart

  重启
  
### 操作命令

```
sudo -u postgres createuser --superuser dbuser #创建用户dbuser
sudo -u postgres createdb -O dbuser exampledb #创建数据库exampledb，指定管理员为dbuser
sudo -u postgres psql #登录postgresql控制台
\password dbuser #为dbuser设置密码
\q #退出控制台


psql -U dbuser -d exampledb -h 127.0.0.1 -p 5432 #登录到数据库
CREATE TABLE user_tbl(name VARCHAR(20), signup_date DATE); #创建表
```

参考网站
[bpwalters.com]: https://bpwalters.com/blog/setting-up-postgresql-on-raspberry-pi/
[www.ruanyifeng.com]:    http://www.ruanyifeng.com/blog/2013/12/getting_started_with_postgresql.html
