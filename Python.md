`**` 进行幂运算

## 字符串

print 时 在引号前加 `r` 可防止 `\` 后的字符被转义  
``` python
print(r"\n is ofen used to change line.")
```

用三引号实现跨行连续输入，行末自动换行，（在行末加 `\` 即可不换行）

切片 `string[0:5]` ，默认以 `0` 开始，以末尾结束，`str[:3]` `str[2:]`

字符串不可修改，是 `immutable`

`len(<str>)` 返回字符串的长度

用 `eval` 将数字字符串转换为数字

> `eval` 能将参数最外侧的引号去掉并执行剩余的语句

## 列表 (mutable)

`append()` 在结尾添加新元素

多重赋值 `x,y = 1,2`

## 字典 dict

### `get`(_key_[, _default_])[¶](https://docs.python.org/zh-cn/3/library/stdtypes.html?highlight=get#dict.get "永久链接至目标")

如果 _key_ 存在于字典中则返回 _key_ 的值，否则返回 _default_。 如果 _default_ 未给出则默认为 `None`，因而此方法绝不会引发 [`KeyError`](https://docs.python.org/zh-cn/3/library/exceptions.html#KeyError "KeyError")。

## 数制的表示

`0b` 表示二进制
`0o` 表示八进制
`0x` 表示十六进制

`id()` 输出变量的地址

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

-------------------

- `range()` 只接受整型数

## 模块

heapq 堆队列算法，可用于排序
