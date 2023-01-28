---
layout: post
title:  "netdata监控主机运行状态，cpu温度监控"
date:   2023-01-28 20:46:15
categories: technique
tags: [lab,netdata]
---

### 安装netdata
在netdata官方文档（https://learn.netdata.cloud/guides/step-by-step/step-00）中找到安装脚本
```
wget -O /tmp/netdata-kickstart.sh https://my-netdata.io/kickstart.sh && sh /tmp/netdata-kickstart.sh
```

### 初始化传感器监控脚本
```
$cd /etc/netdata
$./edit-config python.d/sensors.conf
```

### 安装linux下传感器工具lm-sensors
```
$apt-get install lm-sensors -y
```

### netdata 常用命令
```
$systemctl restart netdata #重启
```
