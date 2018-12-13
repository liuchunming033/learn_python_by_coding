# 1 Python介绍
## 1-1 Python介绍
## 1-2 Python应用场景
## 1-3 Python安装
## 1-4 Python开发环境安装
## 1-5 写第一个程序
## 1-6 执行Python程序
## 1-7 参考资料

# 2 Python变量及数据类型

# 3 Python数值

# 4 Python字符串

# 5 Python列表和元组

# 6 Python字典和集合

# 7 Python条件语句
## 7-1 三元表达式

# 8 Python循环语句
## 8-1 循环控制语句

# 9 关键字介绍

# 10 变量的高级之内存管理

# 11 切片

# 12 列表生成式

# 13 迭代对象与迭代器

# 14 函数及函数定义
## 14-1 函数及函数定义
## 14-2 函数的参数/全局变量和局部变量
## 14-3 函数的调用
## 14-4 函数的返回值

# 15 内建函数

# 16 匿名函数lambda

# 17 递归函数

# 18 高阶函数
## 18-1 map
## 18-2 reduce
## 18-3 filter
## 18-4 sorted

# 19 嵌套函数

# 20 装饰器

# 21 偏函数

# 22 生成器generator

# 23 Python编程规范

# 24 模块的使用
## 24-1 模块名称空间和导入
## 24-2 模块的执行,只执行一次
## 24-3 os和sys模块介绍和使用，
## 24-4 第三方模块的安装

# 25 类和实例
Page Object模型、类和实例的概念，访问限制，获取对象信息，实例属性和类属性

# 26 多态、继承和封装

# 27 类装饰器

# 28 用__slots__
# 29 使用@property
# 30 多重继承
# 31 定制类
# 32 枚举类
# 33 数值类
# 34 使用元类
# 35 单例模式
# 36 工厂模式
# 37 异常、调试和错误
# 38 文件处理

# 39 正则表达式及re模块

# 40 常用内置模块使用
## 11-1 
## 11-2 日志记录模块logging
## 11-3 时间和日期模块 datatime模块、time模块
## 11-4 collections模块
## 11-5 base64
## 11-6 md5
## 11-7 hashlib
## 11-8 itertools
## 11-9 Hmac
## 11-10 contextlib
## 11-11 urllib2
## 11-12 XML
## 11-13 HTMLParser
## 11-14 configpars

# 12 多进程和多线程
## 12-1 并发和并行
并行, parallel
    互不干扰的在同一时刻做多件事;
    如,同一时刻,同时有多辆车在多条车道上跑,即同时发生的概念.
并发, concurrency
    同时做某些事,但是强调同一时段做多件事.
    如,同一路口,发生了车辆要同时通过路面的事件.  
参考https://www.cnblogs.com/amesy/p/8067583.html 引出多线程多进程的方案。
## 12-2 多进程
简单
## 12-3 多线程
http://python.jobbole.com/85177/ 这一篇文章讲的很透彻了。代码跟着敲打一遍。
要提到线程的问题：锁、同步、死锁。

## 12-4 多生产者多消费者模型借助Queue

如何实现生产者消费者模型？思想是：
生产者<----->队列<------>消费者

Python中的Queue模块已经提供了对线程同步的支持，所以本文并没有涉及锁、同步、死锁等多线程问题。

代码参考http://python.jobbole.com/87592/ 


# 13-1 上下文Context
with

# 14 Python环境管理
## 14-1 pyenv、pipenv
http://python.jobbole.com/89235/

# 15-1 网络编程
参考廖雪峰的教程和极客时间APP中的去谈网络协议中TCP协议那一节课。
UDP

TCP 监听的端口和实际服务的端口不是一个端口

Python 中的 Socket 编程（指南）实现TCP编程三个阶段
http://python.jobbole.com/89290/
我们将以一个简单的 Socket 服务器和客户端程序来开始本教程

当你看完 API 了解例子是怎么运行起来以后，我们将会看到一个具有同时处理多个连接能力的例子的改进版

最后，我们将会开发出一个更加完善且具有完整的自定义头信息和内容的 Socket 应用


# 16 访问数据库
## 16-1 mysql
## 16-2 redis
## 16-3 mongodb

