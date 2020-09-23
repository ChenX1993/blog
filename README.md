# Hexo实现静态Blog, Deploy on github pages, Travis CI集成

## 主要结构
1. dev分支: 主分支，放hexo运行文件  
2. gh-pages分支: 存放生成的静态文件  
> Travis已经配置完毕，push到dev分支会触发Travis执行脚本，生成静态文件(build folder)，push回 gh-pages分支  

`git push origin dev`

## Access Via Github
[https://chenx1993.github.io/blog/](https://chenx1993.github.io/blog/)

## Hexo指令
### 安装
`brew install node`

`npm install -g hexo`

`npm install hexo-cli -g`

### 构建
`hexo init [folder name]`  

### clean generate start deply
`hexo c/g/s/d`
