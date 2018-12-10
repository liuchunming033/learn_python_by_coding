# 1 Python介绍和安装
## 1-1 Python介绍
Python的官网是：https://www.python.org 

Python高级解释型语言。语法简单，入门容易，想精通要花功夫。

## 1-2 Python应用场景
Python能干啥？web开发、爬虫、数据分析、软件测试、深度学习、人工智能等领域。

## 1-3 Python安装
可以通过pyenv安装python版本，安装pyenv的方法参考 https://github.com/pyenv/pyenv#basic-github-checkout

安装配置完成后执行下`source ~/.bash_profile`, 就可以执行pyenv命令来安装Python版本了。

比如安装python 3.6.7，执行下面的命令就可以了
```bash
pyenv install 3.6.7
```
安装完成后，查看一下是否安装成功了
```bash
pyenv versions
```
如果输出如下，则表示安装成功了
```bash
* system (set by /Users/mac/.pyenv/version)
  3.6.7
```
如果想要3.6.7版本生效，可以执行
```bash
pyenv global 3.6.7
```
如果输出的3.6.7前面有*号，则表示设置成功了
```bash
  system
* 3.6.7 (set by /Users/mac/.pyenv/version)
```
## 1-4 Python开发环境安装
安装pycharm社区版 http://www.jetbrains.com/pycharm/download 选择Community版下载就可以。按照提示安装。配置。

## 1-5 写第一个程序
1、打开Pycharm——>Create New Project——>给项目起名字——>选择python解释器版本(可以在~/.pyenv/shims/中找到刚才安装的python3.6版本)——>点击"Create"。

2、进入项目中，在项目文件夹上点击右键，选择New——>Python File——>输入文件名hello——>点击"OK"。

3、在新建的hello.py中输入下面的代码
```python
print("Hello world!")
```

4、在代码编辑区点击右键，选择"Run hello"，执行hello.py。可以在Pycharm的底部看到输出结果"Hello world!"
```bash
/Users/mac/.pyenv/shims/python3.6 /Users/mac/Documents/GitHub/learn_python_by_coding/hello.py
Hello world!

Process finished with exit code 0

```

# 2 Python基础知识

## 2-1 Python变量赋值及数据类型

资料简介： 2-1 Python变量赋值及数据类型
资料下载：Python 里的两个布尔值 True 和 False 

## 2-2 Python数值及方法

1、http://python.jobbole.com/89331/ 使用 enum 枚举类型代替数字字面量改善代码，
2、不必预计算字面量表达式，当我们的代码中需要出现复杂计算的字面量时，请保留整个算式吧。它对性能没有任何影响，而且会增加代码的可读性。

## 2-3 Python字符串及方法
参考资料：http://python.jobbole.com/89331/

1、别在裸字符串处理上走太远，对于 SQL 语句这种结构化、有规则的字符串，用对象化的方式构建和编辑它才是更好的做法
2、改善超长字符串的可读性括号括起来就可以随意换行了()
3、别忘了那些 “r” 开头的内建字符串函数，从右往左处理有时候更方便。
4、用 "".join(str_list) 之类的方式来进行字符串拼接。
5、%s拼接 
6、format方法拼接
参考字符串拼接http://python.jobbole.com/89250/?utm_source=blog.jobbole.com&utm_medium=relatedPosts

## 2-4 Python列表和元组
在绝大多数情况下都可以直接等价于 1 和 0 两个整数来使用，将某个布尔值表达式作为列表的下标使用，可以实现类似三元表达式的目的["Python", "Javascript"][2 > 1]

资料简介： 2-4 Python列表和元组，介绍切片操作
资料下载：点击下载
## 2-5 Python字典和集合

资料简介： 2-5 Python字典和集合
资料下载：点击下载
# 3 Python语句、关键字以及内存管理
## 3-1 Python-条件语句
在这一节介绍三元表达式：

x = y.lower() if isinstance(y, str) else y

资料简介： 3-1 Python-条件语句
资料下载：点击下载
## 3-2 Python循环语句

资料简介： 3-2 Python循环语句，循环遍历就是迭代，break代表休息，take a break
资料下载：点击下载
## 3-3-循环控制语句

资料简介： 3-3-循环控制语句
资料下载：点击下载
## 3-4关键字介绍

资料简介： 3-4关键字介绍
资料下载：点击下载
## 3-5 变量的高级之内存管理

资料简介： 3-5 变量的高级之内存管理
资料下载：点击下载
# 4 函数
## 4-1 函数及函数定义

资料简介： 4-1 函数及函数定义
资料下载：点击下载
## 4-2 函数的参数/全局变量和局部变量

资料简介： 4-2 函数的参数/全局变量和局部变量
资料下载：点击下载
## 4-3 内建函数及递归

资料简介： 4-3 内建函数及递归
资料下载：点击下载
## 4-4 匿名函数

资料简介： 4-4 匿名函数
资料下载：点击下载
## 4-5 函数式编程：map/reduce/filter/sorted/偏函数

资料简介： 4-5 函数式编程：map/reduce/filter/sorted/偏函数
资料下载：点击下载

