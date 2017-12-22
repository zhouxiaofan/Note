### Python之禅
原则：应该有一个——且最好只有一个——明显的方式去完成工作

### 空白形式 
将Python代码复制到Python shell中，如果报错IndentationError：expected an indented block

### 除法问题 
Python默认整除，如果想使用浮点数除法需要
```python 
        from __future__ import division
```
这时候整除用//即可
$$
C = AB\\
C_{i,j}=\sum_{k}A_{i,k}B_{k,j}
$$
### 函数
#### 函数作为参数
```python
def double(x):
    return x  *  2

def apply_to_one(f):
    return f(1)

my_double = double
x = apply_to_one(my_double)
```
##### lambda表示
```python
y = apply_to_one(lambda x:x+4)
print  y
```
#### 可以通过参数名称指定参数
```python
def subtrac(a=0,b=0):    
      return a-b
print subtrac(10,5)
print subtrac(0,5)
print subtrac(b=5)
```
