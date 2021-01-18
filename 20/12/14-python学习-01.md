### 1、学习目标

简单的使用，可以编写python程序。

### 2、学习内容

```txt
1.环境搭建
2.输入输出，数据类型，变量，注释，运算符，条件，循环，，函数，类，模块
```

### 3、输入输出

`print()`

`input()`

### 4、数据类型

`int,float,str,bool,list,tuple,set,dict,bytes`

### 5、变量

​	动态语言：在定义变量类型时不需要指定变量类型。

​	`eg. a=22`

### 6、符号

```txt
1. /  //  
前一个会获得一个浮点数，后一个是地板除，会获得整数
2.and or not
eg. print(1>2 or 3>2)
3. r'' 表示不转义
print(r'\\\n')  ==> \\\n
4.'''...''' 表示多行字符串
print('''hello
world''')
5.b'cyan' 表示一个bytes
6.% 用于格式化字符串
eg. print('hello %s' % 'world')
```

### 7、执行流程

#### 7.1判断

```txt
if <执行条件>:
	<执行语句>
elif <执行条件>:
	<执行语句>
else:
	<执行语句>
```

**执行条件不需要加括号，执行体通过 `:`和空格控制，else if 简写为elif.**

#### 7.2循环

##### 7.2.1 for循环

`for x in col`

##### 7.2.2 while循环

`while n<10:`

##### 7.2.3 break 和 continue

- break 提前结束循环
- continue 结束当前循环

### 8、函数

#### 8.1内置函数

```txt
1.type() isinstance(x,(int,float))
2.print() input()
3.ord('A') chr(65)
4.encode('charset') decode('charset',errors='ignore')
5.len()
6.format() eg. 'hello {0}'.format('cyan')
7.enumerate(l) -- 将list转变为索引-元素对
```

#### 8.2函数别名

```python
a=abs
print(a(-33))
```

#### 8.3自定义函数

定义函数。 分别是 关键字def,函数名，左括号，参数，右括号，冒号

```python
>>> def myabs(x):
...     if x>=0:
...             return x
...     else:
...             return -x
... 
>>> myabs(4)
4
>>> myabs(-4)
4
```

#### 8.4返回多个值  --  返回一个tuple

```python
def return_two_value(x,y):
    return x,y

x,y=return_two_value(1,2)
r=return_two_value(1,2)
type(r)
```

#### 8.5、函数参数

- 位置参数

- 默认参数

  - def power(x,n=2)

  - 定义默认参数，默认参数必须指向不变对象，否则，每次调用该函数，如果改变了`L`的内容，则下次调用时，默认参数的内容就变了，不再是函数定义时的`[]`了。

    - ```python
      def add_end(L=[]):
          L.append('END')
          return L
      
      >>> a()
      ['END']
      >>> a()
      ['END', 'END']
      ```

- 可变参数

  - 定义 `def f(*args):`
  - 调用 `f(1,2,3)`  或者   `f(*l)`  --   将l中的所有元素当作可变参数传递

- 关键字参数  --  允许传入0个或者多个含有参数名的参数，在函数的内部转为一个dict

  - 定义 `def f(**args):`
  - 调用 `f(**d)`

- 命名关键字参数

  - 仅允许传入名字的关键字作为参数，用 * 进行分离
  - ‵def person(name, age, *, city='Beijing', job):`

- 参数组合

  - 必选参数，默认参数，可变参数，命名关键字参数，关键字参数

### 9、list 和 tuple   -  有序集合

```python
l=[]
l1=list()
l2=['cyan',22]

# 不可变的集合，指 tuple的指向不可变,
# (1,['cyan']),这里的cyan 可以变，但是变得不是tuple,而是list
t=()
t=(1,)
t=('cyan',22)

```

### 10、dict 和 set

```python
d={'id':1,'name':'cyan'}
d['id']
d['id']=2
d.get('id')
d.get('id',1) 如果不存在，就返回1
d.pop('id')

s={1,2,3}
s=set([1,2,3])
s.add(4)
s.remove(4)
```

