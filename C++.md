# C++

C++ 是在 [[C 语言]]的基础添加了一大堆东西的语言，可以说是 C 语言的一个超集。与 C 语言相比，增加的较重要的一些特性有类、模板等，对应着面向对象编程和泛型编程的思想。

## 输入

`cin.getline(str, 10)`: 输入一行至多 10 个字符（包括 `\0`）于 `str` 中
`cin.get(str, 10)`: 输入一行，将 `\n` 留在输入流中
`cin.get(ch)`: 读取输入一个字符
`cin.get()`: 读取一个字符但不保存

```cpp
string str;
cin.getline(str, 20);
```

## String

`string` 是字符串变量类型

```cpp
string str1 = "hello";
string str2 = "world";
string str3 = str1 + str2;  //字符串连接赋值
str1 += str2;  //将字符串str2加在str1后面
str1 = str2;  //可以赋值
```

## 结构

```cpp
struct point {
double x;
double y;
};

//...

point p1 = {1, 2};
```

## enum

```cpp
enum color {red, blue, yellow};

color wallColor;
wallColor = red;
```

> 请不要将 enum 自增或当作 int 来用。

## 输出不同进制

```cpp
cout << hex;
cout << 10 << endl;  // 以十六进制输出
cout << oct;
cout << 10 << endl; // 以八进制输出
```

## 动态分配内存

```cpp
int * pt = new int;  //分配 int 内存
int * pa = new int[10];  //分配数组
delete pt;  //释放内存
delete [] pa;  //释放数组
```

## 随机数生成函数

- `void srand(int)`
- `int rand()`

```c
#include <cstdlib>
#include <ctime>

srand((int)time(0));  // 通过系统时间来设置随机数的种子
int x = rand();       // 生成一个 int 随机数

```

## 模板语法

```cpp
template<typename T1, typename T2>

void foo(T1 a, T2 b) {
	...
}
```

模板可以让函数应用于多种类型的参数。

## 智能指针

> [智能指针（现代 C++） | Microsoft Docs](https://docs.microsoft.com/zh-cn/cpp/cpp/smart-pointers-modern-cpp?view=msvc-170)

```cpp
std::unique_ptr<Song> song1(new Song(L"Nothing on You", L"Bruno Mars"));
```