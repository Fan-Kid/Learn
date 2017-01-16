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
****
</br>

## 高级特性   
### 3.列表生成器   

** [] **    --->list  
> eg:` L = [x * x for x in range(10)]`   

</br>
### 4.生成器   
** () **      --->generator 一边循环一边计算, 可迭代对象  
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
> 凡是可作用于`for`循环的对象都是`Iterable`类型;    
> 凡是可作用于`next()`函数的对象都是`Iterator`类型， 它们表示一个惰性计算的序列    
> 集合数据类型如`list`、`dict`、`str`等是`Iterable`但不是`Iterator`,不过可以通过
`iter()`函数获得一个`Iterator`对象   
</br>

## 函数式编程
> 越抽象的计算，离计算机硬件越远   

允许把函数本身作为参数传入另一个函数，还允许返回一个函数

### 1. 高阶函数
* 变量可以指向函数
* 函数名也是变量  
* 传入函数   

### 2. map/reduce
#### (1) map(f, Iterable)
将传入的函数依次作用到序列的每个元素,并把结果作为新的`Iterator`返回   
eg:
```
def f(x):
    return x*x

r = map(f, [1,2,3,4,5,6,7,8,9])
list(r)
```
#### (2) reduce(f, Iterable)
f必须接收两个参数，`reduce`把结果继续和序列的下一个元素做累积计算.   
` reduce(f, [x1, x2, x3, x4] = f(f(f(x1, x2), x3), x4))`   


### 3. filter(f, Iterable)
过滤序列: 把传入的函数依次作用于每个元素，然后根据返回值是`True` 还是`False`决定保留还是丢弃该元素。