# 17异步编程
## 17-1 asyncio
## 17-2 async/await
## 17-3 aiohttp
## 17-4 协程

# 18 制作命令行工具
## 18-1 getopt
## 18-2 fire
## 18-3 Plumbum

# 19 处理HTTP的respone
## 19-1 XML
## 19-2 HTMLParser
## 19-3 json

# 20 发起HTTP请求
# 20-1 urllib2
# 20-2 requests

# 21 单元测试框架pytest

# 22 Python设计模式及应用

# 23 Python Web开发

## 23-1 HTTP协议简介

## 23-2 HTML简介

## 23-3 写一个web服务
一个完整，接受HTTP请求、解析HTTP请求、处理HTTP请求，发送HTTP响应。其中接受HTTP请求、解析HTTP请求、发送HTTP响应，对于任何请求的流程都是一样的，处理也是一样的，如果web开发者每个web项目都要实现这三个步骤，太不方便了。
正确的做法是底层代码由专门的服务器软件实现，我们用Python专注于生成HTML文档。因为我们不希望接触到TCP连接、HTTP原始请求和响应格式，所以，需要一个统一的接口，让我们专心用Python编写Web业务。

这个接口就是WSGI：Web Server Gateway Interface。

WSGI协议

## 23-4 Web部署
http请求流程这里有一张图：https://img-blog.csdn.net/20180306142935273?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQveWprMTM3MDM2MjM3NTc=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70
这里面涉及到一些概念：uWSGI，uwsgi，Nginx

WSGI

WSGI的全称是Web Server Gateway Interface（Web服务器网关接口），它不是服务器、python模块、框架、API或者任何软件，只是一种描述web服务器（如nginx，uWSGI等服务器）如何与web应用程序（如用Django、Flask框架写的程序）通信的规范。

server和application的规范在PEP3333中有具体描述，要实现WSGI协议，必须同时实现web server和web application，当前运行在WSGI协议之上的web框架有Bottle, Flask, Django。

uWSGI

uWSGI是一个全功能的HTTP服务器，实现了WSGI协议、uwsgi协议、http协议等。它要做的就是把HTTP协议转化成语言支持的网络协议。比如把HTTP协议转化成WSGI协议，让Python可以直接使用。

uwsgi

与WSGI一样，是uWSGI服务器的独占通信协议，用于定义传输信息的类型(type of information)。每一个uwsgi packet前4byte为传输信息类型的描述，与WSGI协议是两种东西，据说该协议是fcgi协议的10倍快。

Nginx

Nginx是一个Web服务器其中的HTTP服务器功能和uWSGI功能很类似，但是Nginx还可以用作更多用途，比如最常用的反向代理功能。

Django

Django是一个Web框架，框架的作用在于处理request和 reponse，其他的不是框架所关心的内容。所以如何部署Django不是Django所需要关心的。

参考（https://blog.csdn.net/yjk13703623757/article/details/79457913）
里面浏览器访问python程序的流程图。

Browser-->Nginx（web服务器）-->uWSGI（WSGI服务器）-->Application（WSGI应用）

Nginx接受来自客户端的Http请求发送给uWSGI，uWSGI处理请求并将关键信息传递给web应用(django，flask等)，应用返回Response经由uWSGI发送给Nginx，Nginx再发送给客户端。 
## 23-5 编写一个符合WSGI接口规范的应用并运行起来（借助wsgiref）
参考1：
https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/001432012393132788f71e0edad4676a3f76ac7776f3a16000

参考2：
https://blog.csdn.net/a519640026/article/details/76157976
## 23-6 自己实现一个WSGI Server
参考
https://blog.csdn.net/a519640026/article/details/76157976
http://fanchunke.me/Python/wsgiref%E5%8C%85%E2%80%94%E2%80%94%E7%AC%A6%E5%90%88WSGI%E6%A0%87%E5%87%86%E7%9A%84Web%E6%9C%8D%E5%8A%A1%E5%AE%9E%E7%8E%B0%EF%BC%88%E4%B8%80%EF%BC%89/


# 24 Python 网络爬虫
request库+HTML解析

# 25 Python 做软件测试
py.test单元测试框架

# 26 Python