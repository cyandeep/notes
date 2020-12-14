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
1.type()
2.print() input()
3.ord('A') chr(65)
4.encode('charset') decode('charset',errors='ignore')
5.len()
6.format() eg. 'hello {0}'.format('cyan')
```

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

