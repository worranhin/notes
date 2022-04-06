[Matter.js - a 2D rigid body JavaScript physics engine · code by @liabru (brm.io)](https://brm.io/matter-js/)

-------------------------------

Matter.js 是一个 [[JavaScript]] 的物理引擎框架。

## Engine
### methods
- `create([options])` 创建engine
- `clear(engine)` 清除engine
- `merge(engineA, engineB)` 将 A 的 world 替换为 B 的 world
- `run(engine)` 运行

### Properties
- `enableSleeping (Boolean)` able sleeping
- `engine.gravity  Object`  重力
	- `gravity.scale` 比例
	- `gravity.x` 
	- `gravity.y`

## Vector
- `Matter.Vector.dot(vectorA, vectorB)` 点乘