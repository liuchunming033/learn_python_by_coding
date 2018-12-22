有时候我们需要使用到列表或者元组中某一些变量时，可以利用序列分解法得到这些变量。
## 1. 将序列分解为单独的变量
序列解包指的是通过赋值操作，将序列中的元素赋值给独立的变量。
比如元组分解，
```python
tuple_num=(1,2,3)
first, second, third = tuple_num
```
再比如列表分解，
```python
list_info=["lily",18,(2010,10,20)]
name,age,birthday=list_info
```
还可以这样，
```python
list_info=["lily",18,(2010,10,20)]
name,age,(year,month,day)=list_info
```
这里要注意的是，变量的个数和元素的个数要一致，否则会得到一个错误提示。
```python
t=(4,5)
x, y, z = t
```
将会得到下面的错误提示：
```bash
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: not enough values to unpack (expected 3, got 2)
```
其实，不仅仅是tuple或者list，只要对象是iterable的，那么就可以进行unpack操作。比如string、file、iterator、generator。
比如解包字符串，
```python
s="Hello"
a,b,c,d,e=s
```
在Python的shell中，执行上面的语句，看看a,b,c,d,e变量中都是什么？
再比如解包文件内容，
```python
f=open(r"/Users/mac/Documents/GitHub/learn_python_by_coding/数据类型/3lines.txt","r")
first,second,third=f.readlines()
print(first,second,third)
f.close()
```
比如，
```python
ite=iter([2,3,45])
i,t,e=ite
print(i,t,e)
```
比如解包生成器generator
```python
g = (x * 2 for x in range(3))
x,y,z=g
print(x,y,z)
```
当做unpack时候，可能想丢弃序列中不需要的值，有种非常简单的办法，就是将想丢弃的值赋值给用不到的变量。
```python
list_info=["lily",18,(2010,10,20)]
name,_,(year,_,_)=list_info
```
这样就是将年龄、出生月份、出生日期这3个值丢弃了。
## 2. 解包任意长度的Iterable对象
看一个例子
```python
record = ("Yoyo","yoyo@example.com","13400000000","18700000000")
x,y,z=record
print(x,y,z)
```
执行上面的语句时，将会收到异常`ValueError: too many values to unpack (expected 2)`
我们可以通过"*表达式"可以用来解决这个问题，改写上面的代码如下:
```python
record = ("Yoyo","yoyo@example.com","13400000000","18700000000")
x,y,*phone_number=record
print(phone_number)
```
如果Iterable对象中有一些连续具有相同意义的数据，比如上面例子record中的后两个元素都是电话号码，使用"*表达式"来unpack这样的模式就非常合适。
使用"*表达式"unpack未知或任意长度的Iterable对象中某些固定模式，我们可以非常轻松得到我们想要的数据。
"*表达式"可以位于第一个位置、最后一个位置或中间任意的位置。
比如，我们对班级中36名同学成绩排序后，对去掉第一名和最后一名的其他成绩计算平均值。
```python
def delete_highest_lowest(grades):
    highest,*middle,lowest = grades
    return avg(middle)
```
"*表达式"可以位于列表的第一个位置。比如，将公司最近一年的销售额和过去7年的销售额的平均值的几倍。
```python
*last_7years_sales,latest_year=(12,13,18,19,14,15,18,10)
avg_comp=sum(last_7years_sales)/len(last_7years_sales)
print(latest_year/avg_comp)
```
*式的语法在迭代一个变长的tuple组成的list时，非常有用。比如，有一个带标签的tuple组成的list，如果标签是foo，则计算tuple中剩余元素的和，如果标签是bar，则打印tuple中剩余的其他元素。
```python
records=[("foo",1,2),("bar","hello"),("foo",3,4)]
for tag,*args in records:
    if tag == "foo":
        print(sum(args))
    elif tag == "bar":
        print(args)
```
*式语法在与特定的字符串处理函数相结合时，也会发挥非常方便的作用。比如想获得ifconfig命令输出的字符串中的ip地址和组播地址:
```python
ip_info="inet 192.168.1.13 netmask 0xffffff00 broadcast 192.168.1.255"
_,ip,*mask,broadcast=ip_info.split(" ")
```
有时候想丢弃分解出来的某一些值，在unpack时，不能仅仅指定单独的*，可以和_组合使用。
比如丢弃上面例子中" netmask 0xffffff00 broadcast "部分。
```python
ip_info="inet 192.168.1.13 netmask 0xffffff00 broadcast 192.168.1.255"
_,ip,*_,broadcast=ip_info.split(" ")
```
