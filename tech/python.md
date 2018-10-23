% Python tips

<link id="linkstyle" rel='stylesheet' href='css/markdown.css'/>

[PythonInEmacs](http://emacswiki.org/emacs/PythonProgammingInEmacs)

# String & Coding #
Unicode的目的是将所有语言编码到一套编码里，避免乱码问题。Unicode的标准也在不断发展，最初的标准是用两个字节  
表示一个字符(UTF-16)，如果用到非常生僻的字符就需要4个字节为了传输和存储方面的考虑，出现了可变长的UTF-8编码，  
UTF-8是Unicode的一种实现方式。UTF-8编码把一个Unicode字符根据不同的数字大小编码成1~6个字节，汉字通常是3个字节。  

``` python
print('包含中文的str')
>>> ord('A')
65

>>> ord('中')
20013

>>> chr(25991)
'文'

>>> '\u4e2d\u6587'
'中文'
```

Python的字符串类型是str，在内存中以Unicode表示，一个字符对应若干个字节。
Python对bytes类型的数据用带b前缀的单引号或双引号表示：

``` python
x = b'ABC'
```
但bytes的每个字符都只占用一个字节。以Unicode表示的str通过encode()方法可以编码为指定bytes

``` python
>>> 'ABC'.encode('ascii')
b'ABC'

>>> '中文'.encode('utf-8')
b'\xe4\xb8\xad\xe6\x96\x87'
```

``` python
>>> b'ABC'.decode('ascii')
'ABC'

>>> b'\xe4\xb8\xad\xe6\x96\x87'.decode('utf-8')
'中文'
```

``` python
>>> len('ABC')
3

>>> len('中文')
2
```

len()函数计算的是str的字符串，如果换成bytes，len()函数就计算字节数：

``` python
>>> len(b'ABC')
3

>>> len(b'\xe4\xb8\xad\xe6\x96\x87')
6

>>> len('中文'.encode('utf-8'))
6
```

### 格式化字符串 ###
%d
%f
%s
%x

``` python
>>> print('%2d-%02d' % (3, 1))
>>> print('%.2f' % (3.1415926))
>>> 'Growth %s%%' % 7
```

## List & Tuple ##

Python内置的一种数据类型是列表：list

``` python
>>> classmates = ['Michael', 'Bob', 'Lucy']
>>> classmates
```

``` python
>>> classmates.append('Adam')
>>> classmates

>>> classmates.insert(1, 'Jack')
>>> classmates.pop()

>>> classmates[1] = 'Sarah'
```

``` python
>>> L = ['Apple', 123, True]
>>> s = ['python', 'java', ['asp', 'php'], 'scheme']
>>> len(s)
```

另一种有序列表叫元组：tuple。tuple和list非常相似，但是tuple一旦初始化就不能修改，比如同样是列出同学的名字：

``` python
>>> classmate = ('Michael', 'Bob', 'Tracy')
```

定义只有一个元素的tuple
``` python
>>> t = (1,)
>>> t
```

### 条件判断 ###

``` python
age = 3
if age >= 18:
    print('your age is', age)
    print('adult')
elif age >= 6:
    print('your age is', age)
    print('boy')
else:
    print('baby')
```

``` python
# -*- coding: utf-8 -*-

height = 1.75
weight = 80.5

bmi = weight / (height * height)
print('The bmi is %.2f' % bmi)
if bmi < 18.5:
    print('过轻')
elif bmi < 25:
    print('正常')
elif bmi < 28:
    print('过重')
elif bmi < 32:
    print('肥胖')
else:
    print('严重肥胖')
```

## Loop ##

``` python
names = ['Michael', 'Bob', 'Lucy']
for n in names:
    print(n)
```

* range() 函数, 可以生成一个整数序列。最多可以接受3个参数，数组的范围和步长。

* Python does not support (do ... while) loop, but we can use infinite while and break to implement

``` python
n = 0
while True:
    print n
    if n++ > 10:
        break;
```

## dict & set ##

Python orinally support dictionary or hash map. 

``` python
# -*- coding: utf-8 -*-

d = {'Michael': 95, 'Bob': 75, 'Tracy': 85}
d['Michael']
```
可以通过 **in** 关键字判断

## Built-in Functions & type transform ##

``` python
int('123')
int(12.34)
float('12.34')
str(1.23)
str(100)
bool(1)
bool('')
```

## define Function ##

``` python
def my_abs(x):
    if x >= 0:
        return x
    else:
        return -x
```

* 可变参数

  ``` python
  def calc(*numbers):
      sum = 0
      for n in numbers:
          sum = sum + n * n
      return sum

  calc(1, 2)
  args = [1, 2, 3]
  calc(*args)
  ```
* 关键字参数
  可变参数允许你传入0个或任意个参数，这些参数在函数调用时自动组装为一个tuple。而关键字参数允许你传入0个或任意个含参数名的参数，  
  这些参数在函数内部自动组装为一个dict。

  ``` python
  def person(name, age, **kw):
      print('name: ', name, 'age: ', age, 'other:', kw)

  person('Michael', 30, city='Beijing', job='Engineer')
  ```
* 命名关键字参数

  ``` python
  def person(name, age, *, city, job):
      print('name: ', name, 'age: ', age, 'city:', city, 'job:', job)
  person('Tracy', 26, city='beijing', job='account')
  ```

  ``` python
  def person(name, age, *, city='Beijing', job):
      print(name, age, city, job)
  person('Bob', 32, job='test')
  ```
* 参数组合
  在Python定义函数，可以用必选参数，默认参数，可变参数，关键字参数，命名关键字参数，这5种参数可以组合使用，  
  但是顺序必须是：必选参数，默认参数，可变参数，命名关键字参数，关键字参数

  ``` python
  def f1(a, b, c=0, *args, **kw):
      print('a=', a, 'b=', b, 'c=', c, 'args=', args, 'kw=', kw)
  def f2(a, b, c=0, *, d, **kw):
      print('a=', a, 'b=', b, 'c=', c, 'd=', d, 'kw=', kw)
  ```

## 递归函数 ##

* 尾递归
  return 语句不能包含表达式，返回时调用自身。
  ``` python
  def fact(n):
      return fact_iter(n, 1)

  def fact_iter(num, product):
      if num == 1:
          return product;
      return fact_iter(num - 1, num * product)
  ```

* 汉诺塔

  ``` python
  # _*_ coding: utf-8 _*_
  def move(n, a, b, c):
      print(a, '-->', c)
  else:
      move(n-1, a, c, b)
      move(1, a, b, c)
      move(n-1, b, a, c)
  ```

## Advanced Feature ##

### Slice (切片) ###

``` python
L = ['Michael', 'Sarah', 'Tracy']
print(L[0:3])
print(L[:3])
```

如果切片的参数是范围(:)，返回的类型是数组。如果切片的参数是一个值返回类型就是对象。
* 反向索引，-1 代表最后一个对象

### 迭代 ###
我们可以通过(for...in）遍历

``` python
d = {'a':1, 'b': 2, 'c':3}
for key in d:
    print(key)
```

可以通过Python的内置函数**enumberate**实现把一个list变成索引-元素对，可以在**for**循环中同时迭代索引和元素本身

``` python
for key, value in enumerate(['A', 'B', 'C']):
    print('The index of %d value is %s' % key, value)
```

### 列表生成式 ###

``` python
L = list(range(1, 11))
```

``` python
L = [x * x for x in range(1, 11)]
```

``` python
L = [x * x for x in range(1, 11) if x % 2 == 0]
```

``` python
L = [m + n for m in 'ABC' for n in 'XYZ']
```

``` python
d = {'x': 'A', 'y': 'B', 'z': 'C'}
L = [k + '=' + v for k, v in d.items()]
```

``` python
L1 = ['Hello', 'World', 18, 'Apple', None]
L2 = [ss.lower() for ss in L1 if isinstance(ss, str)]
```

### 生成器 (generator) ###

1. 把一个列表生成式的方括号改为圆括号就创建了一个generator

``` python
g = (x * x for x in range(10))
next(g)
```

2. 如果一个函数定义里包含yield关键字，那么这个函数就是一个generator了

``` python
def fib(max):
    n, a, b = 0, 0, 1
    while n < max:
        yield b
        a, b = b, a + b
        n = n + 1
    return

g = fib(10)

for n in range(1, 11):
    print(next(g))
```

``` python
g = fib(6)
while True:
    try:
        x = next(g)
        print('g:', x)
    except StopIteration as e:
        print('Generator return value:', e.value)
        break;

```

``` python
def triangles():
    

```

# 爬虫 #

非机构化数据

ETL (extract, )
(Raw data, ETL Script, Tidy Data)

