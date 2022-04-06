[MDN官方教程链接](https://developer.mozilla.org/zh-CN/docs/Web/API/Canvas_API/Tutorial)

## 矩形
- `ctx.fillRect(x,y,w,h)` 绘制填充矩形
- `ctx.strokeRect()` 绘制矩形边框
- `ctx.clearRect()` 擦除矩形区域

> `const ctx = canvas.getContext()`

## 路径
- `moveTo(x,y)` 移动，不落笔
- `lineTo(x,y)`
- `arc(x, y, radius, startAngle, endAngle, anticlockwise)` 圆弧，`anticlockwise` 默认为`false` (顺时针)。
- `quadraticCurveTo(cp1x, cp1y, x, y)` 二次贝塞尔曲线
- `bezierCurveTo(cp1x, cp1y, cp2x, cp2y, x, y)` 三次贝塞尔曲线
- `fill()` 填充颜色
- `stroke()` 描绘路径

