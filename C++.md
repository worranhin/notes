# C++

C++ 是在 [[C 语言]]的基础添加了一大堆东西的语言，可以说是 C 语言的一个超集。与 C 语言相比，增加的较重要的一些特性有类、模板等，对应着面向对象编程和泛型编程的思想。

## 输出不同进制

```cpp
cout << hex;
cout << 10 << endl;  // 以十六进制输出
cout << oct;
cout << 10 << endl; // 以八进制输出
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