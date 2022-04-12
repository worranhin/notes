## 单位

`em` ：相对于 `font-size` 的尺寸

## 颜色

颜色常用 名称、 HSL 和 RGB 表示

HSL 是用色相、饱和度和亮度，比较易于理解，建议优先采用。

HSLA/RGBA ：最后的 A 是 alpha 通道，表示透明度，取值从 0 到 1

`currentcolor` 值为当前颜色，可以统一用此值，然后再分别设置 `color` 。

## 字体

`font-family`

若要分别设置中文和英文字体，只需将英文字体写在前面即可，因为英文字体不认识中文，中文会自动寻找下一个可用字体。

## 选择器

### 一些常用选择器
- `空格` 包含
- `+` 相邻
- `@media` 根据
- `:hover` 鼠标悬浮
- `::first-line`元素第一行
- `>` 初代子元素
- `*` 通配选择器

### 伪类

`:not()` 排除掉一些元素，如 `:not(:first-child)` 表示排除第一个元素。

### 伪元素

- `::before`  
- `::after`  
- `::first-letter`  
- `::first-line`  

#### content

每个伪元素都必须有 `content`，若没有文本内容可以 `content: '';` 。此外还能引用元素的属性 `content: attr(DOM-property-name);` 。

## 列表
- `list-style-type`  设置列表前的标志


## 布局

### 多列布局
- `column-count` 设置列数
- `columnwidth`  设置列宽

### 盒模型

- 标准盒模型: width仅代表内容宽度
- box-sizing:border-box 替代盒模型
  > width将包含内边距、边框和内容
-   display: inline-block内联块

### 溢出控制 overflow
- `hidden`  隐藏
- `scroll`  滚动条
- `auto`  溢出才出现滚动条

### 弹性盒子 Flex

- `flex: <grow> <shrink> <basis>`  设置子元素填充比例 
  > `flex: auto` 有时会有神奇的效果
- `align-items` 控制 flex 项在交叉轴上的位置。
- `justify-content` 控制主轴位置
- `order` 越大越靠后，可以是负值

### 网格 Grid

用 `grid-column` 和 `grid-row` 来设置子元素占据的网格，可以重叠以实现某种效果。

#### 自动多列填充

``` css
.container {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  grid-auto-rows: minmax(100px, auto);
  grid-gap: 20px;
}
```

### 浮动 Float

可以用浮动来实现首字母下沉的效果。

用 `clear` 属性来清除浮动效果，可取值 `left`, `right`, `both` 

`display:flow-root;` 用于包含一个浮动元素。

### 定位 `position`

- static
- relative
- absolute
- fixed
- sticky

#### 相对布局 relative

![[Pasted image 20220411181026.png]]

#### 绝对定位 absolute
绝对定位是相对于 `html` 的定位，若要使绝对定位相对于父元素，可以把父元素的定位设为相对定位 `position: relative;`

![[Pasted image 20220411181035.png]]

#### z-index
`z-index` 属性用于设置重叠的显示顺序。如元素设置了 z-index 不为 `auto` , 则伪元素始终在该元素的上方。

#### fixed
固定定位 `fixed` 起初类似于相对布局，但它是相对于窗口的，达阈值后固定，可实现让某一页面始终停留在页面中。

可以实现导航栏始终出现在窗口内的效果。

![[Pasted image 20220411180645.png]]
![[Pasted image 20220411180708.png]]

#### sticky
`sticky` 可以让元素随页面滚动到某一位置后再固定在此处。

### 外边距折叠

两个相邻的外边距 `margin` 会取其最大值而不是之和。

`margin: 0 auto;` 使元素居中。

### 处理溢出 
`overflow: auto;` 产生滚动条

使用时要设定容器的高度

   
## 侧边栏滑动效果的奇妙实现

这种方法被称为 *checkbox hack* ，可以不用 javascript 就能实现

### html

```html
<label for="toggle">❔</label>
<input type="checkbox" id="toggle">
<aside>

  ...

</aside>
```

### css
```css
aside {
  background-color: #a60000;
  color: white;

  width: 340px;
  height: 98%;
  padding: 10px 1%;

  position: fixed;
  top: 0;
  right: -370px;

  transition: 0.6s all;
}
input[type=checkbox]:checked + aside {
  right: 0px;
}
```

出自 [MDN 教程](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/CSS_layout/Practical_positioning_examples)。

## 滚动贴合

`sroll-snap-type`

`scroll-snap-align`

********

text-indent 首行缩进