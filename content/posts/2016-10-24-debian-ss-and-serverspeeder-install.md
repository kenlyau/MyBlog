---
layout: post
title:  "debian shadowsocks and serverspeeder install"
date:   2016-10-24 11:38:22
categories: technique
tags: [shadowsocks,linux]
---

### 1. shadowsocks 安装
https://github.com/teddysun/shadowsocks_install  
安装shadowssocks go 版本, 脚本安装完后自动运行。配置文件位置安装在 

```
[/etc/shadowsocks/config.json];

/***********************************
* single user
************************************************/
{
    "server":"0.0.0.0",
    "server_port":8989,
    "local_address":"127.0.0.1",
    "local_port":1080,
    "password":"yourpassword",
    "timeout":300,
    "method":"aes-256-cfb",
    "fast_open": false
}

/****************************************************
* multi user
***************************************************/

{
    "server":"0.0.0.0",
    "local_address":"127.0.0.1",
    "local_port":1080,
    "port_password":{
         "8989":"password0",
         "9001":"password1",
         "9002":"password2",
         "9003":"password3",
         "9004":"password4"
    },
    "timeout":300,
    "method":"aes-256-cfb",
    "fast_open": false
}

```

### 2.锐速安装
安装shadowssocks后，进行测试速度大概在120k左右，果断安装加速，速度瞬间飚到4m。
锐速破解版 
https://www.91yun.org/archives/683


[kenlyau.github.io][link]

[link]:    https://kenlyau.github.io
