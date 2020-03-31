---
title: Linux Commands  
date: 2019-01-16 01:12:44  
tags:
---

## 文件操作:
### ls
* -a : 显示全部文件
* -l : 详情显示
* 组合命令

### mkdir
* -p 参数 
* 
### cd
* 上下级目录
* 
### rm
•	删除文件
•	删除文件夹
•	删除当前目录下所有文件

### mv

### cp

### cat
* 显示内容
* 导入文件
* 追加如文件

### sudo
* 作用
* command not found

### git clone
* 从github上clone一个repo到本地

## 进阶
### grep
* 搜索文件内容
* 搜索前一个命令输出

### ifconfig
* 找到ip

### lsof
* lsof -i tcp:5000

### shell
* 脚本编写
* 执行权限

## 服务器交互
### wget

### scp
* 下载文件 scp user@ip:server_path local_path
* 下载目录 scp -r user@ip:server_path local_path
* 上传文件 scp local_path user@ip:server_path

### 测试远程端口telnet [ip] [端口]

### 本机测试 netstat –aupnt | grep 端口号
