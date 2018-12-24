% Python tips

<link id="linkstyle" rel='stylesheet' href='css/markdown.css'/>

[Python Programming In Emacs](https://www.emacswiki.org/emacs/PythonProgrammingInEmacs)
[elpy](https://elpy.readthedocs.io/en/latest/index.html)

# Environment setup #

``` shell
# Either of these
pip install rope
pip install jedi
# flake8 for code checks
pip install flake8
# and autopep8 for automatic PEP8 formatting
pip install autopep8
# and yapf for code formatting
pip install yapf
```

``` shell
python3 -m pip install --upgrade pip
python3 -m pip install jupyter
```

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

## 格式化字符串 ##

%d
%f
%s
%x

``` python
>>> print('%2d-%02d' % (3, 1))
>>> print('%.2f' % (3.1415926))
>>> 'Growth %s%%' % 7
```

# List & Tuple #

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

# 条件判断 #

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

# Loop #

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

# dict & set #

Python orinally support dictionary or hash map. 

``` python
# -*- coding: utf-8 -*-

d = {'Michael': 95, 'Bob': 75, 'Tracy': 85}
d['Michael']
```
可以通过 **in** 关键字判断

# Built-in Functions & type transform #

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

# Advanced Feature #

## Slice (切片) ##

``` python
L = ['Michael', 'Sarah', 'Tracy']
print(L[0:3])
print(L[:3])
```

如果切片的参数是范围(:)，返回的类型是数组。如果切片的参数是一个值返回类型就是对象。
* 反向索引，-1 代表最后一个对象

## 迭代 ##

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

## 列表生成式 ##

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

## 生成器 (generator) ##

1. 把一个列表生成式的方括号改为圆括号就创建了一个generator

``` python
g = (x * x for x in range(10))
next(g)
```

1. 如果一个函数定义里包含yield关键字，那么这个函数就是一个generator了

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

* 杨辉三角

``` python
def triangles():
    origin = []
    while True:
        result = origin[:]
        if len(origin) > 1:
            for i in range(1: len(origin)):
                result[i] = origin[i - 1] + origin[i]
        result.append(1)
        yield result
        origin = result[:]

results = []
for t in triangles():
    print(t)
    results.append(t)
    n = n + 1
    if n == 10:
        break

```

## 迭代器（Iterator） ##

可用于for循环的数据类型有：
1. 集合数据类型，list，tuple，dict，set，str等
2. generator，包括生成器和带yield的generator function
这些可以直接作用于for循环的对象成为可迭代对象：Iterable
可以使用isinstance()函数判断一个对象是否Interable对象

``` python
from collections import Iterable

isinstance([], Iterable)
True

isinstance({}, Iterable)
True

isinstance('abc', Iterable)
True

isinstance((x for x in range(10)), Iterable)
True


isinstance([], Iterator)
False

isinstance({}, Iterator)
False

isinstance('abc', Iterator)
False

isinstance((x for x in range(10)), Iterator)
True
```

可以通过iter函数获取一个Iterator对象

``` python
it = iter([1, 2, 3, 4, 5])

while True:
    try:
        x = next(it)
        print('value is ', x)
    except StopIteration as e:
        print('Error occurred while Iteration')
        break

```

# 函数式编程（Functional Programming） #

## 高阶函数（High-order function） ##

函数名也是变量，把函数作为参数传入，这样的函数称为高阶函数。

* map/reduce
[MapReduce: Simplified Data Processing on Large Clusters](https://ai.google/research/pubs/pub62)

``` Pseudocode
map(String input_key, String input_value):
    // input_key: document name
    // input_value: document contents
    for each word w in input_value:
        EmitIntermediate(w, "1");

reduce(String output_key, Iterator intermediate_values):
    // output_key: a word
    // output_values: a list of counts
    int result = 0;
    for each v in intermediate_vlaues:
        result += ParseInt(v);
    Emit(AsString(result));
```

Python内建了map()和reduce()函数，map函数接受两个参数(一个函数，一个Iterable)，map将传入的函数一次作用到每个元素，并把元素作为新的Iterator返回。

``` python
def f(x):
    return x * x
r = map(f, [1, 2, 3, 4, 5, 6, 7, 8, 9])
list(r)
```

再看reduce函数的用法，reduce函数把一个函数作用在一个序列[x1, x2, x3, ...]上，这个函数必须接收两个参数，  
reduce把结果继续和序列的下一个元素做累计计算  

``` python
reduce(f, [x1, x2, x3, x4]) = f(f(f(x1, x2), x3), x4)
```

1. map(function, iterable, ..)
  Return an iterator that applies function to every item of iterable, yielding the results. If additional iterable  
  arguments are passed, function must take that many arguments and is applied to the items form all iterables in  
  parallel. With multiple iterables, the iterator stops when the shortest iterable is exhausted. For cases where  
  the function inputs are already arranged into argument tuples.  

2. functools.reduce(function, iterable[, initilizer])
  Apply function of two arguments cumulatively to the items of sequence, from left to right, so as to **reduce** the  
  sequence to a single value. For example, **reduce(lambda x, y: x+y, [1, 2, 3, 4, 5])** calculates ((((1 + 2) + 3) + 4) + 5)  

* filter
  Python 内建的filter()函数用于过滤序列。参数与map()类似，filter()也是接收一个函数和一个序列。

  ``` python
  def is_odd(n):
      return n % 2 == 1
  list(filter(is_odd, [1, 2, 3, 4, 5, 6, 9, 10, 15]))
  ```

* sorted
  Python 内建的函数sorted()可以对list进行排序

  ``` python
  sorted(['bob', 'about', 'Zoo', 'Credit'], key=str.lower)
  ```

## 返回函数 ##

* 闭包
一、在内部函数内修改外部函数局部变量的两种方法

1法：把外部变量变成容器或者说可变变量
``` python
def createCounter():
    a = [0]
    def counter():
        a[0] += 1
        return a[0]
    return counter
```

2法：在内部函数里给予外部函数局部变量nonlocal声明，让内部函数去其他领域获取这个变量
``` python
def createCounter():
    a = 0
    def counter():
        nonlocal a
        a += 1
        return a
    return counter
```

二、在内部函数内修改全局变量
``` python
def createCounter():
    global a
    a = 0
    def counter():
        global a
        a += 1
        return a
    return counter

```

## 匿名函数 (lambda) ##

* 匿名函数有一个限制，只能有一个表达式，不用写return，返回值就是表达式的结果

## 装饰器 ##

* 函数也是一个对象，可以赋值给一个变量。
* 函数对象有一个属性("__name__")

``` python
def now():
    print('2018-10-24')

f = now
f()

print now.__name__
```

* 装饰器
``` python
def log(func):
    def wrapper(*args, **kw):
        print('call %s():' % func.__name__)
        return func(*args, **kw)
    return wrapper

@log
def now():
    print('2018-10-24')
```
``` python
now = log(now)
```

* 带参数的装饰器
``` python
def log(text):
    def decorator(func):
        def wrapper(*args, **kw):
            print('%s %s():' % (text, func.__name__))
            return func(*args, **kw)
        return wrapper
    return decorator

@log('execute')
def now():
    print('2018-10-24')
```
``` python
now = log('execute')(now)
```

* 完整的docorator

``` python
import functools

def log(func):
    @functools.wraps(func)
    def wrapper(*args, **kw):
        print('call %s():' % func.__name__)
        return func(*args, **kw)
    return wrapper
```

``` python
def metric(fn):
    @functools.wraps(fn)
    def wrapper(*args, **kw):
        tstart = time.time()
        ret = fn(*args, **kw)
        print('%s executed in %s ms' % (fn.__name__, time.time() - tstart))
        return ret
    return wrapper
```

* Summary
  在面向对象(OOP)的设计模式中，decorator被称为装饰模式。OOP的装饰模式需要通过继承和组合来实现，而Python除了  
  能支持OOP的decorator外，直接从语法层次支持decorator。Python的decorator可以用函数实现，也可以用类实现。  

## 偏函数(Partial function) ##

``` python
import functools
int2 = functools.partial(int, base=2)
int2('1000000')
int2('1010101')
```

## 模块 ##

使用模块可以提高代码的可维护性。使代码重用。Python还引入按目录来组织模块的方法，称为Package。  
注意每个包目录下都会有一个`__init__.py`的文件，这个文件必须存在，否则，Python就把这个目录当成普通目录，而不是一个包。  
`__init__.py`可以是空文件，也可以有Python代码

``` python
#!/usr/bin/env python3
#_*_ coding: utf-8 _*_

' a test module '

__author__ = 'xxx'

import sys

def test():
    args = sys.argv
    if len(args) == 1:
        print('Hello world!')
    elif len(args) == 2:
        print('Hello, %s!' % args[1])
    else:
        print('Too many arguments!')

if __name__ == '__main__':
    test()

```

* 作用域
  变量通过使用下划线的命名规则来定义是否可以从外部访问

  ``` python
  def _private1(name):
      return 'Hello, %s' % name

  def _private2(name):
      return 'Hi, %s' % name

  def greeting(name):
      if len(name) > 3:
          return _private1(name)
      else:
          return _private2(name)
  ```

# 面向对象编程 #

``` python
class Student(object):
    def __init__(self, name, score):
        self.name = name
        self.score = score
    def print_score(self):
        print('%s : %s' % (self.name, self.score))

me = Student('Albert', 96)
me.print_score()
```

* type()

``` python
import types

def fn():
    pass

type(fn) == types.FunctionType
True

type(abs) == types.BuiltinFunctionType
True

type(lambda x: x) == types.LambdaType
True

type(x for x in range(10)) == types.GeneratorType
True

```

* isinstance()
`object -> Animal -> Dog -> Husky`

``` python
a = Animal()
d = Dog()
h = Husky()

isinstance(h, Husky)
True

isinstance(h, Dog)
True

isinstance(h, Animal)
True

isinstance(d, Husky)
False
```
能用type()判断的也可以用isinstance()判断

``` python
isinstance('a' str)
True

isinstance(123, int)
True

isinstance(b'a', bytes)
True
```
* dir()
  获取一个对象的所有属性和方法，可以使用`dir()`函数，它返回一个包含字符串的list，比如，获得一个str对象的所有属性和方法

``` python
dir('AAA')
['__add__', '__class__',..., '__subclasshook__', 'capitalize', 'casefold',..., 'zfill']
```

* getattr(), setattr(), hasattr()

``` python
class MyObject(object):
    def __init__(self):
        self.x = 9
    def power(self):
        return self.x * self.x

obj = MyObject()

hasattr(obj, 'x')
True

hasattr(obj, 'y')
False

setattr(obj, 'y', 19)
hasattr(obj, 'y')
True

getattr(obj, 'y')
19
```

## 实例属性和类属性 ##

``` python
class Student(object):
    count = 0

    def __init__(self, name):
        self.name = name
        Student.count += 1
```

# 面向对象高级 #

## 使用 __slots__ ##
我们想限制实例的属性，比如只允许Student实例添加`name`和`age`属性。
为了达到限制的目的，Python允许定义class的时候，定义一个特殊的变量`__slots__`，来限制class实例能添加的属性：

``` python
class Student(object):
    __slots__ = ('name', 'age')
```

## 使用@property ##
Python内置@property装饰器就是负责把一个方法编程属性调用。

``` python
class Student(object):

    @property
    def score(self):
        return self._score

    @score.setter
    def score(self, value):
        if not isinstance(value, int):
            raise ValueError('score must be an integer')
        if value < 0 or value > 100:
            raise ValueError('score must between 0 ~ 100')
        self._score = value
```

## 多重继承 ##

``` python
class Animal(object):
    pass

class Mammal(Animal):
    pass

class Bird(Animal):
    pass

class Runnable(object):
    def run(self):
        print('running...')

class Flyable(object):
    def fly(self):
        print('flying...')

class Dog(Mammal, Runnable):
    pass
```

## 定制类 ##

* __str__
``` python
class Student(object):
    def __init__(self, name):
        self._name = name

    def __str__(self):
        return 'Student object (name=%s)' % self.name

    @property
    def name(self):
        return self._name

    __repr__ = __str__

```

* __iter__
如果一个类想被用于(for...in)循环，就必须实现一个__iter__()方法，该方法返回一个迭代对象，然后，Python的`for`循环就会不断  
调用迭代对象的__next__()方法拿到循环的下一个值，直到遇到StopIteration错误时推出循环。  

``` python
class Fib(object):
    def __init__(self):
        self.a, self.b = 0, 1

    def __iter__(self):
        return self

    def __next__(self):
        self.a, self.b = self.b, self.a + self.b
        if self.a > 10000:
            raise StopIteration()
        return self.a

for n in Fib():
    print(n)
```

* __getitem__, __setitem__, __delitem__

``` python
class Fib(object):
    def __getitem__(self, n):
        if isinstance(n, int):
            a, b = 1, 1
            for x in range(n):
                a, b = b, a + b
            return a
        elif isinstance(n, range):
            start = n.start
            stop = n.stop
            if start is None:
                start = 0
            a, b = 1, 1
            L = []
            for x in range(stop):
                if x >= start:
                    L.append(a)
                a, b = b, a + b
            return L
f = Fib()
f[0]
f[1]
f[:10]
```

* __getattr__

``` python
class Student(object):

    def __init__(self):
        self.name = 'Albert'

    def __getattr__(self, attr):
        if attr == 'score':
            return 99

s = Student()
s.name
# 'Albert'
s.score
# 99
```

可以使用__getattr__实现级联调用  

``` python
class Chain(object):
    def __init__(self, path=''):
        self._path = path

    def __getattr__(self, path):
        return Chain('%s/%s' % (self._path, path))

    def __str__(self):
        return self._path

    __repr__ = __str__
```

* __call__

``` python
class Student(object):
    def __init__(self, name):
        self.name = name

    def __call__(self):
        print('My name is %s.' % self.name)

s = Student('Albert')
s()
# My name is Albert.
```


### 使用枚举类 ###

``` python
from enum import Enum

Mouth = Enum('Month', ('Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'))

for name, member in Month.__members__.items():
    print(name, '=>', member, ', ', member.value)
```

自定义枚举值

``` python
from enum import Enum, unique

@unique
class Weekday(Enum):
    Sun = 0
    Mon = 1
    Tue = 2
    Wed = 3
    Thu = 4
    Fri = 5
    Sat = 6
```
`@unique` 保证没有重复值

``` python
day1 = Weekday.Mon
print(day1)

print(Weekday.Tue)
print(Weekday['Tue'])
print(Weekday.Tue.value)
print(Weekday(1))
```

## 使用元类 ##

* type()
  使用type()函数创建类

``` python
def fn(self, name='world'):
    print('Hello, %s.' % name)

Hello = type('Hello', (object,), dict(hello-fn))
```

* metaclass
  使用metaclass创建类，再使用创建的类创建对象。

``` python
class ListMetaclass(type):
    def __new__(cls, bases, attrs):
        attrs['add'] = lambda self, value: self.append(value)
        return type.__new__(cls, name, bases, attrs)

class MyList(list, metaclass=ListMetaclass):
    pass
```

当我们传入关键字参数metaclass时，魔术就生效了，它指示Python解释器在创建MyList时，要通过ListMetaclass.__new__()来创建。
__new__()方法接收到的参数依次是：
1. 当前准备创建的类的对象；
2. 类的名字；
3. 类继承的父类集合；
4. 类的方法集合。

* 使用metaclass的场景在ORM（Object Relational Mapping），即对象-关系数据库的一行映射为一个对象，也就是一个类对应一个表。

``` python
class User(Model):
    id = Integer('id')
    name = StringField('username')
    email = StringField('email')
    password = StringField('password')

u = User(id=12345, name='Albert', email='test@orm.org', password='pwd')
u.save()
```

``` python
class Field(object):

    def __init__(self, name, column_type):
        self.name = name
        self.column_type = column_type

    def __str__(self):
        return '<%s:%s>' % (self.__class__.__name__, self.name)

class StringField(Field):
    def __init__(self, name):
        super(StringField, self).__init__(name, 'varchar(100)')

class IntegerField(Field):
    def __init__(self, name):
        super(IntegerField, self).__init__(name, 'biginit')

class ModelMetaclass(type):
    def __new__(cls, name, bases, attrs):
        if name == 'Model':
            return type.__new__(cls, name, bases, attrs)
        print('Found model: %s' % name)
        mappings = dict()
        for k, v in attrs.items():
            if isinstance(v, Field):
                print('Found mapping: %s ==> %s' % (k, v))
                mappings[k] = v

        for k in mappings.keys():
            attrs.pop(k)
        attrs['__mappings__'] = mappings
        attrs['__table__'] = name
        return type.__new__(cls, name, bases, attrs)

class Model(dict, metaclass=ModelMetaclass):
    def __init__(self, **kw):
        super(Model, self).__init__(**kw)

    def __getattr__(self, key):
        try:
            return self[key]
        except KeyError:
            raise AttrbuteError(r"'Model' object has no attribute '%s'" % key)

    def __setattr__(self, key, value):
        self[key] = value

    def save(self):
        fields = []
        params = []
        args = []
        for k, v in self.__mappings__.items():
            fields.appends(v.name)
            params.append('?')
            args.append(getattr(self, k, None))
        sql = 'insert into %s (%s) values (%s)' % (self.__talbe__, ','.join(fields), ','.join(params))
        print('SQL: %s' % sql)
        print('ARGS: %s' % str(args))
```

# 错误，调试和测试 #

## 错误处理 ##

``` python
try:
    print('try...')
    r = 10 / int('2')
    print('result: ', r)
except ValueError: as e:
    print('ValueError: ', e)
except ZeroDivisionError as e:
    print('except: ', e)
else:
    print('no error!')
finally:
    print('finally...')
print('END')
```

* 记录错误

``` python
import logging

def foo(s):
    return 10 / int(s)

def bar(s):
    return foo(s) * 2

def main():
    try:
        bar('0')
    except Exception as e:
        logging.exception(e)
```

* 抛出错误

``` python
class FooError(ValueError):
    pass

def foo(s):
    n = int(s)
    if n == 0:
        raise FooError('invalid value: %s' % s)
    return 10 / n

foo('0')
```

## 调试 ##

* assert

``` python
def foo(s):
    n = int(s)
    assert n != 0, 'n is zero!'
    return 10 / n

def main():
    foo('0')
```

* logging
使用logging替换print()是第三种方式， logging不会抛出异常，但可以输出到文件

``` python
import logging

s = '0'
n = int(s)
logging.info('n = %d' % n)
print(10 / n)
```

`logging.basicConfig(level=logging.INFO)`

* pdb
启动Python的调试器pdb，让程序以单步方式运行，可以随时查看运行状态。

## 单元测试 ##

``` python
import unittest

from mydict import Dict

class TestDict(unittest.TestCase):

    def setUp(self):
        print('setup')

    def tearDown(self):
        print('tearDown')

    def test_init(self):
        d = Dict(a=1, b='test')
        self.assertEqual(d.a, 1)
        self.assertEqual(d.b, 'test')
        self.assertTrue(isinstance(d, dict))

    def test_key(self):
        d = Dict()
        d['key'] = 'value'
        self.assertEqual(d.key, 'value')

    def test_attr(self):
        d = Dict()
        d.key = 'value'
        self.assertTrue('key' in d)
        self.assertEqual(d['key'], 'value')

    def test_keyerror(self):
        d = Dict()
        with self.assertRaises(KeyError):
            value = d['empty']

    def test_attrerror(self):
        d = Dict()
        with self.assertRaises(AttributeError):
            value = d.empty
```

``` python
if __name__ == '__main__':
    unittest.main()
```

## 文档测试 ##

``` python
def fact(n):
    '''
    Calculate 1*2*...*n

    >>> fact(1)
    1
    >>> fact(10)
    3628800
    >>> fact(-1)
    Traceback (most recent call last):
    ...
    ValueError
    '''
    if n < 1:
        raise ValueError()
    if n == 1:
        return 1
    return n * fact(n - 1)

if __name__ == '__main__':
    import doctest
    doctest.testmod()
```

# IO编程 #

## 文件读写 ##

``` python
try:
    f = open('/Users/liangchao/temp/logs/face.log', r)
    print(f.read())
except IOError as e:
    print('exception: ', e)
finally:
    if f:
        f.close()
```

``` python
with open('/Users/liangchao/temp/logs/face.log', r) as f:
    print(f.read())
```

``` python
for line in f.readlines():
    print(line.strip())
```

* file-link object
  像open()函数返回的这种有个read()方法的对象，在Python中统称为file-like Object。  
  除了file外，还可以是内存的字节流，网络流，自定义流等等。file-like Object不要求从特定类继承，只要写个read()方法就行。  
  StringIO就是在内存中创建的file-like Object，常用作临时缓冲。  

* 字符编码
``` python
f = open('/Users/liangchao/temp/logs/face.log', 'r', encoding='gbk')
f.read()
```

* 写文件
``` python
with open('Users/liangchao/temp/logs/face.log', 'w') as f:
    f.write('Hello, world!')
```

## StringIO 和 BytesIO ##
* StringIO就是在内存中读写String

``` python
from io import StringIO

f = StringIO()
f.write('hello')
5

f.write(' ')
1

f.write('world!')
6

print(f.getValue())
hello world!
```

``` python
from io import StringIO
f = StringIO(u'Hello!\nHi!\nGoodbye!')

while True:
    s = f.readline()
    if s == '':
        break
    print(s.strip())
```
* BytesIO实现了内存中读写bytes

``` python
from io import BytesIO
f = BytesIO()
f.write(‘中文’.encode('utf-8'))

print(f.getvalue())
```

## 操作文件和目录 ##

``` python
import os

os.name
os.uname() # 在windows系统上不提供
```
* 环境变量
``` python
os.environ
os.environ.get('PATH')
```

* 操作文件和目录

``` python
# 查看当前绝对路径
os.path.abspath('.')
# 在某个目录下创建一个新目录
os.path.join('/Users/liangchao/', 'testdir')
os.mkdir('/Users/liangchao/testdir')
os.rmdir('/Users/liangchao/testdir')

# 拆分路径
os.path.splittext('/path/to/file.txt')
('/path/to/file', '.txt')

# 文件重命名
os.rename('test.txt', 'test.py')
os.remove('test.py')
```

``` python
import shutil
```

``` python
[x for x in os.listdir('.') if os.path.isdir(x)]
```

``` python
[x for x in os.listdir('.') if os.path.isfile(x) and os.path.splitext(x)[1]=='.py']
```

## 序列化 ##
Python提供了**pickle**模块来实现序列化

``` python
import pickle

f = open('dump.txt', 'wb')
d = dict(name='Bob', age=20, score=88)
pickle.dumps(d, f)
f.close()

f = open('dump.txt', 'rb')
pickle.load(f)
f.close()
d
```
* JSON

``` python
import json

d = dict(name='Bob', age=20, score=88)
json.dumps(d)

json_str = '{"age": 20, "score": 88, "name": "Bob"}'
json.loads(json_str)
```

``` python
def student2dict(std):
    return {
        'name': std.name,
        'age': std.age,
        'score': std.score
    }
```

# 进程和线程 #

## 多进程 ##

``` python
import os

print('Process (%s) start...' % os.getpid())

pid = os.fork()
if pid == 0:
    print('I am child process (%s) and my parent is %s.' % (os.getpid(), os.getppid()))
else:
    print('I (%s) just created a child process (%s).' % (os.getpid(), pid))

```

* multiprocessing

``` python
from multiprocessing import Process
import os

def run_proc(name):
    print('Run child process %s (%s)...' % (name, os.getpid()))

if __name__ == '__main__':
    print('Parent process %s.' % os.getpid())
    p = Process(target=run_proc, args=('test',))
    print('Child process will start.')
    p.start()
    p.join()
    print('Child process end.')
```
> join()方法可以等待子进程结束后再继续往下运行，通常用于进程间的同步。

* Pool
> 如果要启动大量的子进程，可以用进程池方式批量创建子进程  

``` python
from multiprocessing import Pool
import os, time, random

def long_time_task(name):
    print('Run task %s (%s)...' % (name, os.getpid()))
    start = time.time()
    time.sleep(random.random() * 3)
    end = time.time()
    print('Task %s runs %0.2f seconds.' % (name, (end - start)))

if __name__=='__main__':
    print('Parent process %s.' % os.getpid())
    p = Pool(4)
    for i in range(5):
        p.apply_async(long_time_task, args=(i,))
    print('Waiting for all subprocesses done...')
    p.close()
    p.join()
    print('All subprocesses done.')
```
> 对Pool对象调用join()方法会等待所有子进程执行完毕，调用join()之前必须先调用close()，调用close()之后就不能继续添加新的Process了。  

* 子进程

``` python
import subprocess

print('$ nslookup www.python.org')
r = subprocess.call(['nslookup', 'www.python.org'])
print('Exit code:', r)
```

``` python
import subprocess

print('$ nslookup')
p = subprocess.Popen(['nslookup'], stdin=subprocess.PIPE, stdout=subprocess.PIPE, stderr=subprocess.PIPE)
output, err = p.communicate(b'set q=mx\npython.org\nexit\n')
print(output.decode('utf-8'))
print('Exit code:', p.returncode)
```

* 进程间通信
> Process之间肯定是需要通信的，操作系统提供了很多机制来实现进程间的通信。Python的multiprocessing模块包装了底层的机制，提供了Queue、Pipes等多种方式来交换数据。
> 我们以Queue为例，在父进程中创建两个子进程，一个往Queue里写数据，一个从Queue里读数据：

``` python
from multiprocessing import Process, Queue
import os, time, random

# 写数据进程执行的代码
def write(q):
    print('Process to write: %s' % os.getpid())
    for value in ['A', 'B', 'C']:
        print('Put %s to queue...' % value)
        q.put(value)
        time.sleep(random.random())

# 读数据进程执行的代码
def read(q):
    print('Process to read: %s' % os.getpid())
    while True:
        value = q.get(True)
        print('Get %s from queue.' % value)

if __name__ == '__main__':
    q = Queue()
    pw = Process(target=write, args=(q,))
    pr = Process(target=read, args=(q,))

    pw.start()
    pr.start()
    # 等待pw进程结束
    pw.join()
    # pr进程里是死循环，无法等待其结束，只能强行终止
    pr.terminate()
```

## 多线程 ##
Python标准库提供了两个模块：_thread和threading，_thread是低级模块，threading是高级模块，对_thread进行了封装。绝大多数情况下，我们只需要使用  
threading这个高级模块。

``` python
import time, threading

def loop():
    print('thread %s is running...' % threading.current_thread().name)
    n = 0
    while n < 5:
        n = n + 1
        print('thread %s >>> %s' % (threading.current_thread().name, n))
        time.sleep(1)
    print('thread %s is running...' % threading.current_thread().name)

print('thread %s is running...' % threading.current_thread().name)
t = threading.Thread(target=loop, name='LoopThread')
t.start()
t.join()
print('thread %s ended.' % threading.current_thread().name)
```

* Lock

``` python
import time, threading

balance = 0
lock = threading.Lock()

def change_it(n):
    global balance
    lock.acquire()
    try:
        balance = balance + n
        balance = balance - n
    finally:
        lock.release()

def run_thread(n):
    for i in range(10000):
        change_it(n)

t1 = threading.Thread(target=run_thread, args=(5,))
t2 = threading.Thread(target=run_thread, args=(8,))

t1.start()
t2.start()
t1.join()
t2.join()
print(balance)
```

* 多核CPU

``` python
import threading, multiprocessing

def loop():
    x = 0
    while True:
        x = x ^ 1

for i in range(multiprocessing.cpu_count()):
    t = threading.Thread(target=loop)
    t.start()
```
因为Python解释器执行代码时有一个GIL(Global Interpreter Lock)锁，任何Python线程执行前，必须先获得GIL锁，然后，没执行100条字节码，  
解释器就自动释放GIL锁，让别的线程有机会执行。所以，多线程在Python中只能交替执行。即使100个线程跑在100核CPU上，也只能用到一个核。  
GIL是Python解释器设计的历史遗留问题，通常我们用的解释器是官方实现的CPython，要真正利用多核，除非重写一个不带GIL的解释器。  

## ThreadLocal ##

``` python
import threading

local_school = threading.local()

def process_student():
    std = local_school.student
    print('Hello, %s (in %s)' % (std, threading.current_thread().name))

def process_thread(name):
    local_school.student = name
    process_student()

t1 = threading.Thread(target=process_thread, args=('Alice',), name='Thread-A')
t2 = threading.Thread(target=process_thread, args=('Bob',), name='Thread-B')

t1.start()
t2.start()

t1.join()
t2.join()
```

## 进程vs线程 ##

> 对应到Python语言，单线程的异步编程模型称为协程，有了协程的支持，就可以基于事件驱动编写高效的多任务程序。我们会在后面讨论如何编写协程。  

## 分布式进程 ##
> 在Thread和Process中，应当优选Process，因为Process更稳定，而且，Process可以分布到多台机器上，而Thread最多只能分布到同一台机器的多个CPU上。  
> Python的multiprocessing模块不但支持多进程，其中managers子模块还支持把多进程分布到多台机器上。一个服务进程可以作为调度者，将任务分布到其他多个进程中，
> 依靠网络通信。由于managers模块封装很好，不必了解网络通信的细节，就可以很容易地编写分布式多进程程序。

``` python
# task_master.py
import time, queue, random
from multiprocssing.managers import BaseManager

task_queue = queue.Queue()
result_queue = queue.Queue()

class QueueManager(BaseManager):
    pass

# 把两个Queue都注册到网络上，callback参数关联了Queue对象:
QueueManager.register('get_task_queue', callback=lambda: task_queue)
QueueManager.register('get_result_queue', callback=lambda: result_queue)

manager = QueueManager(address=('', 5000), authkey=b'abc')

# 启动Queue:
manager.start()

# 获得通过网络访问的Queue对象:
task = manager.get_task_queue()
result = manager.get_result_queue()

for i in range(10):
    n - random.randint(0, 10000)
    print('Put task %d...' % n)
    task.put(n)

# 从result队列读取结果:
print('Try get results...')
for i in range(10):
    r = result.get(timeout=10)
    print('Result: %s' % r)
# 关闭
manager.shutdown()
print('master exit.')
```

``` python
# task_work.py

import time, sys, queue
from multiprocessing.managers import BaseManager

class QueueManager(BaseManager):
    pass

QueueManager.register('get_task_queue')
QueueManager.register('get_result_queue')

server_addr = '127.0.0.1'
print('Connect to server %s...' % server_addr)

m = QueueManager(address=(server_addr, 5000), authkey=b'abc')
m.connect()

# 获取Queue对象
task = m.get_task_queue()
result = m.get_result_queue()

for i in range(10):
    try:
        n = task.get(timeout=1)
        print('run task %d * %d...' % (n, n))
        r = '%d * %d = %d' % (n, n, n * n)
        time.sleep(1)
        result.put(r)
    except Queue.Empty:
        print('task queue is empty.')
# 处理结束
print('worker exit.')
```
> 注意Queue的作用是用来传递任务和接收结果，每个任务的描述数据量要尽量小。比如发送一个处理日志文件的任务，
> 就不要发送几百兆的日志文件本身，而是发送日志文件存放的完整路径，由Worker进程再去共享的磁盘上读取文件。

# 正则表达式 #

``` python
s = 'ABC\\-001'
```
或者使用`r`前缀

``` python
s = r'ABC\-001'
```

``` python
import re

re.match(r'^\d{3}\-\d{3,8}$', '010-12345')

re.match(r'^\d{3}\-\d{3,8}$', '010 12345')
```
> match()方法判断是否匹配，如果匹配成功，返回一个Match对象，否则返回None。常见的判断方法就是：

``` python
test = 'test_string'
if re.match(r'regex', test)
    print('ok')
else:
    print('fail')
```

* 切分字符串

``` python
re.split(r'\s+', 'a b  c')
['a', 'b', 'c']

re.split(r'[\s\,]+', 'a,b, c  d')
['a', 'b', 'c', 'd']
```

* 分组

``` python
m = re.match(r'(\d{3})-(\d{3,8})$', '010-12345')
m
```

* 贪婪匹配

``` python
re.match(r'(\d+)(0*)$', '102300').groups()
('102300', '')
```

``` python
re.match(r'(\d+?)(0*)$', '102300').groups()
('1023', '00')
```

* 编译

# 常用内建模块 #

## datetime ##
* 格林尼治时间
> timestamp = 0 = 1970-1-1 00:00:00 UTC+0:00
* 北京时间
> timestamp = 0 = 1970-1-1 08:00:00 UTC+8:00
* 获取timestamp
``` python
from datetime import datetime
dt = datetime(2018, 10, 24, 10, 0)
dt.timestamp()
```
* timestamp转换为datetime
``` python
from datetime import datetime
t = 1429417200.0
print(datetime.fromtimestamp(t))
2015-04-19 12:20:00
```
* str转换为datetime
``` python
from datetime import datetime
cday = datetime.strptime('2018-10-24 10:24:00', '%Y-%m-%d %H:%M%S')
print(cday)
```
* datetime转换为str
``` python
from datetime import datetime
now = datetime.now()
print(now.strftime('%a, %b %d %H:%M'))
```
* datetime加减
``` python
from datetime import datetime, timedelta
now = datetime.now()
now + timedelta(hours=10)
now - timedelta(days=1)
now + timedelta(days=2, hours=12)
```
* 本地时间转换为UTC时间
> 本地时间是指系统设定市区对应的时间。datetime类型有一个时区属性，默认为None
``` python
from datetime import datetime, timedelta, timezone
tz_utc_8 = timezone(timedelta(hours=8))
now = datetime.now()
dt = now.replace(tzinfo=tz_utc_8)
dt
```
* 时区转换

``` python
utc_dt = datetime.utcnow().replace(tzinfo=timezone.utc)
print(utc_dt)

bj_dt = utc_dt.astimezone(timezone(timedelta(hours=8)))
print(bj_dt)

tokyo_dt = utc_dt.astimezone(timezone(timedelta(hours=9)))
print(tokyo_dt)

tokyo_dt2 = bj_dt.astimezone(timezone(timedelta(hours=9)))
```

## collections ##
* namedtuple

``` python
> namedtuple是一个函数，用来创建一个自定义的tuple对象，并且规定了tuple元素的个数，并且可以用属性来索引tuple的元素。  

from collections import namedtuple
Point = namedtuple('Point', ['x', 'y'])
p = Point(1, 2)
p.x
# 1
p.y
# 2
```

* dque
> deque是为了实现高效插入和删除操作的双向列表

``` python
from collections import deque
q = deque(['a', 'b', 'c'])
q.append('x')
q.appendleft('y')
q
# deque('y', 'a', 'b', 'c', 'x')
```

* defaultdict

``` python
from collections import defaultdict
dd = defaultdict(lambda: 'N/A')
dd['key1'] = 'abc'
dd['key1']
# 'abc'
dd['key2']
# 'N/A'
```

* OrderedDict
使用*dict*时，key是无序的。在对dict做迭代时，我们无法确定key的顺序。  
如果需要保持key的顺序，可以使用OrderedDict

``` python
from collections import OrderedDict
l = [('a', 1), ('b', 2), ('c', 3)]
d = dict(l)
print(d)

od = OrderedDict(l)
print(od)
```


* ChainMap
> ChainMap可以把一组*dict*串起来形成一个逻辑上的*dict*。ChainMap本身也是一个dict。查找的时候会按照顺序在内部的dict中依次查找。  

``` python
from collects import ChainMap
import os, argparse

defaults = {
    'color': 'red',
    'user': 'guest'
}

parser = argparse.ArgumentParser()
parser.add_argument('-u', '--user')
parser.add_argument('-c', '--color')
namespace = parser.parse_args()
command_line_args = { k: v for k, v in vars(namespace).items() if v }

# 组和成ChainMap
combined = ChainMap(command_line_args, os.environ, defaults)

# 打印参数
print('color=%s' % combined['color'])
print('user=%s' % combined['user'])

```

* Counter
``` python
from collections import Counter
c = Counter()
for ch in 'programming':
    c[ch] = c[ch] + 1
print(c)
# Counter({'g': 2, 'm': 2, 'r': 2, 'a': 1, 'i': 1, 'o': 1, 'n': 1, 'p': 1})
```

## base64 ##
Base64是一种用64个字符表示任意二进制数据的方法。 因为二进制包含很多无法显示和打印的字符，所以要让文本处理器处理和显示二进制数据，需要一个二进制到字符的  
转换方法。Base64是一种常见的二进制编码方法。  
![编码方式](images/base64.png "Base64 encoding")

如果要编码的二进制数据不是3的倍数，最后会剩下1个或2个字节怎么办？Base64用\x00字节在末尾补足后，再在编码的末尾加上1个或2个=号，  
表示补了多少字节，解码的时候，会自动去掉。  

由于标准的Base64编码后可能出现字符+和/，在URL中就不能直接作为参数，所以又有一种"url safe"的base64编码，其实就是把字符+和/分别变成-和_。   
去掉=后怎么解码呢？因为Base64是把3个字节变为4个字节，所以，Base64编码的长度永远是4的倍数，因此，需要加上=把Base64字符串的长度变为4的倍数，就可以正常解码了。  

``` python
import base64

def safe_base64_decode(s):
    l = len(s)
    compl = 4 - l % 4
    ba = bytearray(s)
    if compl < 4:
        for i in range(compl):
            ba.append()
```

## struct ##
Python没有专门处理字节的数据类型，但由于`b'str'`可以表示字节，所以，字节数组=二进制str。  

``` python
import struct
struct.pack('>I', 10240099)
# b'\x00\x9c@c'
```
* > 表示big-endien
* I 表示4字节无符号整数

``` python
struct.unpack('>IH', b'\xf0\xf0\xf0\xf0\x80\x80')
(4042322160, 32896)
```

``` python
def bmp_info(data):
    info_bytes = struct.unpack('<ccIIIIIIHH', data)
    width = info_bytes[6]
    height = info_bytes[7]
    color = info_bytes[9]
    return {
        'width': width,
        'height': height
        'color': color
    }

bi = bmp_info(bmp_data)
print(bi)
```

## hashlib ##

Python的hashlib提供了常见的摘要算法，如MD5，SHA1等等。  
什么是摘要算法呢？摘要算法又称哈希算法、散列算法。他通过一个函数，把任意长度的数据转化成固定长度的字符串。  

``` python
import hashlib

db = {
    'michael': 'e10adc3949ba59abbe56e057f20f883e',
    'bob': '878ef96e86145580c38c87f0410ad153',
    'alice': '99b1c2188db85afee403b1536010c2c9'
}

def login(user, password):
    md5 = hashlib.md5()
    md5.update(password.encode('utf-8'))
    if db[user] == md5.hexdigest():
        return True
    return False
```
由于常用口令的MD5值很容易被计算出来，所以，要确保存储的用户口令不是那些已经被计算出来的常用口令的MD5，这一方法通过对原始口令加一个复杂字符串来实现，俗称“加盐”：  

``` python
def calc_md5(password):
    return get_md5(password + 'the-Salt')
```

## hmac ##
是Hmac算法：Keyed-Hashing for Message Authentication。

``` python
import hmac

message = b'Hello, world!'
key = b'secret'
h = hmac.new(key, message, digest='MD5')
# 如果消息很长，可以多次调用h.update(msg)
h.hexdigest()
```

## itertools ##

count()会创建一个无限的迭代器，所以上述代码会打印出自然数序列，根本停不下来，只能按Ctrl+C退出。
``` python
import itertools
natuals = itertools.count(1)
for n in natuals:
    print(n)
```

cycle()会把传入的一个序列无限重复下去：

``` python
import itertools
cs = itertools.cycle('ABC')
for c in cs:
    print(c)
```

repeat()负责把一个元素无限重复下去，不过如果提供第二个参数就可以限定重复次数：

``` python
ns = itertools.repeat('A', 3)
for n in ns:
    print(n)
```

``` python
natuals = itertools.count(1)
ns = itertools.takewhile(lambda x: x <= 10, natuals)
list(ns)
```

* chain()
chain()可以把一组对象串联起来，形成一个更大的迭代器  

``` python
for c in itertools.chain('ABC', 'XYZ'):
    print(c)
```

* groupby()
groupby()把迭代器中相邻的重复元素跳出来放在一起  

``` python
for key, group in itertools.groupby('AAABBBCCAAA'):
    print(key, list(group))
...
A ['A', 'A', 'A']
B ['B', 'B', 'B']
C ['C', 'C']
A ['A', 'A', 'A']
```

* 计算圆周率

``` python
def pi(N):
    gen = itertools.count(1, 2)
    gen = itertools.takewhile(lambda x: x < 2 * N, gen)
    sum = 0
    for i in range(N):
        sum += ((-1)**i)*(4 / next(gen))
    return sum
```

## contextlib ##
任何对象，只要正确实现了上下文管理，就可以用*with*语句。实现上下文管理是通过*__enter__*, *__exit__*实现的。  

``` python
class Query(object):
    def __init__(self):
        self.name = name

    def __enter__(self):
        print('Begin')
        return self

    def __exit__(self, exc_type, exc_value, trackback):
        if exc_type:
            print('Error')
        else:
            print('End')

    def query(self):
        print('Query info about %s...' % self.name)
```

``` python
with Query('Bob') as q:
    q.query()
```

* @contextmanager
编写__enter__和__exit__仍然很繁琐，因此Python的标准库contextlib提供了更简单的写法，上面的代码可以改写如下：  

``` python
from contextlib import contextmanager

class Query(object):

    def __init__(self, name):
        self.name = name

    def query(self):
        print('Query info about %s...' % self.name)

@contextmanager
def create_query(name):
    print('Begin')
    q = Query(name)
    yield q
    print('End')
```
`@contextmanager`这个decorator接受一个generator，用yield语句把with ... as var把变量输出出去，然后，with语句就可以正常地工作了：  

``` python
with create_query('Bob') as q:
    q.query()
```

``` python
def tag(name):
    print('<%s>' % name)
    yield
    print('</%s>' % name)

with tag('h1'):
    print('hello')
    print('world')
...
<h1>
hello
world
</h1>
```

* @closing

``` python
from contextlib import closing
from urllib.request import urlopen

with closing(urlopen('https://www.python.org')) as page:
    for line in page:
        print(line)
```

> `closing`也是一个经过@contextmanager装饰的generator

``` python
@contextmanager
def closing(thing):
    try:
        yield thing
    finally:
        thing.close()
```

## urllib ##

### GET ###
urllib的request模块可以非常方便的抓取URL内容，也就是发送一个GET请求到指定页面，然后返回HTTP的respond

``` python
from urllib import request

with request.urlopen('https://api.douban.com/v2/book/2129650') as f:
    data = f.read()
    print('Status:', f.status, f.reason)
    for k, v in f.getheaders():
        print('%s: %s' % (k, v))
    print('Data:', data.decode('utf-8'))
```

### POST ###
如果要以POST发送一个请求，只需要把参数*data*以bytes形式传入  

``` python
from urllib import request, parse

email = input('Email:')
passwd = input('Password:')
login_data = parse.urlencode([
    ('username', email),
    ('password', passwd),
    ('entry', 'mweibo'),
    ('client_id', ''),
    ('savestate', '1'),
    ('ec', ''),
    ('pagerefer', 'https://passport.weibo.cn/signin/welcome?entry=mweibo&r=http%3A%2F%2Fm.weibo.cn%2F')
])

req = request.Request('https://passport.weibo.cn/sso/login')
req.add_header('Origin', 'https://passport.weibo.cn')
req.add_header('User-Agent', 'Mozilla/6.0 (iPhone; CPU iPhone OS 8_0 like Mac OS X) AppleWebKit/536.26 (KHTML, like Gecko) Version/8.0 Mobile/10A5376e Safari/8536.25')
req.add_header('Referer', 'https://passport.weibo.cn/signin/login?entry=mweibo&res=wel&wm=3349&r=http%3A%2F%2Fm.weibo.cn%2F')

with request.urlopen(req, data=login_data.encode('utf-8')) as f:
    print('Status:', f.status, f.reason)
    for k, v in f.getheaders():
        print('%s: %s' % (k, v))
    print('Data: ', f.read().decode('utf-8'))

```

### Handler ###

``` python
proxy_handler = urllib.request.ProxyHandler({'http': 'http://www.example.com:3128'})
proxy_auth_handler = urllib.request.ProxyBasicAuthHandler()
proxy_auth_handler.add_password('realm', 'host', 'username', 'password')
opener = urllib.request.build_opener(proxy_handler, proxy_auth_handler)
with opener.open('http://www.example.com/login.html') as f:
    pass
```

## XML ##
DOM vs SAX
* DOM会把整个XML读入内存，解析为树，因此占用内存大，解析慢，优点是可以任意遍历树的节点。
* SAX是流模式，边读边解析，占用内存小，解析快，缺点是我们需要自己处理事件。

``` python
from xml.parsers.expat import ParserCreate
class DefaultSaxHandler(object):
    def start_element(self, name, attrs):
        print('sax:start_element: %s, attrs: %s' % (name, str(attrs)))

    def end_element(self, name):
        print('sax:end_element: %s' % name)

    def char_data(self, text):
        print('sax:char_data: %s' % text)

xml = r'''<?xml version="1.0"?>
<ol>
    <li><a href="/python">Python</a></li>
    <li><a href="/ruby">Ruby</a></li>
</ol>
'''
handler = DefaultSaxHandler()
parser = ParserCreate()
parser.StartElementHandler = handler.start_element
parser.EndElementHandler = handler.end_element
parser.CharacterDataHandler = handler.char_data
parser.Parse(xml)
```

``` python
from xml.parsers.expat import ParserCreate
from urllib import request

def parseXml(xml_str):
    obj = {}
    def startEle(name, attrs):
        if name == 'yweather:location':
            obj['city'] = attrs['city']
        elif name == 'yweather:forecast':
            if 'forecast' not in obj:
                obj['forecast'] = []
            else:
                obj['forecast'].append({
                    'date': attrs['date'],
                    'high': attrs['high'],
                    'low': attrs['low']
                })

    parser = ParserCreate()
    parser.StartElementHandler = startEle
    parser.Parse(xml_str)
    return obj

URL = 'https://query.yahooapis.com/v1/public/yql?q=select%20*%20from%20weather.forecast%20where%20woeid%20%3D%202151330&format=xml'
with request.urlopen(URL, timeout=4) as f:
    data = f.read()

result = parseXml(data.decode('utf-8'))
assert result['city'] == 'Beijing'
```

## HTMLParser ##

``` python
from html.parser import HTMLParser
from html.entities import name2codepoint

class MyHTMLParser(HTMLParser):

    def handle_starttag(self, tag, attrs):
        print('<%s>' % tag)

    def handle_endtag(self, tag):
        print('</%s>' % tag)

    def handle_startendtag(self, tag, attrs):
        print('<%s/>' % tag)

    def handle_data(self, data):
        print(data)

    def handle_comment(self, data):
        print('<!--', data, '-->')

    def handle_entityref(self, name):
        print('&%s;' % name)

    def handle_charref(self, name):
        print('&#%s;' % name)

parser = MyHTMLParser()
parser.feed('''<html>
<head></head>
<body>
<!-- test html parser -->
    <p>Some <a href=\"#\">html</a> HTML&nbsp;tutorial...<br>END</p>
</body></html>''')
```

# 常用第三方模块 #
## Pillow ##
[https://pillow.readthedocs.org/](Pillow "Pillow")

PIL: Python Imaging Library  
一群志愿者在PIL的基础上创建了兼容的版本，名字叫Pillow，支持最新Python 3.x，又加入了许多新特性，因此，我们可以直接安装使用Pillow。  
`pip install pillow`

``` python
from PIL import Image

w, h = im.size
print('Original image size: %sx%s' % (w, h))

im.thumbnail((w//2, h//2))
im.save('thumbnail.jpg', 'jpeg')
```

## requests ##

``` python
import requests
r = request.get('https://www.douban.com/')
r.status_code
# 200
r.text
...
```

## chardet ##
当我们拿到一个bytes时，就可以对其检测编码。用chardet检测编码，只需要一行代码：  

``` python
chardet.detect(b'Hello, world!')
# {'encoding': 'ascii', 'confidence': 1.0, 'language': ''}

data = '离离原上草，一岁一枯荣'.encode('gbk')
chardet.detect(data)
# {'encoding': 'GB2312', 'confidence': 0.7407407407407407, 'language': 'Chinese'}

data = '离离原上草，一岁一枯荣'.encode('utf-8')
chardet.detect(data)
# {'encoding': 'utf-8', 'confidence': 0.99, 'language': ''}
```

## psutil ##
psutil = process and system utilities
`pip install psutil`

* 获取CPU信息

``` python
import psutil
psutil.cpu_count()
# 4
psutil.cpu_count(logical=False)
# 2
```

* 统计CPU的用户/系统/空闲实现

``` python
psutil.cpu_times()
# scputimes(user=10963.31, nice=0.0, system=5138.67, idle=356102.45)
```

* 获取内存信息

``` python
psutil.virtual_memory()
# svmem(total=8589934592, available=2866520064, percent=66.6, used=7201386496, free=216178688, active=3342192640, inactive=2650341376, wired=1208852480)

psutil.swap_memory()
# sswap(total=1073741824, used=150732800, free=923009024, percent=14.0, sin=10705981440, sout=40353792)
```

* 获取磁盘信息

``` python
psutil.disk_partitions()
# [sdiskpart(device='/dev/disk1', mountpoint='/', fstype='hfs', opts='rw,local,rootfs,dovolfs,journaled,multilabel')]

psutil.disk_usage('/') # 磁盘使用情况
# sdiskusage(total=998982549504, used=390880133120, free=607840272384, percent=39.1)

psutil.disk_io_counters() # 磁盘IO
# sdiskio(read_count=988513, write_count=274457, read_bytes=14856830464, write_bytes=17509420032, read_time=2228966, write_time=1618405)
```

* 获取网络信息

``` python
psutil.net_io_counters() # 获取网络读写字节／包的个数
# snetio(bytes_sent=3885744870, bytes_recv=10357676702, packets_sent=10613069, packets_recv=10423357, errin=0, errout=0, dropin=0, dropout=0)

psutil.net_if_addrs() # 获取网络接口信息
# {
#  'lo0': [snic(family=<AddressFamily.AF_INET: 2>, address='127.0.0.1', netmask='255.0.0.0'), ...],
#  'en1': [snic(family=<AddressFamily.AF_INET: 2>, address='10.0.1.80', netmask='255.255.255.0'), ...],
#  'en0': [...],
#  'en2': [...],
#  'bridge0': [...]
# }

psutil.net_if_stats() # 获取网络接口状态
# {
#   'lo0': snicstats(isup=True, duplex=<NicDuplex.NIC_DUPLEX_UNKNOWN: 0>, speed=0, mtu=16384),
#   'en0': snicstats(isup=True, duplex=<NicDuplex.NIC_DUPLEX_UNKNOWN: 0>, speed=0, mtu=1500),
#   'en1': snicstats(...),
#   'en2': snicstats(...),
#   'bridge0': snicstats(...)
# }

```

``` python
psutil.net_connections() # 需要sudo执行
```

* 获取进程信息

``` python
psutil.pids()
# [3865, 3864, 3863, 3856, 3855, 3853, 3776, ..., 45, 44, 1, 0]

p = psutil.Process(3776)
p.name()

p.exe()
# '/Users/michael/anaconda3/bin/python3.6'

p.cwd()
# '/Users/michael'

p.cmdline()
# ['python3']

p.ppid()
3365

p.parent()
# <psutil.Process(pid=3765, name='bash') at 4503144040>

p.children()
# []

p.status()
# 'running'

p.username()
# 'albert'

p.create_time()
# 1511052731.120666

p.terminal() # 进程终端
# '/dev/ttys002'

p.memory_info() # 进程使用的内存
# pmem(rss=8310784, vms=2481725440, pfaults=3207, pageins=18)

p.open_files()
# []

p.connections() # 进程相关网络连接
# []

p.num_threads() # 进程的线程数
# 1

p.threads() # 所有线程信息
# [pthread(id=1, user_time=0.090318, system_time=0.062736)]

p.environ() # 进程环境变量
# {'SHELL': '/bin/bash', 'PATH': '/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin:...', 'PWD': '/Users/michael', 'LANG': 'zh_CN.UTF-8', ...}

p.terminate() # 结束进程

```

# virtualenv #
> virtualenv 就是用来为一个应用创建一套‘隔离’的Python运行环境
`pip3 install virtualenv`
`virtualenv --no-site-packages venv`
`source venv/bin/active`

# 图形界面 #
Python支持多种图形界面第三方库，包括:
* TK
* wxWidgets
* Qt
* GTK

Python自带的是支持TK的Tkinter

``` python
from tkinter import *
import tkinter.messagebox as messagebox

class Application(Frame):
    def __init__(self, master=None):
        Frame.__init__(self, master)
        self.pack()
        self.createWidgets()

    def createWidgets(self):
        self.nameInput = Entry(self)
        self.nameInput.pack()
        self.quitButton = Button(self, text='Quit', command=self.hello)
        self.quitButton.pack()

    def hello(self):
        name = self.nameInput.get() or 'world'
        messagebox.showinfo('Message', 'Hello, %s' % name)

app = Application()
app.master.title('Hello World')
app.mainloop()
```
# 网络编程 #

## TCP/IP简介 ##
> IP协议负责把数据从一台计算机通过网络发送到另一台计算机。数据被分割成一小块一小块，然后通过IP包发送出去。由于互联网链路复杂，两台计算机之间经常有多条线路，
> 因此，路由器就负责决定如何把一个IP包转发出去。IP包的特点是按块发送，途径多个路由，但不保证能到达，也不保证顺序到达。

> TCP协议则是建立在IP协议之上的。TCP协议负责在两台计算机之间建立可靠连接，保证数据包按顺序到达。TCP协议会通过握手建立连接，然后，对每个IP包编号，
> 确保对方按顺序收到，如果包丢掉了，就自动重发。

## TCP编程 ##

* 客户端
``` python
import socket

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect(('www.sina.com.cn', 80))

# 发送数据
s.send(b'GET / HTTP/1.1\r\nHost: www.sina.com.cn\r\nConnection: close\r\n\r\n')

# 接收数据:
buffer = []
while True:
    # 每次最多接收1k字节:
    d = s.recv(1024)
    if d:
        buffer.append(d)
    else:
        break
data = b''.join(buffer)

# 关闭连接
s.close()

header, html = data.split(b'\r\n\r\n', 1)
print(header.decode('utf-8'))
# 把接收的数据写入文件:
with open('sina.html', 'wb') as f:
    f.write(html)
```

``` python
s = scoket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect(('127.0.0.1', 9999))
print(s.recv(1024).decode('utf-8'))
for data in [b'Michael', b'Tracy', b'Sarah']
    s.send(data)
    print(s.recv(1024).decode('utf-8'))
s.send(b'exit')
s.close()
```

* 服务端

``` python
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.bind(("127.0.0.1", 9999))
s.listen()
print('Waiting for connections...')

while True:
    sock, addr = s.accept()
    t = threading.Thread(target=tcplink, args=(sock, addr))

def tcplink(sock, addr):
    print('Accept new connection from %s:%s...' % addr)
    sock.send(b'Welcome')
    while True:
        data = sock.recv(1024)
        time.sleep(1)
        if not data or data.decode('utf-8') == 'exit':
            break
        sock.send(('Hello, %s!' % data.decode('utf-8')).encode('utf-8'))
    sock.close()
    print('Connection from %s:%s closed.' % addr)

```
## UDP编程 ##


``` python
# 服务端
s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
s.bind(('127.0.0.1', 9999))
print('Bind UDP on 9999...')

while True:
    data, addr = s.recvfrom(1024)
    print('Received from %s:%s' % addr)
    s.sendto(b'Hello, %s!' % data, addr)
```

``` python
# 客户端
s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
for data in [b'Michael', b'Tracy', b'Sarah']
    s.sendto(data, ('127.0.0.1', 9999))
    # 接收数据
    print(s.recv(1024).decode('utf-8'))
s.close()
```

# 电子邮件 #
> *smtplib*负责发送邮件，*poplib*负责接收邮件，*email*负责构建邮件

``` python
from email.mine.text import MIMEText
msg = MIMEText('hello, send by Python...', 'plain', 'utf-8')

from_addr = input('From: ')
password = input('Password: ')

to_addr = input('To: ')
smtp_server = input('SMTP server: ')

import smtplib
server = smtplib.SMTP(smtp_server, 25') # SMTP协议默认端口25
server.set_debuglevel(1)
server.login(from_addr, password)
server.sendmail(from_addr, [to_addr], msg.as_string())
server.quit()
```

* 带标题
``` python
from email import encoders
from email.header import Header
from email.mime.text import MIMEText
from email.utils import parseaddr, formataddr

import smtplib

def _format_addr(s):
    name, addr = parseaddr(s)
    return formataddr((Header(name, 'utf-8').encode(), addr))

from_addr = input('From: ')
password = input('Password: ')
to_addr = input('To: ')
smtp_server = input('SMTP server: ')

msg = MIMEText('hello, send by Python...', 'plain', 'utf-8')
msg['From'] = _format_addr('Python爱好者 <%s>' % from_addr)
msg['To'] = _format_addr('管理员 <%s>' % to_addr)
msg['Subject'] = Header('来自SMTP的问候……', 'utf-8').encode()

server = smtplib.SMTP(smtp_server, 25)
server.set_debuglevel(1)
server.login(from_addr, password)
server.sendmail(from_addr, [to_addr], msg.as_string())
server.quit()
```

* 发送附件

``` python
# 邮件对象:
msg = MIMEMultipart()
msg['From'] = _format_addr('Python爱好者 <%s>' % from_addr)
msg['To'] = _format_addr('管理员 <%s>' % to_addr)
msg['Subject'] = Header('来自SMTP的问候……', 'utf-8').encode()

# 邮件正文是MIMEText:
msg.attach(MIMEText('send with file...', 'plain', 'utf-8'))

# 添加附件就是加上一个MIMEBase，从本地读取一个图片:
with open('/Users/michael/Downloads/test.png', 'rb') as f:
    # 设置附件的MIME和文件名，这里是png类型:
    mime = MIMEBase('image', 'png', filename='test.png')
    # 加上必要的头信息:
    mime.add_header('Content-Disposition', 'attachment', filename='test.png')
    mime.add_header('Content-ID', '<0>')
    mime.add_header('X-Attachment-Id', '0')
    # 把附件的内容读进来:
    mime.set_payload(f.read())
    # 用Base64编码:
    encoders.encode_base64(mime)
    # 添加到MIMEMultipart:
    msg.attach(mime)
```

* 接收邮件

``` python
import poplib

# 输入邮件地址, 口令和POP3服务器地址:
email = input('Email: ')
password = input('Password: ')
pop3_server = input('POP3 server: ')

# 连接到POP3服务器:
server = poplib.POP3(pop3_server)
# 可以打开或关闭调试信息:
server.set_debuglevel(1)
# 可选:打印POP3服务器的欢迎文字:
print(server.getwelcome().decode('utf-8'))

# 身份认证:
server.user(email)
server.pass_(password)

# stat()返回邮件数量和占用空间:
print('Messages: %s. Size: %s' % server.stat())
# list()返回所有邮件的编号:
resp, mails, octets = server.list()
# 可以查看返回的列表类似[b'1 82923', b'2 2184', ...]
print(mails)

# 获取最新一封邮件, 注意索引号从1开始:
index = len(mails)
resp, lines, octets = server.retr(index)

# lines存储了邮件的原始文本的每一行,
# 可以获得整个邮件的原始文本:
msg_content = b'\r\n'.join(lines).decode('utf-8')
# 稍后解析出邮件:
msg = Parser().parsestr(msg_content)

# 可以根据邮件索引号直接从服务器删除邮件:
# server.dele(index)
# 关闭连接:
server.quit()
```

* 解析邮件

``` python
from email.parser import Parser
from email.header import decode_header
from email.utils import parseaddr

import poplib

msg = Parser().parsestr(msg_content)

# indent用于缩进显示:
def print_info(msg, indent=0):
    if indent == 0:
        for header in ['From', 'To', 'Subject']:
            value = msg.get(header, '')
            if value:
                if header=='Subject':
                    value = decode_str(value)
                else:
                    hdr, addr = parseaddr(value)
                    name = decode_str(hdr)
                    value = u'%s <%s>' % (name, addr)
            print('%s%s: %s' % ('  ' * indent, header, value))
    if (msg.is_multipart()):
        parts = msg.get_payload()
        for n, part in enumerate(parts):
            print('%spart %s' % ('  ' * indent, n))
            print('%s--------------------' % ('  ' * indent))
            print_info(part, indent + 1)
    else:
        content_type = msg.get_content_type()
        if content_type=='text/plain' or content_type=='text/html':
            content = msg.get_payload(decode=True)
            charset = guess_charset(msg)
            if charset:
                content = content.decode(charset)
            print('%sText: %s' % ('  ' * indent, content + '...'))
        else:
            print('%sAttachment: %s' % ('  ' * indent, content_type))
```

# 访问数据库 #

## SQLite ##

``` python
# 导入SQLite驱动:
>>> import sqlite3
# 连接到SQLite数据库
# 数据库文件是test.db
# 如果文件不存在，会自动在当前目录创建:
>>> conn = sqlite3.connect('test.db')
# 创建一个Cursor:
>>> cursor = conn.cursor()
# 执行一条SQL语句，创建user表:
>>> cursor.execute('create table user (id varchar(20) primary key, name varchar(20))')
<sqlite3.Cursor object at 0x10f8aa260>
# 继续执行一条SQL语句，插入一条记录:
>>> cursor.execute('insert into user (id, name) values (\'1\', \'Michael\')')
<sqlite3.Cursor object at 0x10f8aa260>
# 通过rowcount获得插入的行数:
>>> cursor.rowcount
1
# 关闭Cursor:
>>> cursor.close()
# 提交事务:
>>> conn.commit()
# 关闭Connection:
>>> conn.close()
```

``` python
>>> conn = sqlite3.connect('test.db')
>>> cursor = conn.cursor()
# 执行查询语句:
>>> cursor.execute('select * from user where id=?', ('1',))
<sqlite3.Cursor object at 0x10f8aa340>
# 获得查询结果集:
>>> values = cursor.fetchall()
>>> values
[('1', 'Michael')]
>>> cursor.close()
>>> conn.close()
```

## MySQL ##
> MySQL内部有多种数据库引擎，最常用的引擎是支持数据库事务的InnoDB
* 安装MySQL驱动
`pip install mysql-connector-python --allow-external mysql-connector-python`
or
`pip install mysql-connector`

``` python
# 导入MySQL驱动:
>>> import mysql.connector
# 注意把password设为你的root口令:
>>> conn = mysql.connector.connect(user='root', password='password', database='test')
>>> cursor = conn.cursor()
# 创建user表:
>>> cursor.execute('create table user (id varchar(20) primary key, name varchar(20))')
# 插入一行记录，注意MySQL的占位符是%s:
>>> cursor.execute('insert into user (id, name) values (%s, %s)', ['1', 'Michael'])
>>> cursor.rowcount
1
# 提交事务:
>>> conn.commit()
>>> cursor.close()
# 运行查询:
>>> cursor = conn.cursor()
>>> cursor.execute('select * from user where id = %s', ('1',))
>>> values = cursor.fetchall()
>>> values
[('1', 'Michael')]
# 关闭Cursor和Connection:
>>> cursor.close()
True
>>> conn.close()
```

## SQLAlchemy ##
使用ORM技术将*数据库表结构*映射到对象上
`pip install sqlalchemy`

``` python
# 导入:
from sqlalchemy import Column, String, create_engine
from sqlalchemy.orm import sessionmaker
from sqlalchemy.ext.declarative import declarative_base

# 创建对象的基类:
Base = declarative_base()

# 定义User对象:
class User(Base):
    # 表的名字:
    __tablename__ = 'user'

    # 表的结构:
    id = Column(String(20), primary_key=True)
    name = Column(String(20))

# 初始化数据库连接:
engine = create_engine('mysql+mysqlconnector://root:password@localhost:3306/test')
# 创建DBSession类型:
DBSession = sessionmaker(bind=engine)
```

# Web开发 #
> Web开发也经历了好几个阶段：
1. 静态Web页面：由文本编辑器直接编辑并生成静态的HTML页面，如果要修改Web页面的内容，就需要再次编辑HTML源文件，早期的互联网Web页面就是静态的；
2. CGI：由于静态Web页面无法与用户交互，比如用户填写了一个注册表单，静态Web页面就无法处理。要处理用户发送的动态数据，出现了Common Gateway Interface，简称CGI，用C/C++编写。
3. ASP/JSP/PHP：由于Web应用特点是修改频繁，用C/C++这样的低级语言非常不适合Web开发，而脚本语言由于开发效率高，与HTML结合紧密，因此，迅速取代了CGI模式。ASP是微软推出的用VBScript脚本编程的Web开发技术，而JSP用Java来编写脚本，PHP本身则是开源的脚本语言。
4. MVC：为了解决直接用脚本语言嵌入HTML导致的可维护性差的问题，Web应用也引入了Model-View-Controller的模式，来简化Web开发。ASP发展为ASP.Net，JSP和PHP也有一大堆MVC框架。

目前，Web开发技术仍在快速发展中，异步开发、新的MVVM前端技术层出不穷。

## HTTP协议 ##

``` GET请求
GET /path HTTP/1.1
Header1: Value1
Header2: Value2
Header3: Value3
```

``` POST请求
POST /path HTTP/1.1
Header1: Value1
Header2: Value2
Header3: Value3

body data goes here...
```

当遇到连续两个\r\n时，Header部分结束，后面的数据全部是Body。

``` Reponse
200 OK
Header1: Value1
Header2: Value2
Header3: Value3

body data goes here...
```

## HTML简介 ##
HTML | CSS | Javascript

## WSGI接口 ##

``` python
# hello.py
def application(environ, start_response):
    start_response('200 OK', [('Content-Type', 'text/html')])
    return [b'<h1>Hello, web!</h1>']
```

``` python
# server.py
from wsgiref.simple_server import make_server

from hello import application

httpd = make_server('', 8000, application)
print('Serving HTTP on port 8000...')
httpd.serve_forever()
```

## 使用WEB框架 ##
* Flask
`pip install flask`
> Flask通过python的装饰器在内部自动地把URL和函数关联起来

``` python
from flask import Flask
from flask import request

app = Flask(__name__)

@app.route('/', methods=['GET', 'POST'])
def home():
    return '<h1>Home</h1>'

@app.route('/signin', methods=['GET'])
def signin_form():
    return '''<form action="/signin" method="post">
              <p><input name="username"></p>
              <p><input name="password" type="password"></p>
              <p><button type="submit">Sign In</button></p>
              </form>'''

@app.route('/signin', methods=['POST'])
def signin():
    # 需要从request对象读取表单内容：
    if request.form['username']=='admin' and request.form['password']=='password':
        return '<h3>Hello, admin!</h3>'
    return '<h3>Bad username or password.</h3>'

if __name__ == '__main__':
    app.run()
```

* Django：全能型Web框架；
* web.py：一个小巧的Web框架；
* Bottle：和Flask类似的Web框架；
* Tornado：Facebook的开源异步Web框架。

## 使用模板 ##

``` python
from flask import Flask, request, render_template

app = Flask(__name__)

@app.route('/', methods=['GET', 'POST'])
def home():
    return render_template('home.html')

@app.route('/signin', methods=['GET'])
def signin_form():
    return render_template('form.html')

@app.route('/signin', methods=['POST'])
def signin():
    username = request.form['username']
    password = request.form['password']
    if username=='admin' and password=='password':
        return render_template('signin-ok.html', username=username)
    return render_template('form.html', message='Bad username or password', username=username)

if __name__ == '__main__':
    app.run()
```
Flask通过`render_template()函数来实现模板的渲染`
`pip install jinja2`

``` html
# home.html
<html>
<head>
  <title>Home</title>
</head>
<body>
  <h1 style="font-style:italic">Home</h1>
</body>
</html>
```

``` html
# form.html
<html>
<head>
  <title>Please Sign In</title>
</head>
<body>
  {% if message %}
  <p style="color:red">{{ message }}</p>
  {% endif %}
  <form action="/signin" method="post">
    <legend>Please sign in:</legend>
    <p><input name="username" placeholder="Username" value="{{ username }}"></p>
    <p><input name="password" placeholder="Password" type="password"></p>
    <p><button type="submit">Sign In</button></p>
  </form>
</body>
</html>
```

``` html
# signin-ok.html
<html>
<head>
  <title>Welcome, {{ username }}</title>
</head>
<body>
  <p>Welcome, {{ username }}!</p>
</body>
</html>
```
> 通过MVC，我们在Python代码中处理M：Model和C：Controller，而V：View是通过模板处理的，这样，我们就成功地把Python代码和HTML代码最大限度地分离了。
> 在Jinja2模板中，我们用{{ name }}表示一个需要替换的变量。很多时候，还需要循环、条件判断等指令语句，在Jinja2中，用{% ... %}表示指令。

``` html
{% for i in page_list %}
    <a href="/page/{{ i }}">{{ i }}</a>
{% endfor %}
```

# 异步IO #

* 协程，又名纤程（Coroutine）
协程的概念很早就提出来了，但直到最近几年才在某些语言（如Lua）中得到广泛应用。协程最大的优势是执行效率极高。协程在一个线程中执行。
Python对协程的支持是通过generator实现的。

``` python
def consumer():
     r = ''
    while True:
        n = yield r
        if not n:
            return
        print('[CONSUMER] Consuming %s...' % n)
        r = '200 OK'

def produce(c):
    c.send(None)
    n = 0
    while n < 5:
        n = n + 1
        print('[PRODUCER] Producing %s...' % n)
        r = c.send(n)
        print('[PRODUCER] Consumer return: %s' % r)
    c.close()

c = consumer()
produce(c)
```

> “子程序就是协程的一种特例。”
> by Donald Knuth

## asyncio ##

*asyncio*是Python3.4版本引入的标准库，直接内置了对异步IO的支持。*asyncio*的编程模型就是一个消息循环。  
我们从*asyncio*模块中直接获取一个EventLoop的引用，然后把需要执行的协程扔到EventLoop中执行，就实现了异步IO。  

``` python
import asyncio

@asyncio.coroutine
def hello():
    print('Hello world!')
    r = yield from ayncio.sleep(1)
    print('Hello again!')

loop = aysncio.get_event_leep()
loop.run_until_complete(hello())
loop.close()
```

> `@asyncio.coroutine`把一个generator标记为coroutine类型，然后，我们就把这个coroutine扔到EventLoop中执行。
> hello()会首先打印出Hello world!，然后，yield from语法可以让我们方便地调用另一个generator。
> 由于asyncio.sleep()也是一个coroutine，所以线程不会等待asyncio.sleep()，而是直接中断并执行下一个消息循环。当asyncio.sleep()返回时
> ，线程就可以从yield from拿到返回值（此处是None），然后接着执行下一行语句。
> 把asyncio.sleep(1)看成是一个耗时1秒的IO操作，在此期间，主线程并未等待，而是去执行EventLoop中其他可以执行的coroutine了，因此可以实现并发执行。

``` python
import asyncio

@asyncio.coroutine
def wget(host):
    print('wget %s...' % host)
    connect = asyncio.open_connection(host, 80)
    reader, writer = yield from connect
    header = 'GET / HTTP/1.0\r\nHost: %s\r\n\r\n' % host
    writer.write(header.encode('utf-8'))
    yield from writer.drain()
    while True:
        line = yield from reader.readline()
        if line == b'\r\n':
            break
        print('%s header > %s' % (host, line.decode('utf-8').rstrip()))
    # Ignore the body, close the socket
    writer.close()

loop = asyncio.get_event_loop()
tasks = [wget(host) for host in ['www.sina.com.cn', 'www.sohu.com', 'www.163.com']]
loop.run_until_complete(asyncio.wait(tasks))
loop.close()
```

## asyncio/await ##

用asyncio提供的@asyncio.coroutine可以把一个generator标记为coroutine类型，然后在coroutine内部用yield from调用另一个coroutine实现异步操作。
python在3.5版引入了新的语法async和await，可以让corountine语法更简洁易读
1. 把@asyncio.coroutine替换为async；
2. 把yield from替换为await。

``` python
@asyncio.coroutine
def hello():
    print("Hello world!")
    r = yield from asyncio.sleep(1)
    print("Hello again!")
```

``` python
async def hello():
    print("Hello world!")
    r = await asyncio.sleep(1)
    print("Hello again!")
```

## aiohttp ##
`pip install aiohttp`

``` python
import asyncio

from aiohttp import web

async def index(request):
    await asyncio.sleep(0.5)
    return web.Response(body=b'<h1>Index</h1>')

async def hello(request):
    await asyncio.sleep(0.5)
    text = '<h1>hello, %s!</h1>' % request.match_info['name']
    return web.Response(body=text.encode('utf-8'))

async def init(loop):
    app = web.Application(loop=loop)
    app.router.add_route('GET', '/', index)
    app.router.add_route('GET', '/hello/{name}', hello)
    srv = await loop.create_server(app.make_handler(), '127.0.0.1', 8000)
    print('Server started at http://127.0.0.1:8000...')
    return srv

loop = asyncio.get_event_loop()
loop.run_until_complete(init(loop))
loop.run_forever()
```

