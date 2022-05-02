学习 Vue 前要掌握的 [[JavaScript]] 知识：
- ES6 语法
- ES6 模块化
- 包管理器 (npm 等)
- 原型
- 数组方法
- [[axios]]
- promise

-----------------------------------

## 安装

通过 CDN 

```javascript
<script src="https://unpkg.com/vue@next"></script>
```

## 创建实例

```html
<div id="root">
  <h1>hello {{name}}</h1>  
  <!--"{{}}"里面可以是js的表达式，Vue实例中Data的内容可以直接调用。-->
</div>
```

```javascript
const Root = {
	data() { //存数据
		return {
			name: '老张',
		}
	}
}

Vue.createApp(Root).mount('#root')  
 ```

### 这是 Vue2 的写法 

```javascript
new Vue({  //别漏了 new
	el: '#root',  //查找应用Vue实例的元素(容器)
	data: {  //
		name: 'world',
	},
})
```

> Vue3 似乎不支持这种写法了


## 组件实例 Property

- data
- methods
- props
- computed
- inject
- setup

### 内置 property

- $attrs
- $emit

## 生命周期钩子

可以在不同阶段执行相应操作

钩子有
- created 实例创建后
- mounted
- updated
- unmounted

> 不要在 property 和回调上使用箭头函数。

## 实例的生命周期

![[Pasted image 20220117133547.png]]

## 插值语法

用 `{{}}` 包裹 Vue 实例中 Data 返回的数据键，即可单向传递数据。

### v-once

用 `v-once` 使插值在生成后不再改变

```html
<span v-once>这将不改变: {{ msg }}</span>
```

### v-html

用 `v-html="msg"` 解析 html 语法

> 动态渲染 html 是危险行为，不要将用户提供的内容作为插值。

插值中的内容可以是表达式，但不能是语句，所以可以用三元表达式实现条件判断等。

## v-bind 

绑定元素 attribute

```html
<a v-bind:href="url">链接</a>
<!--这里的url是在Vue实例中定义的data-->
<!--当然也可以是任何表达式-->

<!--下面是简写形式-->
<a :href="url">链接</a>
```

## 指令

以 `v-` 开头的 `attribute` 都称为指令（Directives)

### 参数

指令的 ':' 后面是指令的参数，如 `v-on:click` 中的 `click` 就是指令 `v-on` 的参数。

指令的参数也可以是动态的，用方括号 `[]`括起来，像这样 `v-bind:[attributeName]="url"` ，这表示 `attributeName` 的内容的值等于 `url` 的内容。

> 注意：attributeName 会自动转换为小写 attributename

### 修饰符

在参数后用 `.` 指明后缀。

## data  and methods

```js
const app = Vue.createApp({
  data() {
    return {
      x: 1,
	}
  }，
  methods: {
    clickHandler() {
      //do something
	}
  }
})

const vm = app.mount('#app')
console.log(vm.$data.x)  // 可以用这种方式访问 data property
console.log(vm.x)  //这样也可以访问 data 里的顶级属性
```

> methods 中不要用箭头函数，里面定义的方法会将 `this` 绑定为应用实例

## 防抖

