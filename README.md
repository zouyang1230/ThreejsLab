# ThreejsDemos

使用 Threejs 实现的3D效果demo。

记录自己学习的一个过程。

所有项目均使用了2个开发环境用的测试辅助库：
*  stats.js性能监视器来监视3d性能，详见各个demo左上角（它的介绍在https://github.com/mrdoob/stats.js ）
*  GUI库( dat.gui.js )，详见各个demo右上角，用户可进行控制操作（https://github.com/dataarts/dat.gui ）

## Demo：
1、<a href="http://zouyang1230.com/project/threejs/areaLight.html" target="_blank">平面光3d光源</a>
（该页面右上角各GUI参数可控制3d变化）
* 该光源：属于复杂光源、使用它可以定义一个发光的矩形、此光源不再Three.js标准库中，而在它的扩展库中，它不能再使用渲染器WebGLRenderer对象了，而是使用渲染器WebGLDeferredRenderer，俗称延迟渲染器(使用此渲染器还需引入其他js，详见demo，才能使用延迟渲染器)，该渲染器专门处理复杂光源。

2、<a href="http://zouyang1230.com/project/threejs/card.html" target="_blank">多米诺骨牌</a>
（该页面右上角各GUI参数可控制3d变化）







