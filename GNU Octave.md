---
Tags: 
aliases: [Octave]
---

GNU Octave 是 [[Matlab]] 的开源替代。语法与 Matlab 几乎一致。

## pkg

```octave
pkg load <pkgName>  #加载包
pkg describe <pkgName>  #显示包的描述
pkg describe <pkgName> -verbose  #显示包的详细描述，包括所有函数
```

## control

control 是[[自动控制原理|自动控制]]相关的包。

像这样加载包：

```octave
pkg load control  # 加载 control 包
```

一些实例：

```octave
# 生成伯德图
s = tf('s');
G = 20 / (s * (0.5 * s + 1));
bode(G);
```