Vue 没有内置防抖，可以通过 [Lodash](https://lodash.com/) 等库实现。

```javascript
app.component('save-button', {
  created() {
    // 使用 Lodash 实现防抖
    this.debouncedClick = _.debounce(this.click, 500)
  },
  unmounted() {
    // 移除组件时，取消定时器
    this.debouncedClick.cancel()
  },
  methods: {
    click() {
      // ... 响应点击 ...
    }
  },
  template: `
    <button @click="debouncedClick">
      Save
    </button>
  `
})
```

## 计算属性

计算属性通过 `computed` 定义。

```js
const app = Vue.createApp({
	 data() {
		 return {
			 count: 4,
		 }
	 },
	 computed: {
		 countPlus: {
			 get() {	
				 return this.count + 1;	
			 },	
			 set(newValue) {	
				 this.count = newValue;	
			 }	
		 }	
	 }
 });
```

setter 通过这种方式调用

```js
vm = app.mount('#app')
vm.countPlus = 1
```

计算属性默认下只有 getter，所以不需要 setter 时可以这样：

```js
const app = Vue.createApp({
	 data() {
		 return {
			 count: 4,
		 }
	 },
	 computed: {
		 countPlus() {	
			 return this.count + 1;	
		 }	
	 }
 });
```

## 侦听器

侦听器用 `watch` 定义。方法名与 data 中的 property 名一致。

```js
const app = Vue.createApp({
	 data() {
		 return {
			 count: 4,
		 }
	 },
	 watch: {
		 count() {
			 console.log('Count has changed.')
		 }
	 }
})
```

## v-model

实现双向绑定，只能用在表单类（输入）元素中。

```html
<input type="text" v-model:value="input_value"/>
```

`v-model:value=""` 可简写为 `v-model=""`

### v-model 的修饰词

- `.lazy` : 数据将在 change 事件后同步
- `.number`: 将数据自动转换为数值
- `.trim`: 过滤首尾空白字符

### 自定义修饰词

通过 props 传入 modelModifiers

```js
modelModifiers: {
      default: () => ({})
    }
```

## 条件渲染 v-if

```html
<p v-if="key">根据key是真或假来决定是否显示p</p>
```

一般来说，`v-if` 有更高的切换开销，而 `v-show` 有更高的初始渲染开销。因此，如果需要非常频繁地切换，则使用 `v-show` 较好；如果在运行时条件很少改变，则使用 `v-if` 较好。

## 列表渲染 v-for

```html
<ul>
	<li v-for="item in list">{{ item.text }}</li>
	<!-- 第二个参数作为索引 -->
	<li v-for="(item, index) in list">{{ item.text }}</li>
	<!-- 也可以遍历一个对象，形参分别是值、键、索引 -->
	<li v-for="(value, key, index) in object">{{ item.text }}</li>
	<!-- 一般列表渲染时要给元素一个 key 属性 -->
	<li v-for="item in list" :key="item.id">{{ item.text }}</li>
</ul>
```

## 事件处理 v-on

响应用户输入

```html
<button v-on:click="clickHandler">点击按钮</button>
```

这是缩写形式

```html
<a @click="doSomething">...</a>
```

### 事件的一些修饰词

-   `.stop`  停止冒泡
-   `.prevent`  阻止默认行为
-   `.capture`  事件捕获，即先在此处理内部元素触发的事件再交由内部元素处理
-   `.self`  只有事件由自己触发时响应
-   `.once`  只响应一次
-   `.passive`  立即触发默认行为

例子：

```html
<button @click.stop="handler">按钮</button>
```

### 一些按键修饰符

-   `.enter`
-   `.tab`
-   `.delete` (捕获“删除”和“退格”键)
-   `.esc`
-   `.space`
-   `.up`
-   `.down`
-   `.left`
-   `.right`

例子：

```html
<input @keyup.page-down="onPageDown" />
```

### 系统修饰键

可以用如下修饰符来实现仅在按下相应按键时才触发鼠标或键盘事件的监听器。

-   `.ctrl`
-   `.alt`
-   `.shift`
-   `.meta`

> meta 是 Windows 上的 `Win` 键，Mac 上的 `Command` 键。

#### `.exact` 修饰符

`.exact` 修饰符允许你控制由精确的系统修饰符组合触发的事件。

### 鼠标按钮修饰符

-   `.left`
-   `.right`
-   `.middle`

## 组件

### 插槽

用 `<slot></slot>` 来表示占位符

```html
<slot></slot>
```

### 动态组件

```html
<component :is="currentComponent"></component>
```

### Props

可以像这样给定组件的 props

```js
props: ['title', 'likes', 'isPublished', 'commentIds', 'author']
```

可以像这样给定属性的类型以便于错误检查。

```js
props: {
  title: String,
  likes: Number,
  isPublished: Boolean,
  commentIds: Array,
  author: Object,
  callback: Function,
  contactsPromise: Promise // 或任何其他构造函数
}
```

可以传递一个对象里的每一个属性：

对于一个对象

```js
post: {
  id: 1,
  title: 'My Journey with Vue'
}
```

可以这样：

```html
<blog-post v-bind="post"></blog-post>
```

等价于：

```html
<blog-post v-bind:id="post.id" v-bind:title="post.title"></blog-post>
```

> 注意：在 [[JavaScript]] 中对象和数组是通过引用传入的，所以对于一个数组或对象类型的 prop 来说，在子组件中改变这个对象或数组本身**将会**影响到父组件的状态，且 Vue 无法为此向你发出警告。

----------------------------------

## 关于 Vue 的一些库集合

[vuejs/awesome-vue: 🎉 A curated list of awesome things related to Vue.js (github.com)](https://github.com/vuejs/awesome-vue)

[Awesome Vue packages - Awesome JS](https://awesomejs.dev/for/vue/)

