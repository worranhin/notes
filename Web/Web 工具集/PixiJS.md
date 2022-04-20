---
Tags: 
aliases: []
---

PixiJS 是一个 [[JavaScript]] 的 [[WebGL]] 渲染器。

>看到[这里](https://pixijs.io/guides/basics/architecture-overview.html)了。

## 组件

**Renderer**  
`@pixi/core`

The core of the PixiJS system is the renderer, which displays the scene graph and draws it to the screen. The default renderer for PixiJS is based on WebGL under the hood.

**Container**  
`@pixi/display`

Main display object which creates a scene graph: the tree of renderable objects to be displayed, such as sprites, graphics and text. See [Scene Graph](https://pixijs.io/guides/basics/scene-graph.html) for more details.

**Loader**  
`@pixi/loader`

The loader system provides tools for asynchronously loading resources such as images and audio files.

**Ticker**  
`@pixi/ticker`

Tickers provide periodic callbacks based on a clock. Your game update logic will generally be run in response to a tick once per frame. You can have multiple tickers in use at one time.

**Application**  
`@pixi/app`

The Application is a simple helper that wraps a Loader, Ticker and Renderer into a single, convenient easy-to-use object. Great for getting started quickly, prototyping and building simple projects.

**Interaction**  
`@pixi/interaction`

PixiJS supports both touch and mouse-based interaction - making objects clickable, firing hover events, etc.

**Accessibility**  
`@pixi/accessibility`

Woven through our display system is a rich set of tools for enabling keyboard and screen-reader accessibility.