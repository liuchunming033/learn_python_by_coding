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
