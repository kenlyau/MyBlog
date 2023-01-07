---
layout: post
title:  "pve 命令行功能展示"
date:   2023-1-07 20:46:15
categories: technique
tags: [lab,pve]
---

### lvrename(修改虚拟机磁盘id)
```
lvrename /dev/pve/vm-105-disk-1 /dev/pve/vm-100-disk-1
```
修改虚拟机磁盘 vm-105-disk-1 到vm-100-disk-1

### 修改虚拟机id
```
$cd /etc/pve/nodes/hostnmae/qemu-server
$mv 100.conf 200.conf
$nano 200.conf
```
```
### 修改conf文件
sata0:ZFSA_Pool:vm-100-disk-0,size=50G
to:
sata0:ZFSA_Pool:vm-200-disk-0,size=50G

替换所有的vm-100-disk为vm-200-disk
```
