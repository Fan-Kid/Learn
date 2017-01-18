### 注释
1\. \# 单行注释   

`#这是注释`   

2\. ''' ''' 多行注释
```
    '''
    多行注释
    多行注释
    多行注释
    '''
```
3\. `*`     -> 用来传递任意个无名字参数，这些参数会以一个tuple(**元组**)的形式访问   
    `**`    -> 用来处理传递任意个有名字的参数，这些参数用dict(**键/值**)访问     
****
</br>
## Python基础
### 3.使用list和tuple
索引从0开始
* list
    ` strlist = ["mma", "bbs", 32, 11]`   
    * 有序集合，可以随时添加和删除其中的元素
    * 获取最后一个元素：    
        `-1 `   
        `len(list) - 1` 
    * 追加元素到末尾：      
        ` list.append("")`   
    * 插入到指定位置：   
        ` list.insert(index, "")`
    * 删除末尾的元素：   
        ` list.pop()`   
    * 删除指定位置的元素：   
        ` list.pop(index)`
* tuple   
   元表,一旦初始化就不能修改  
   `inttuple = (1,)`   
    

## 高级特性   
### 3.列表生成式   

** [] **    --->list  
> eg:` L = [x * x for x in range(10)]`   

</br>
### 4.生成器   
** () **      --->generator 一边循环一边计算, 可迭代对象    
** 函数中带有 `yield` ，则他就是一个 `generator` **
> eg: ` L = (x * x for x in range(10)) ` 

`next(L)`                 --->下一个元素

```    
# 杨辉三角
def triangles():
    l = [1]
    while True:
        yiled l
        l.append(0)
        l = [l[i-1] + l[i] for i in range(len(i))]
        return

n = 0
for t in triangles():
    print(t)
    n = n + 1
    if n == 10:
        break
```
</br>
### 5.迭代器   
 `isinstance(obj, Iterable)` : 判断obj是不是一个Iterator
> 凡是可作用于 `for` 循环的对象都是 `Iterable` 类型;    
> 凡是可作用于 `next()` 函数的对象都是 `Iterator` 类型， 它们表示一个惰性计算的序列    
> 集合数据类型如 `list` 、 `dict` 、 `str` 等是 `Iterable` 但不是 `Iterator` ,不过可以通过
 `iter()` 函数获得一个 `Iterator` 对象   
</br>

## 七、函数式编程
> 越抽象的计算，离计算机硬件越远   

允许把函数本身作为参数传入另一个函数，还允许返回一个函数

### 1. 高阶函数
* 变量可以指向函数
* 函数名也是变量  
* 传入函数   

#### I. map/reduce
##### (1) map(f, Iterable)
将传入的函数依次作用到序列的每个元素,并把结果作为新的`Iterator`返回   
eg:
```
def f(x):
    return x*x

r = map(f, [1,2,3,4,5,6,7,8,9])
list(r)
```
##### (2) reduce(f, Iterable)
f必须接收两个参数，`reduce`把结果继续和序列的下一个元素做累积计算.   
` reduce(f, [x1, x2, x3, x4] = f(f(f(x1, x2), x3), x4))`   


#### II. filter(f, Iterable)
过滤序列: 把传入的函数依次作用于每个元素，然后根据返回值是`True` 还是`False`决定保留还是丢弃该元素。   
```
def _not_divisible(n):
    return lambda x: x%n > 0 #根据传入的n构造了一个过滤函数
```

#### III. sorted
`sorted([1,2,3,4,23,35], key=abs, reverse=True)`   
* 可以接收一个`key`函数来实现自定义排序   
* 可以传入第三个参数 `reverse` 进行反向排序   

### 2. 返回函数
* 函数作为返回值   
* 闭包（Closure）:相关参数和变量保存在返回的函数中   
* 返回函数不要引用任何循环变量，或者后续会发生变化的变量  

### 3. 匿名函数
`lambda x : x*x `

### 4. 装饰器(Decorator)
 函数名字：`__name__`   
`@`   
eg:   
```
import functools

def log(func):
    @functools.wraps(func)      # 把原始函数的__name__等属性复制到wrapper()函数中
    def wrapper(*args, **kw):
        print('call %s()' $ func.__name__)
        return func(*args, **kw)
    return wrapper
```
### 5. 偏函数(Partial function)

`functools.partial` : 把一个函数的某些参数固定住（也就是设置默认值）,返回一个新函数   


## 八、模块
包含"__init__.py"的文件夹就是一个包，   
"__init__.py"可以是一个空文件，也可以python代码   
自己创建模块时不能和Python自带的模块名称冲突   

### 1. 使用模块
* 任何模块的第一个字符串都被视为模块的文档注释
* `__author__ = 'name'` 把作者名写进去
* 当在命令行运行`hello` 模块文件时，Python解释器会把一个特殊变量`__name__`置为`__main__`   
* 作用域   
    * 类似 `_xxx` 和 `__xxx` 这样的函数或变量就是非公开的（private）,不应该直接引用(**“不应该”而不是“不能”**)   
    * 外部不需要引用的函数全部定义成`private`，只有外部需要引用的函数才可以定义为public   

```
def _private_1(name):
    return 'Hello, %s' % name

def _private_2(name):
    return 'hi, %s' % name

# 公开greeting函数
def greeting(name): 
    if len(name) > 3:
        return _private_1(name)
    else:
        return _private_2(name)

```

### 2. 安装第三方模块
* 包管理工具 `pip`, 若未安装则重新安装python，勾选pip和Add python.exe to path   
* `pip install Pillow # 安装处理图像的工具库`   

```
from PIL import Image
im = Image.open('test.jpg')
print(im.format, im.size, im.mode)

im.thumbnail((200,100))
im.save('thumb.jpg', 'JPEG')

```   
* 加载模块时，Python解释器会搜索当前目录、所有已安装的内置模块和第三方模块,
  搜索路径房在`sys`模块的`path`变量中
* 修改搜索路径：   
    * 直接修改 `sys.path`, 运行时修改，运行结束后实效   

        ```
        >>> import sys
        >>> sys.path.append('path')

        ```   
    * 设置环境变量`PYTHONPATH`,只需添加你自己的搜索路径，Python自身的搜索路径不受影响


