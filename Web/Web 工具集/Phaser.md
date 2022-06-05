[Phaser 官网](http://phaser.io/)

------------------------

[在线文档](https://photonstorm.github.io/phaser3-docs/index.html)

## 特性

-  使用 WEBGL & [[Canvas]]
-  支持预加载
-  内置物理引擎：Arcade Physics, Impact Physics, [[Matter.js]]
- 支持移动端

## Get Start

```js
<!DOCTYPE html>

<html>

<head>
    <script src="https://cdn.jsdelivr.net/npm/phaser@3.15.1/dist/phaser-arcade-physics.min.js"></script>
</head>

<body>

    <script>

    var config = {
        type: Phaser.AUTO,
        width: 800,
        height: 600,
        physics: {
            default: 'arcade',
            arcade: {
                gravity: { y: 200 }
            }
        },
        scene: {
            preload: preload,
            create: create
        }
    };
    
    var game = new Phaser.Game(config);  

    function preload ()
    {
        this.load.setBaseURL('http://labs.phaser.io');  

        this.load.image('sky', 'assets/skies/space3.png');
        this.load.image('logo', 'assets/sprites/phaser3-logo.png');
        this.load.image('red', 'assets/particles/red.png');
    }

    function create ()
    {
        this.add.image(400, 300, 'sky');
        var particles = this.add.particles('red');
        var emitter = particles.createEmitter({
            speed: 100,
            scale: { start: 1, end: 0 },
            blendMode: 'ADD'
        });
        
        var logo = this.physics.add.image(400, 100, 'logo');
        logo.setVelocity(100, 200);
        logo.setBounce(1, 1);
        logo.setCollideWorldBounds(true);  

        emitter.startFollow(logo);
    }
    </script>
</body>

</html>
```

## 配置

一个模板如下：

```js
var config = {
    type: Phaser.AUTO,  //渲染环境
    width: 800,
    height: 600,
    scene: {
        preload: preload,
        create: create,
        update: update
    }
};
```

```js
this.add.image(0, 0, 'sky').setOrigin(0, 0);
// 设置图片的锚点为 (0, 0)
```

- `type:`
	- `Phaser.AUTO`
	- `Phaser.WEBGL`
	- `Phaser.CANVAS`

## Scene

Scene 是一些游戏对象的逻辑集合，可以更好地管理游戏的各部分。

```js
class Game extends Phaser.Scene
{
	constructor() {
		super('game');  // 为 Scene 指定一个 key
	}
}
```

### preload

一般用于加载图片、音频等资源

```js
preload()
{
	// 加载一个图片，并命名为 dude
	this.load.image('dude', 'assets/dude.png');
}
```