# 5 Python高级特性及编程规范
## 5-1 列表生成式

列表生成式即List Comprehensions，是Python内置的非常简单却强大的可以用来创建list的生成式。写法简单明了。

语法格式：[exp for iter_var in iterable]

举几个实际的例子

1、[x * x for x in range(1, 11)]

2、[x * x for x in range(1, 11) if x % 2 == 0]

3、[d for d in os.listdir('.')] # os.listdir可以列出文件和目录

4、[k + '=' + v for k, v in d.items()]

5、来做一个练习：
L = ['Java' , 'C' , 'Swift' , 'Python' , 123] ， 现在有 list 中包含字符串，和整数，把list中得大写字符转为小写，推到出另外一个list":

1、使用内建的isinstance函数可以判断一个变量是不是字符串

2、s.lower() 可以将一个大写字母转为小写。

3、增加if语句保证列表生成式正确执行。

代码如下：

L = ['Java' , 'C' , 'Swift' , 'Python' , 123]
print [s.lower() if isinstance(s , str) else s for s in L ]

资料下载：[点击下载](http://note.youdao.com/noteshare?id=fb1e36d1cc8a1aeb700867c60d0d6110)

## 5-2 生成器generator
如何生成generator？yield方法和generator expression
generator的执行过程

> 参考https://www.jb51.net/article/113160.htm
代码执行过程如下：
当调用gen.next(或者send(None))方法时，会激活生成器，直至遇到生成器方法的yield语句。同时，生成器方法的执行被挂起。
当调用close方法时，恢复生成器方法的执行过程。系统在yield语句处抛出GeneratorExit异常，执行过程跳到except语句块。当except语句块处理完毕后，系统会继续往下执行，直至生成器方法执行结束。
在实例化生成器后如果直接调用send()方法启动函数，应该使用send(None)方法，因为此时没有yield表达式可以接收其返回的值。

generator的特点
generator与普通的function的区别
generator基础应用
generator高级应用
【参考】
http://www.cnblogs.com/xybaby/p/6322376.html
https://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000/001432090954004980bd351f2cd4cc18c9e6c06d855c498000
https://www.jb51.net/article/113160.htm 是对廖雪峰文章的解读

## 5-3 迭代器
### 1、概念

可以直接作用于for循环的对象统称为Iterable对象。

可以被next()函数调用并不断返回下一个值的对象称为Iterator。

可以使用isinstance()判断一个对象是否是Iterable对象或者Iterator

isinstance([], Iterable)
isinstance((), Iterable)
isinstance({}, Iterable)
isinstance(set(), Iterable)
isinstance("abc", Iterable)
isinstance((x for x in range(10)), Iterable)
由此可看到，list、tuple、dict、set、str、generator都是Iterable对象

但是只有generator是Iterator对象，但list、dict、str虽然是Iterable，却不是Iterator。
isinstance((x for x in range(10)), Iterator)
isinstance([], Iterator)

把list、dict、str等Iterable变成Iterator可以使用iter()函数
isinstance(iter([]), Iterator)

### 2、Iterator的使用
主要来做迭代。
3.1、可以使用for来迭代
```
#!/usr/bin/python3
list=[1,2,3,4]
it = iter(list)    # 创建迭代器对象
for x in it:
    print(x, end=" ")
```
也可以使用__next__()函数
```
#!/usr/bin/python3
import sys         # 引入 sys 模块
list=[1,2,3,4]
it = iter(list)    # 创建迭代器对象
while True:
    try:
        print(it.__next__())
    except StopIteration:
        sys.exit()
```

### 3、迭代器的作用 
迭代器就是把不同的数据结构 "相同功能 "的函数装到一个名字相同的函数里，这样的话你在写算法的时候就可以不管你要操作的数据结构的逻辑结构了。
比如不管是链表,数组还是别的什么，统一都用迭代器进行访问的话可能都是Next()表示下一个元素，Pre()表示上一个元素等等 。
其实意思就是，不管你用的是链表，2叉树、3叉树、N叉树，还是向量。 迭代器都可以让你从first开始，使用next，到达last，而且一个不漏滴都走一遍。
你不必知道在next的时候，迭代器是怎样从当前节点跳到下一个节点的。
就和猴子一样，你不必知道猴子是怎样从这个树的节点跳到那个树的！总之，猴子可以把树的所有节点跳一边（再次强调：一个不漏）
 
迭代器是：
无论你用的是什么结构（链表也好、数组也好、数也好、图也好、hash表也好），总之， 你可以不关心任何细节遍历细节，（下面看好了） 从一个起点(begin)触发到达，到达终点(end)，并且保证每个节点都能走到且只走一次。

### 4、深入介绍
有了Iterator，我们就可以迭代一个不是序列的对象，因为他表现出了序列的行为。当在python中使用for循环迭代一个对象时，调用者几乎分辨不出他迭代的是一个迭代器对象还是一个序列对象，因为python让他（迭代器）像一个序列那样操作。

本质上说迭代器是个对象，但是这个对象有个特殊的方法next()(在python3中使用__next__()代替了next方法)。当使用for循环来遍历整个对象时候，就会自动调用此对象的__next__()方法并获取下一个item。当所有的item全部取出后就会抛出一个StopIteration异常，这并不是错误的发生，而是告诉外部调用者迭代完成了，外部的调用者尝试去捕获这个异常去做进一步的处理。

不过迭代器是有限制的，例如

- 不能向后移动
- 不能回到开始
- 也无法复制一个迭代器。

因此要再次进行迭代只能重新生成一个新的迭代器对象。

### 5、Iterator的属性
迭代器对象的属性
```
a = [1,2,3,45]
b=iter(a)
dir(b)
```
从输出看
Iterator具有两个特殊的成员方法__iter__()和__next__(),这两个方法便是支持迭代器协议所需要实现的方法。
其中__iter__()方法返回迭代器对象本身，__next__()方法返回容器的下一个元素，直到结尾抛出StopIteration异常。

我们来测试一下这个list_iterator对象的这两个方法:

__iter__()返回的对象就是迭代器对象本身。__next__()方法返回容器中的值直到结尾。

```
b.__iter__()
b is b.__iter__()
b.__next__()
```

### 6、创建Iterator
除了使用iter()函数将内置的序列对象转换成相应的迭代器，我们可以自己实现迭代器协议创建迭代器对象，要实现迭代器协议也就是要在类中实现__iter__()和__next__()方法。

下面我写一个与list_iterator相同行为的迭代器：
```
class ListIter(object):
    def __init__(self, data):
        self.__data = data
        self.__count = 0
 
    def __iter__(self):
        return self
 
    def __next__(self):
        if self.__count < len(self.__data):
            val = self.__data[self.__count]
            self.__count += 1
            return val
        else:
            raise StopIteration
```
我们就可以使用for循环来遍历这个迭代器了：
```
a = ListIter([1,2,3,4,5])
for i in a:
    print(i)
```
对于迭代器对象，使用for循环遍历整个数组其实是个语法糖，他的内部实现还是通过调用对象的__next__()方法。
实际上他内部的工作原理应该是这样的：
```
a = ListIter([1, 2, 3, 4, 5])
 
while True:
    try:
        i = a.__next__()
    except StopIteration:
        break
    // do something in for loop
    print(i)
```
### 7、迭代器支持多次迭代
参考 http://python.jobbole.com/85240/
### 8、可变对象和迭代器
在迭代可变对象时候，一个序列的迭代器只是记录当前到达了序列中的第几个元素，所以如果在迭代过程中改变了序列的元素。更新会立即反应到所迭代的条目上。
我写了个测试看了下，的确：
参考 http://python.jobbole.com/85240/

## 5-4 装饰器

资料简介： 5-4 装饰器
资料下载：点击下载
## 5-5 Python编程规范

资料简介： 5-5 Python编程规范
资料下载：点击下载

# 6 模块的使用
## 6-1 模块名称空间和导入

资料简介： 6-1 模块名称空间和使用
资料下载：点击下载
## 6-2 模块的执行

资料简介： 6-2 模块的执行
资料下载：点击下载
## 6-3 os和sys模块介绍和使用

资料简介： 6-3 os和sys模块介绍和使用，os模块操作文件和目录
资料下载：点击下载，
## 6-4 第三方模块的安装

资料简介： 6-4 第三方模块的安装
资料下载：点击下载
# 7 面向对象编程
## 7-1 类与面向对象设计OOP

资料简介： 7-1 类与面向对象设计OOP
资料下载：点击下载，Page Object模型、类和实例的概念，访问限制，获取对象信息，实例属性和类属性
## 7-2 多态、继承和封装

资料简介： 7-2 多态、继承和封装
资料下载：点击下载
## 7-3 类装饰器

资料简介： 7-3 类装饰器
资料下载：点击下载

## 7-4 使用__slots__
## 7-5 使用@property
## 7-6 多重继承
## 7-7 定制类
## 7-8 使用枚举类
## 7-9 使用元类

# 8 异常、错误类型以及编码

## 8-1异常和警告

资料简介： 8-1异常和警告
资料下载：点击下载
## 8-2 try-except语句和结构

资料简介： 8-2try-except语句和结构
资料下载：点击下载
## 8-3 排查错误方法

资料简介： 8-3 排查错误方法
资料下载：点击下载
## 8-4 编码方式介绍

资料简介： 8-4 编码方式介绍
资料下载：点击下载

# 9 文件处理
## 9-1 文件内建方法：打开和读写

资料简介： 9-1 文件内建方法：打开和读写
资料下载：点击下载
## 9-2文件的存储模块：pickle和marshal

资料简介： 9-2 文件的存储模块：pickle和marshal
资料下载：点击下载
## 9-3Json文件的使用场景及解析

资料简介： 9-3Json文件的使用场景及解析，序列化的概念，参考廖雪峰
资料下载：点击下载

# 10 正则表达式
## 10-1 正则表达式与python

资料简介： 10-1正则表达式与python
资料下载：点击下载
## 10-2 特殊的符号

资料简介： 特殊的符号
资料下载：点击下载
## 10-3 re模块

资料简介： re模块
资料下载：点击下载
# 11 常用内置模块使用
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