[webpack][] 是一个[[web]]打包工具。

[webpack]: https://webpack.docschina.org/

## 安装

```shell
npm install --save-dev webpack webpack-cli
```

## 配置

```js
const path = require('path');

module.exports = {

 entry: {
	 index: './src/index.js',  // 程序入口
 },

 output: {  // 输出
	 filename: '[name].bundle.js',
	 path: path.resolve(__dirname, 'dist'),
	 clean: true,  // 构建前清空目标文件夹
 },

 mode: 'production',  // 生产模式或开发模式(development)

};
```

> 可以用 [[createapp.dev]] 快速配置

## 开发工具

### devServer

```js
devServer: {
 static: './dist',
 },
 ```

## 插件

### HtmlWebpackPlugin
```shell
npm install --save-dev html-webpack-plugin
```

```js
const HtmlWebpackPlugin = require('html-webpack-plugin');

//...
plugins: [
 new HtmlWebpackPlugin({
	 title: 'Development',
 }),
 ],
```

## 预获取与预加载

预获取 (prefetch)：获取将来导航可能需要的资源
预加载 (preload)：获取当前导航下可能需要的资源

```js
import(/* webpackPrefetch: true */ './path/to/LoginModal.js');
```

## 分析代码的工具

-   [webpack-chart](https://alexkuz.github.io/webpack-chart/): webpack stats 可交互饼图。
-   [webpack-visualizer](https://chrisbateman.github.io/webpack-visualizer/): 可视化并分析你的 bundle，检查哪些模块占用空间，哪些可能是重复使用的。
-   [webpack-bundle-analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer)：一个 plugin 和 CLI 工具，它将 bundle 内容展示为一个便捷的、交互式、可缩放的树状图形式。
-   [webpack bundle optimize helper](https://webpack.jakoblind.no/optimize)：这个工具会分析你的 bundle，并提供可操作的改进措施，以减少 bundle 的大小。
-   [bundle-stats](https://github.com/bundle-stats/bundle-stats)：生成一个 bundle 报告（bundle 大小、资源、模块），并比较不同构建之间的结果。