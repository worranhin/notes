---
title: Matlab
updated: 2021-10-30 02:46:42Z
created: 2021-10-29 16:31:17Z
---

# Matlab

`sys=tf（num，den）` 建立传递函数模型

`sys=zpk（z，p，k）` 建立零极点的传递函数模型

`[z p k]= tf2zp(num, den)` 将传递函数模型转换为零极点增益模型

`zp2tf()` 将零极点增益模型转换为传递函数模型

`sys=series（sys1，sys2）` `sys=sys1 x sys2` 串联系统

`sys= parallel （sys1，sys2）` `sys=sys1+sys2` 并联系统

`sys= feedback （sys1，sys2，sign）` 反馈系统

`step()` 阶跃响应

bode 波特图
margin 裕度



