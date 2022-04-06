ACLLib 是一个基于 [[C 语言]] 的一个教学用图形库。

库地址为：[wengkai/ACLLib: ACLLib is a bunch of C functions covers Win32API and provides simpler API to beginners for programming Windows GUI applications. It compiles with MinGW and MS Visual Studio Express (github.com)](https://github.com/wengkai/ACLLib)

--------------------------------------

## API

### Setup

用 `Setup()` 函数来代替 `main()`。

### initWindow

用于新建一个窗口。

```c
initWindow(char title[], int x, int y, int width, int height);
```

参数分别是标题、横纵坐标和宽度高度。

### initConsole

初始化一个控制台程序