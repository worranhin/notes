## 数据类型

### 基本数据类型

- int
- long
- short
- unsigned
- char
- float
- double
- signed
- _Bool
- _Complex
- _Imaginary

### 字符串和字符

用双引号括起来的为字符串，用单引号括起来的是字符
如 `'a'` 是一个字符，`"a"` 是由 'a' 和 '\0' 组成

### 复数和虚数

在 C99 支持复数和虚数，包括：
- 复数
	- `float_Complex`
	- `double_Complex`
	- `long double_Complex`
- 虚数
	- `float_Imaginary`
	- `double_Imaginary`
	- `long double_Imaginary`

> 包含 <complex.h> 后可以用 `complex` 代替 `_Complex`，用 `imaginary` 代替 `_Imaginary`

### 数组

不能令一个数组等于另一个数组。

```C
int a[];
int b[];
b = a;	//这样不行
```

数组名就是一个地址。

```C
int a[];
a == &a[0];
```

### 指针

```C
const int *p = &i //不能通过 *p 来赋值，i 可以是常量也可以是变量
int * const p = &i    //p 不能被重新赋值
int const *p = &i	//等同于 const int *p = &i
const int a[] = {1,2,3,4,5} //表明数组 a 内的元素不可变（a 本身就是不可变的指针）
```

#### 函数指针

对于下面这样一个函数

```c
void f(void) {
	//......
}
```

可以定义它的函数指针

```c
void (*pf)(void) = f;  // 定义函数指针并赋值
```

可以定义函数指针数组

```c
void (*pa)(void) = {f, g, h};
```

通过函数指针可以实现回调函数

### 结构

```c
struct point {  //声明了叫 point 的结构
	int x;  // 结构内有 x 和 y 两个 int
	int y;
} p1, p2;  // 定义了两个 point 类型的变量

// 也可以这样定义结构
struct point p3;
struct point p4 = {1, 1};  //同时赋值
struct point p5 = {.y=1, .x=2};  // 给某些成员赋值
int x = p4.x;  // 这样访问成员变量
p1 = (struct point){2, 2};  // 强制转换后赋值
p2 = p1;  // 可以整体赋值
struct point *pp1;  // 定义结构指针
*pp1 = &p1;

(*pp1).x = 1;  // 可以这样访问指针内容
pp1->x = 1;  // 也可以这样
```

## 变量修饰符

- `const` 常量
- `static` 静态变量，定义在函数内部，下次调用函数可以保留上一次的值

## 输入与输出

### scanf
```c
char s1[10000];
scanf("%s", s1);
```

### 更改 printf 输出颜色

```c
printf(ANSI_COLOR_RED  "this is red" ANSI_COLOR_RESET "\r\n");
```

> RED 可以换成 GREEN、YELLOW、BLUE、MAGENTA、CYAN

```C
main() {
  printf("%s", __func__);  // 输出当前函数的名称
}
```

### printf 的格式化

`%[flags][width][.prec][hlL]type`

#### flags
- `-`  表示左对齐
- `+`  表示要显示符号

#### width

- `<number>`  位数
- `*`  表示位数以参数形式输入
- `.<number>`  小数点位数
- `.*`  小数点位数以参数形式输入

```c
printf("%9.2d", 123);  // [3个空字符][][]123.00
printf("%*d", 4, 123);  // []123
```

![[Pasted image 20220323164211.png]]

#### 输出不同进制

```c
printf("dec = %d; octal = %o; hex = %#x\n", x, x, x);
// 输出十进制、八进制和十六进制，其中 %#x 表示输出 "0x" 前缀。
```

#### 浮点数

`%e` 表示打印用指数计数法的浮点数

#### 输出类型大小

`%zd` 表示 `size_t` 类型

```c
printf("size of int is %zd\n", sizeof(int));
```
 

### 转义字符

![[NeatReader-1649347150935.png]]

## clock()

`clock()` 函数返回程序开始运行至今的时间，单位是 `clock tick`，常与常数 `CLK_TCK` 一秒的 clock tick 数一起用。返回值的类型是 `clock_t`

包含在 `<time.h>` 中

## string 函数

- `strlen()` 返回长度
- `strcmp(s1, s2)` 比较两个字符串，0：相等；1：s1 > s2；2：s1 < s2
- `strcpy(dst, src)` 将 src 复制到 dst 中
 一个动态复制的例子：
```c
char *dst =  (char*)malloc(strlen(src)+1);
strcpy(dst, src);
```
- `strncmp(s1, s2, n)` 比较两个字符串的前 n 个，0：相等；1：s1 > s2；2：s1 < s2
- `strncpy(s1, s2, n)` 将 s2 拷贝到 s1
- `strncat(s1, s2, n)` s2 接到 s1 后
- `strchr(s, c)` 在 s 中 找 c，返回 NULL 表示没找到，找到的话返回指针
-  `strrchr(s, c)` 从右边开始找
- `strstr(s1, s2)` 在 s1 中找 s2
- `strcasestr(s1, s2)` 忽略大小写，其余同上

### 用 `strchr(s, c)` 寻找第二个字符的例子

```c
char s[] = "hello";
char *p = strchr(s, 'l');    //返回第一个 'l' 的指针
p = strchr(p+1, 'l');        //返回第二个 'l' 的指针
```

### 复制某字符前的一段字符串

```c
char s[] = "hello";
char *p = strchr(s, 'l');    //找到 'l' 的地址
char c = *p;                 //暂存 *p 的内容
*p = '\0';                   //令 'l' 变成 '\0'
char *t = (char*)malloc(strlen(s)+1);
strcpy(t, s);                //将 "he" 复制给 t
free(t);                     //释放动态内存 t
```


## 分支

### switch-case

case 只能是 int 、常量


通过 `getchar()` 来让程序暂停。


## 动态内存分配 malloc

```C
#include <stdlib.h>

int main(void)
{
	int number;
	int* a;

	/*输入 number*/

	//动态索取内存
	a = (int*)malloc(number*sizeof(int));

	/*操作*/
	a[0] = 1;

	//还内存
	free(a);
}
```

> 注意不要忘了 include <stdlib.h> 库

## 头文件

### stdint.h / inttypes.h

- 精确宽度整数类型(exact-width integer type)
    `int32_t` 表示 32 位的整数类型
- 最小宽度类型(minimum width type)
    `int_least8_t` 表示可容纳 8 位的最小的整数类型
- 最快最小宽度类型(fastest minimum width type)
  `int_fast8_t` 对 8 位有符号值运算最快的整数类型
- 最大有符号整数类型
  `intmax_t`
- 最大无符号整数类型
  `uintmax_t`

除了定义类型，该头文件还定义了用于控制输出格式的宏 `PRId32`。

下面是一个例子

```c
#include <stdio.h>
#include <inttypes.h>

int main(void)
{
	int32_t x32;  // 定义 x
	printf("x=" PRId32 "\n", x32);  // 正确输出 x
```

### string.h

#### memchr

```c
void *memchr(const void *str, int c, size_t n)
```

在 `str` 的前 `n` 个字符中查找 `c` 。

返回一个指向目标的指针。

#### strtok

[strtok, strtok_s - cppreference.com](https://zh.cppreference.com/w/c/string/byte/strtok)

一个诡异的函数。