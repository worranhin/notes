
---
aliases: C51
---

单片机的 [[C 语言]] 又叫 C51 是标准 C 的扩展，它为单片机的程序设计而生。

## C51 的存储类型

- data  可直接寻址
- bdata  可位寻址
- idata  间接寻址区
- xdata  外部存储区
- pdata  外存，比 xdata 快
- code  程序存储区，只读

## 数据类型

- bit
- unsigned char
- signed char
- unsigned long
- signed long
- float
- double
- 指针

## 数组

数组常用于查表操作，必要时还能加上插值算法。

## 指针

### 基于存储器的指针

以下两种声明方式等价

```c
char xdata *data pdx;
data char xdata *px;
```

表示定义指向在 xdata 中的 char 类型的指针, 指针位于 data

### 一般指针

一般指针占 3 字节, 分别为存储器类型, 偏移量高位, 偏移量地位, 如: `0x0100000L` 表示指向 xdata 零地址的指针。

#### 存储器类型编码
编码|类型
-----|-----
0x00 | idata/data/bdata
0x01 | xdata
0xFE | pdata
0xFF | code

## 中断函数的定义

函数类型  函数名  interrupt <中断号(0~31)>  [using  <寄存器组号 0~3>]

如果中断中使用浮点运算，需要保存浮点寄存器的状态，`math.h` 的库中有函数 `pfsave` 和 `fprestore` 用以保存和恢复寄存器状态。

中断中调用函数需要保证被调用的函数使用的寄存器组与中断使用的寄存器组一致。

## 库

库|文件
-----|-----
I/O 库|stdio.h
内部函数库|intrins.h
绝对地址访问|absacc.h

### 内部函数

函数|功能
-----|-----
\_crol\_ | 将 char 循环左移
\_nope\_| 延时

## 宏定义

宏定义一般用大写字母表示。

### 条件宏定义

```c51
#if 表达式
//code
#else
//code
#endif

#ifdef 标识符
//code
#else
//code
#endif

#ifndef 标识符
//code
#else
//code
#endif
```

## 嵌入汇编语句

```c51
#pragma asm
// 汇编语句
#pragma endasm
```

## 编程规范

变量名常加上表示数据类型的前缀。