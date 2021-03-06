---
title: Flask
date: 2019-01-14 11:39:08
tags:
---
# Run sever
```
FLASK_APP=manage.py FLASK_ENV=development flask run
```

# 项目结构
```
|- projectName   
        |- app  //程序包   
                |- templates //jinjia2模板   
                |- static //css,js 图片等静态文件   
                |- main  //py程序包 ，可以有多个这种包，每个对应不同的功能   
                        |- __init__.py
                        |- errors.py
                        |- forms.py
                        |- views.py
                |- __init__.py
                |- email.py //邮件处理程序
                |- models.py //数据库模型
        |- migrations //数据迁移文件夹
        |- tests  //单元测试
                |- __init__.py
                |- test*.py //单元测试程序，可以包含多个对应不同的功能点测试
        |- venv  //虚拟环境
        |- requirements.txt //列出了所有依赖包以及版本号，方便在其他位置生成相同的虚拟环境以及依赖
        |- config.py //全局配置文件，配置全局变量
        |- manage.py //启动程序
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

# 异步任务
## 在Flask中使用简单异步任务
```
from flask import Flask
from time import sleep
from concurrent.futures import ThreadPoolExecutor

executor = ThreadPoolExecutor(2)

app = Flask(__name__)


@app.route('/jobs')
def run_jobs():
    executor.submit(some_long_task1)
    executor.submit(some_long_task2, 'hello', 123)
    return 'Two jobs was launched in background!'


def some_long_task1():
    print("Task #1 started!")
    sleep(10)
    print("Task #1 is done!")


def some_long_task2(arg1, arg2):
    print("Task #2 started with args: %s %s!" % (arg1, arg2))
    sleep(5)
    print("Task #2 is done!")


if __name__ == '__main__':
    app.run()
```


# os命令
## Download folder
```
def get_download_folder():
    """
    Get mac downloads folder
    """
    home = os.path.expanduser("~")
    return os.path.join(home, "Downloads")
```

## Username
`os.getlogin()`
