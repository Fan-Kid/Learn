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
**isinstance(obj)** : 判断obj是不是一个Iterator
> 凡是可作用于`for`循环的对象都是`Iterable`类型;  

> 凡是可作用于`next()`函数的对象都是`Iterator`类型， 它们表示一个惰性计算的序列  

> 集合数据类型如`list`、`dict`、`str`等是`Iterable`但不是`Iterator`,不过可以通过
`iter()`函数活得一个`Iterator`对象   
