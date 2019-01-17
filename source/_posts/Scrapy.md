---
title: Scrapy
date: 2019-01-16 22:48:48
tags:
---

pip3 list  
[https://doc.scrapy.org/en/latest/intro/tutorial.html
](https://doc.scrapy.org/en/latest/intro/tutorial.html
)

## Create a project
`scrapy startproject tutorial`

This will create a `tutorial` directory with the following contents:

```
tutorial/
    scrapy.cfg            # deploy configuration file

    tutorial/             # project's Python module, you'll import your code from here
        __init__.py

        items.py          # project items definition file

        middlewares.py    # project middlewares file

        pipelines.py      # project pipelines file

        settings.py       # project settings file

        spiders/          # a directory where you'll later put your spiders
            __init__.py
```

## How to run our spider
`scrapy crawl quotes`

![](/images/scrapy.png)
            