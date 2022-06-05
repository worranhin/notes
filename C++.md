---
alias: ["cpp"]
---

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

可以用 `cin.fail()` 判断文件结尾：  

```cpp
cin.get(ch);
while(!cin.fail())
  cin.get(ch);

// 还可以这样
while(cin)  // input success
while(cin.get(ch))  // 输入同时判断，这样更精简

// 还有类似 c 的写法
int ch;  // 因为 EOF 一般是 1，所以需要 int 来接收
ch = cin.get();
while(ch != EOF)
	ch = cin.get();
```

### cin.get() 与 cin.get(ch) 比较


属性|cin.get(ch)|ch=cin.get()
--- |---|---
传递输入字符的方式|将函数返回赋给参数ch|函数的返回值赋给ch
用于字符输入时函数的返回值|istream对象（执行bool转换后为true)|int类型的字符编码
到达EOF时函数的返回值|istream对象（执行bool转换后为false)|EOF

### 丢弃无效输入

```cpp
while(!(cin >> ch)){
	cin.clear();  // 重置输入，否则程序将拒绝继续输入。
	while(cin.get() != '\n')  // 清除剩余无效输入
		continue;
}
```

## 输出不同进制

```cpp
cout << hex;
cout << 10 << endl;  // 以十六进制输出
cout << oct;
cout << 10 << endl; // 以八进制输出
```

## 文件 IO

文件 IO 操作包含在 `<fstream>` 中。

```cpp
#incldue <fstream>

//...

ifstream fin;  // 声明了一个文件输入类型对象。
fin.open("test.txt");  // 与文件绑定
double x;
fin >> x;  // 将文件中的数读入 x
char line[81];
fin.getline(line, 81);  // 读入一行
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

## 动态分配内存

```cpp
int * pt = new int;  //分配 int 内存
int * pa = new int[10];  //分配数组
delete pt;  //释放内存
delete [] pa;  //释放数组
```

## 动态数组 Vector

> 参考 [std::vector - cppreference.com](https://zh.cppreference.com/w/cpp/container/vector)

`vector` 类型包含在 `<vector>` 中。

```cpp
#include <vector>

//...
std::vector<int> v1 = {1, 2, 3};
v1.push_back(4);  //  将元素追加到数组末尾
```

## 逻辑表达式

符号|描述|别名
---|---|---
<code>&#124;&#124;</code> | 逻辑或 | `or`
`&&`|逻辑与|`and`
`!`|逻辑非|`or`


## 字符函数库 cctype

`<cctype>` 是一个方便的字符相关库，能简化判断字符是否字母、标点、数字等操作。

```cpp
isalpha(ch);  // 检验 ch 是否为字母
ispunct(ch);  // ch 是标点符号
isdigit(ch);  // 数字字符
isspace(ch);  // 空白，包括空格、换行符等
```


函 数 名 称|返 回 值
---|---
`isalnum()`|如果参数是字母数字，即字母或数字，该函数返回true
`isalpha()`|如果参数是字母，该函数返回true
`iscntrl()`|如果参数是控制字符，该函数返回true
`isdigit()`|如果参数是数字（0～9），该函数返回true
`isgraph()`|如果参数是除空格之外的打印字符，该函数返回true
`islower()`|如果参数是小写字母，该函数返回true
`isprint()`|如果参数是打印字符（包括空格），该函数返回true
`ispunct()`|如果参数是标点符号，该函数返回true
`isspace()`|如果参数是标准空白字符，如空格、进纸、换行符、回车、水平制表符或者垂直制表符，该函数返回true
`isupper()`|如果参数是大写字母，该函数返回true
`isxdigit()`|如果参数是十六进制数字，即0～9、a～f或A～F，该函数返回true
`tolower()`|如果参数是大写字符，则返回其小写，否则返回该参数
`toupper()`|如果参数是小写字符，则返回其大写，否则返回该参数
`isgraph()`|如果参数是除空格之外的打印字符，该函数返回true
`islower()`|如果参数是小写字母，该函数返回true
`isprint()`|如果参数是打印字符（包括空格），该函数返回true
`ispunct()`|如果参数是标点符号，该函数返回true
`isspace()`|如果参数是标准空白字符，如空格、进纸、换行符、回车、水平制表符或者垂直制表符，该函数返回true
`isupper()`|如果参数是大写字母，该函数返回true
`isxdigit()`|如果参数是十六进制数字，即0～9、a～f或A～F，该函数返回true
`tolower()`|如果参数是大写字符，则返回其小写，否则返回该参数
`toupper()`|如果参数是小写字符，则返回其大写，否则返回该参数

更多参考[标准库头文件 <cctype> - cppreference.com](https://zh.cppreference.com/w/cpp/header/cctype)

## 随机数生成函数

- `void srand(int)`
- `int rand()`

```c
#include <cstdlib>
#include <ctime>

srand((int)time(0));  // 通过系统时间来设置随机数的种子
int x = rand();       // 生成一个 int 随机数

```

## 软件延时

软件延时可以用 `clock()` 函数。该函数包含在 `<ctime>` 中。

```cpp
#include <ctime>

float secs = 1;  // 定时 1s
clock_t delay = secs * CLOCKS_PER_SEC;  // 转换为 clock ticks
clock_t start = clock();  // 存储开始时间
while(clock() - start < delay);  // 停留直到过去 delay 时间
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

## 技巧

### 条件语句

在写条件判断时，有可能会手抖写错，将 `x == 1` 写成 `x = 1`，这样就变成了赋值语句了。

所以可以尝试反过来写 `1 == x`，这样如果写成 `1 = x` 的话，编译器就会报错，也就更容易找出错误。