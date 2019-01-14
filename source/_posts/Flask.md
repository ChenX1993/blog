---
title: Flask
date: 2019-01-14 11:39:08
tags:
---
# Run sever
```
FLASK_APP=manage.py FLASK_ENV=development flask run
```

# Virtualenv
## 安装Library
`pip3 install virtualenv`

## 创建虚拟环境
`mkdir myproject`  
`python3 -m venv venv`

## 激活虚拟环境
`. venv/bin/activate` 

## 安装Flask
`pip install Flask`
 
## 退出虚拟环境
`deactivate`

# 安装依赖 
## 生成requirements.txt
`pip freeze > requirements.txt`
 
## 安装requirements.txt依赖
`pip install -r requirements.txt`
