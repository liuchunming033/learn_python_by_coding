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

# generator解决了什么问题
# 什么是generator
# 如何定一个genrator的两种方法
# generator的高级方法
# generator的适用场景

# 1、generator解决了什么问题
通过列表生成式，我们可以直接创建一个列表。但是这里有个问题，受内存限制，列表容量肯定是有限的。
比如创建一个100万个元素的列表，不仅占用很大的存储空间，如果我们仅仅需要访问前面几个元素，那后面绝大多数元素占用的空间都白白浪费了。
我们得想一个办法解决这个问题。
试想一下，如果列表元素可以按照某种算法推算出来，我们可以在循环使用元素的过程中不断推算出后续的元素，这样就不必创建完整的list，从而节省大量的空间。

# 2、什么是generator
在Python中，一边循环一边计算的机制，称为Generator。generator具有可迭代属性。我们可以通过循环来使用它。

# 3、简单生成器
要创建一个generator，有很多种方法。第一种方法很简单，只要把一个列表生成式的[]改成()，就创建了一个generator：
```
import re
from collections import Iterable

import time
from lxml import etree
import requests

l = [x * 2 for x in range(4)]
print("l 是什么对象？", l)

g = (x * 2 for x in range(4))
print("g 是什么对象？", g)
print("g 包含有__iter__属性吗，如果包含则说明其可以迭代。\n", dir(g))
print("g 是可迭代的吗？\n", isinstance(g, Iterable))
```
# 4、如何获取generator的值
如果要一个一个打印出来，可以通过generator的next()方法：
print(g.__next__())
print(g.__next__())
print(g.__next__())
print(g.__next__())
print(g.__next__())

generator保存的是算法，每次调用__next__()，就计算出下一个元素的值，直到计算到最后一个元素，没有更多的元素时，抛出StopIteration的异常。
这种不断调用next()方法实在是太变态了，实际很少用。因为generator是可以迭代的，所以我们可以使用for循环来读取元素。
print("使用for来读取generator数据，先把上面的__next__()语句注释掉")


# for i in g:
#     print(i)


# 5、yield生成器
# 举个简单的例子，定义一个generator，依次返回数字1，3，5
def odd():
    print("step1")
    yield 1
    print("step2")
    yield 3
    print("step3")
    yield 5


# 5.1、我们说generator适合返回那些使用某种算法推算的情况，修改一下，找个简单的推算算法，下一个元素比前一个元素少1（哈哈）
def countdown(n):
    print("counting down")
    while n > 0:
        print("n is ", n)
        yield n  # 生成一个n值
        n -= 1  # 根据推算算法推算


# 5.2、在举个例子，斐波拉契数列，这个要比前面的那个推算规则复杂一些。但是只要是元素之间有推算规则，就适合用generator
def fib(bound):
    n = 0
    a, b = 0, 1
    while n < bound:
        yield a  # 生成一个值
        a, b = b, a + b  # 根据推算算法推算下一个元素
        n += 1


# 当generator被调用的时候，遇到yield就会中止，当再次被调用时，将generator继续执行yield之后的语句，直到再次遇到yield中止。
# 通过5.1和5.2发现，包含yield关键字的generator，也不难，就是在一个循环中，yield一个值，然后在下一条语句，写推算算法就好了。


# 6、加强的生成器
# 前面使用generator主要是从中取数据，我们还可以给generator中传数据进去。
# 给generator传数据，主要是通过generator的send方法给yield表达式赋值。
# 在generator中定义一个变量，接收yield表达式的值，就可以对这个变量进行操作了，从而控制generator的行为。举个例子

def gen(x):
    count = x
    while True:
        val = (yield count)
        if val is not None:
            count = val
        else:
            count += 1


# 6.1、再举个例子，generator可以接收调用者的参数，这个参数将赋值给yield表达式。
def h(n):
    while n > 0:
        m = (yield n)
        print("m is " + str(m))
        n -= 1
        print("n is " + str(n))


# 7、yield实际用处
# 7.1、实现在单线程的情况下实现并发运算，实现了生产者和消费中的并发，明显地看到两个任务的打印是你一次我一次,即并发执行的.
# 从时间上可以看出并发效果（可以将produce的while循环设置多点，更方便看出并发效果）
def consumer():
    r = ''
    while True:
        n = yield r
        print("[Consumer] 收到第{}个包子 @{}".format(n, int(time.time())))
        if not n:
            return
        print("[Consumer] 吃包子 {}...".format(n))
        r = '我吃完了'


