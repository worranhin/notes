# WebGL

WebGL 直接用的话好像还挺麻烦的，一般可以用一些封装好的框架会更简便。

一些用到 WebGL 的框架：
- [[Three.js]]
- [[Babylon]]


## 创建上下文

```html
<body onload="main()">
 <canvas id="glcanvas" width="640" height="480">
 你的浏览器似乎不支持或者禁用了HTML5 <code>&lt;canvas&gt;</code> 元素.
 </canvas>
</body>
```

```js
const canvas = document.querySelector("#glcanvas");
const gl = canvas.getContext('webgl');
```

## 着色器

[WebGL 3D Perspective (webglfundamentals.org)](https://webglfundamentals.org/webgl/lessons/webgl-3d-perspective.html)

## 2 幂纹理

在 WebGL 里使用宽和高的尺寸像素都是2的幂的纹理（图片）是最理想的情况。若使用非 2 幂纹理会有诸多限制。

> 参考这一页内容 [Using textures in WebGL - Web API 接口参考 | MDN (mozilla.org)](https://developer.mozilla.org/zh-CN/docs/Web/API/WebGL_API/Tutorial/Using_textures_in_WebGL)