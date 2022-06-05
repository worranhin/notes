# Python

Python 是一门解释型的高级开源编程语言。

## 字符串

字符串是不可修改 （*immutable*）类型。

print 时在引号前加 `r` 可防止 `\` 后的字符被转义 

``` python
print(r"\n is ofen used to change line.")
```

用三引号实现跨行连续输入，行末自动换行，（在行末加 `\` 即可不换行）

### 切片
默认以 0 开始，以末尾结束
- `string[0:5]`: 从 0 到 5
- `str[:3]`: 从开头到 3
- `str[2:]`: 从 2 到结尾

### 相关函数

- `len(<str>)` 返回字符串的长度
- 用 `eval(str)` 将数字字符串转换为数字
    > `eval` 能将参数最外侧的引号去掉并执行剩余的语句
- `str(value)` 能将数字等非字符串转换为字符串。

### 字符串方法

`.title()`: 首字母大写  
`.upper()`: 全大写  
`.lower()`: 全小写  

`.rstrip()`: 删除末尾的空白  
`.lstrip()`: 删除开头的空白  
`.strip()`: 删除两端的空白  

## 列表

列表是 *mutable* 类型的数据结构。

### 列表解析

```python
squares = [value**2 for value in range(1, 11)]  #将返回 1~10的平方数
```

### 相关函数

`del(list[i])`: 删除列表第 i 个元素  
`len(list)`: 返回列表的长度  
`max(nlist)`: 返回最大值  
`min(nlist)`: 返回最小值  
`sorted(list)`: 返回被排序的列表（不改变列表） 
`sum(nlist)`: 返回数值列表之和

### 方法

`.append()`: 在结尾添加新元素  
`.insert(i, el)`: 在索引 i 处插入 el  
`.pop()`: 弹出末尾的元素  
`.pop(i)`: 弹出第 i 个元素  
`.remove(el)`: 删除值为 el 的元素  
`.reverse()`: 翻转列表
`.sort()`: 排序  
`.sort(reverse=True)`: 反向排序  
 


## 字典 dict

`get(_key_[, _default_])`: 如果 _key_ 存在于字典中则返回 _key_ 的值，否则返回 _default_。 如果 _default_ 未给出则默认为 `None`，因而此方法绝不会引发 [`KeyError`](https://docs.python.org/zh-cn/3/library/exceptions.html#KeyError "KeyError")。

## 数制的表示

`0b` 表示二进制
`0o` 表示八进制
`0x` 表示十六进制

## 复数

```python
z = 1 + 2j
z.real #返回实数
z.imag #返回虚数部分
z.conjugate() #返回共轭复数
```

## random 库

`choice(list)` 从 list 中随机挑个数
`shuffle(list)` 将 list 随机排列

## 模块

heapq 堆队列算法，可用于排序

## 问号表达式

Python 中没有像 [[C 语言]] 那样的问号表达式，但可以用简化的 `if-else` 语句实现类似的功能：

```python
a, b = 1, 2
max = a if a > b else b
```

## 杂项

`range()` 只接受整型数

```python
numbers = list(range(1, 6))  #生成 1~5 的数字列表
even_numbers = list(range(1, 11, 2))  #可以指定步长
```

`id()` 输出变量的地址

多重赋值 `x,y = 1,2`

`**` 进行幂运算
