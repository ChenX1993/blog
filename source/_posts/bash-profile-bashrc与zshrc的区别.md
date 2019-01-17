---
title: bash_profile, bashrc与zshrc的区别
date: 2019-01-16 22:22:41
tags:
---

看教程的时候，经常能看到需要在这三个文件上读写。那么这三个文件是干什么的，以及有什么区别呢？

这三个文件都是用来设置用户工作环境的文件。它们都是终端启动时默认运行的文件。只不过他们稍有区别。

> Login Shell: 输入密码进入终端的shell环境叫做Login Shell，如ssh远程登录  
> no-Login Shell: 普通双击打开终端成为no-Login Shell, 但是在Mac中，系统都会默认给Login Shell。

* bash_profile: 专门用于Login Shell里的
* bashrc: 专门用于no-Login Shell里的
* zshrc: 装了oh-my-zsh之后，启动时会运行zshrc而不是上面两个文件。另外它和Login Shell与no-Login Shell都没有关系，不管什么shell都会运行。

![](/images/scrapy.png)