def produce(cc):
    cc.send(None)  # 1、启动generator，consumer从代码第一行执行到yield停下来，接着执行produce()中接下来的代码
    x = 0
    while x < 1000:
        x += 1
        print("[Producer] 生产第 %s 个包子, @%s" % (x, int(time.time())))
        s = cc.send(
            x)  # 2、给consumer的yield表达式传递参数x（相当于把包子送给顾客），consumer接着上一次暂停处往下继续执行，r最终变成"我吃完了"，接着循环遇到yield，consumer()函数又暂停并且返回变量r的值，此时程序又进入produce(c)函数中接着执行，s收到consumer yield出来的值
        print("[Producer] 顾客说: %s" % s)
    cc.close()


# 7.2、生成器的实际运用
# 提取目标内容并且格式化

def parse_one_page(html):
    pattern = re.compile(
        '<dd>.*?index.*?>(.*?)</i>.*?<img data-src="(.*?)".*?</a>.*?name"><a.*?>(.*?)</a>.*?star">(.*?)</p>.*?releasetime">(.*?)</p>.*?integer">(.*?)</i>.*?fraction">(.*?)</i>',
        re.S)
    items = re.findall(pattern, html)  # 得到所有电影信息列表
    for item in items:
        yield {  # 每次被调用返回yield后面的参数 这里是一个字典(代表一条电影信息)
            'index': item[0],
            'image': item[1],
            'title': item[2].strip(),
            'actor': item[3].strip()[3:] if len(item[3]) > 3 else '',
            'time': item[4].strip()[5:] if len(item[4]) > 5 else '',
            'score': item[5].strip() + item[6].strip()
        }


# 爬取一个网页
def main(offset):
    maoyan_url = 'http://maoyan.com/board/4?offset=' + str(offset)
    html = get_one_page(maoyan_url)
    for item in parse_one_page(html):  # Parse_one_page(html)是一个个可迭代对象 实质上是个生成器
        print(item)


# 7.3、爬虫
# 定一个generator，接受简书用户的唯一标识符，先获取用户当前的文章数，然后通过文章数计算出页面数
# 再根据页面数来生成对应用户的文章列表的链接

# url生成器
def urls_generator(uid):
    # 设置请求头
    headers = {
        'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/66.0.3359.117 Safari/537.36'
    }
    r = requests.get('https://www.jianshu.com/u/{}?order_by=shared_at&page={}'.format(uid, 1), headers=headers)
    dom = etree.HTML(r.text)

    # 获取文章数量和最大页数
    article_num = int(dom.xpath('//div[@class="info"]//li[3]//p/text()')[0].strip())
    print(article_num)
    max_page_num = article_num / 9

    i = 1
    while True:
        yield 'https://www.jianshu.com/u/{}?order_by=shared_at&page={}'.format(uid, i)
        if i >= max_page_num:
            break
        i += 1


# 7.4、监控日志中的500错误。 因为日志文件很难知道什么时候结束，对于这样的情况非常适合使用generator。
def tail(file_path):  # 定义一个查看文件的函数
    with open(file_path, 'rb') as f:  # 打开形参为filepath rb是二进制读
        f.seek(0, 2)  # 把光标移动到末尾
        while True:  # 循环监控日志
            data = f.readline()  # 读取文件末尾
            if data:  # 加入有数据就用yield返回
                yield data
            else:  # 否则就睡眠0.05秒
                time.sleep(0.05)


def grep(file, k):  # 定义过滤关键字函数
    for i in tail(file):  # 循环生成器中的数据
        if k in i.decode('utf-8'):  # 因为是用二进制读取方式，所以需要解码显示
            print(i.decode('utf-8'))
grep('a.txt', '500')  # 监控a.txt最新日志，并过滤500的错误代码，一旦有500出现就会被抓拍到

if __name__ == '__main__':
    # o = countdown(3)
    # o = fib(5)
    # for i in o:
    #     print(i)
    # f = gen(5)
    # print(f.__next__())
    # print(f.__next__())
    # print(f.__next__())
    # print(f.send(9))  # f.send(9)，在yield出数据，然后给yield表达式赋值，接着执行下面的语句
    # print(f.__next__())
    # print(f.__next__())
    # f.close()
    # print(f.__next__())  # close之后再次调用，会报StopIteration异常
    #
    # p = h(5)
    # print(p.__next__())
    # print(p.__next__())
    # print(p.send("test"))
    c = consumer()  # 创建一个生成器
    produce(c)  # 在该函数中，调用生成器的send()方法

    my_uid = '9bc194fde100'
    urls = urls_generator(my_uid)
    for url in urls:
        print(url)
