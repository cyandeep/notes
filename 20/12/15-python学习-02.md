### 1、高级特性

#### 1.1切片	--	类似于`java`中的`substring`

获取索引从m到n步长为k的元素。

```python
>>> l=list(range(100))                                                                       >>> l                                                                                         [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 57, 58, 59, 60, 61, 62, 63, 64, 65, 66, 67, 68, 69, 70, 71, 72, 73, 74, 75, 76, 77, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90, 91, 92, 93, 94, 95, 96, 97, 98, 99]                                                                                 
>>> l[:10]                                                                                   [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]                                                       
>>> l[10:20]                                                                                 [10, 11, 12, 13, 14, 15, 16, 17, 18, 19]                                                     >>> l[-10:]                                                                                   [90, 91, 92, 93, 94, 95, 96, 97, 98, 99]                                                     >>> l[-10::2]                                                                                 [90, 92, 94, 96, 98]                                                                         >>> l[-11::2]                                                                                 [89, 91, 93, 95, 97, 99]    
```

#### 1.2迭代	--	遍历可迭代的对象

```python
>>> from collections import Iterable
>>> isinstance('abc', Iterable) # str是否可迭代

>>> d={'a':1,'b':2}     # d d.values() d.items()
>>> for k,v in d.items():                                                                     ...  print(k,v)                                                                               ...                                                                                           a 1                                                                                           b 2  
```

#### 1.3列表生成式	--	生成列表

```python
list1 = [x*x if x % 2 == 0 else -x for x in range(1, 11) if x > 4]
print(list1)
```

#### 1.4生成器	--	一边循环一边计算的机制

```python
g = (x * x for x in range(3)) #定义生成器
def f():					#定义生成器
    # print('step1')
    yield 1
    # print('step2')
    yield 2
    
for v in g:					#遍历
    print(v)

for v in f():
    print(v)
```

#### 1.5迭代器	--	generator,包括生成器和带yield的generator function

```txt
可以被for循环遍历的数据类型 -- 即Iterable
1、集合类型，如list,tuple,dict,set,str等
2.generator,包括生成器和带yield的generator function，即Iterator

Iterable 和 Iterator 的区别
Iterable 可以被for循环遍历
Iterator 不仅可以被for循环遍历，还可以通过next获取值，
可以通过iter()将Iterable变为Iterator
```

### 2、高阶函数	--	把函数当作参数

```python
def add(x,y,f):
  return f(x)+f(y)

print(add(1,2,abs))
```

#### 2.1`map/reduce`

- `map()`,将函数`fn`作用于集合的每一个元素，并返回一个`Iterator`对象

  ```python
  >>> list(map(abs,[-3,5,-6]))
  [3, 5, 6]
  ```

- `reduce()`,通过接收两个参数的`fn`对集合做归纳操作

  ```python
  >>> from functools import reduce
  >>> reduce(lambda x,y:x+y,m)
  14
  ```

#### 2.2`filter`

- 函数作用于集合的每一个元素，并根据返回的`bool`,决定是否丢弃该元素。

```python
>>> list(filter(lambda x:x>5,[2,3,6,5,8]))
[6, 8]
```

#### 2.3`sorted`

- 排序

```python
# key函数作用于集合中的每一个元素，然后对作用后的元素按照倒序排序
>>> sorted(['cyan','Deep','Hello','world'],key=str.lower,reverse=True)
['world', 'Hello', 'Deep', 'cyan']
```

