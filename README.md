# ThreejsLab

记录自己学习的一个过程。

所有项目均使用了2个开发环境用的测试辅助库：
*  stats.js性能监视器来监视3d性能，详见各个demo左上角（它的介绍在 <https://github.com/mrdoob/stats.js> ）
*  GUI库( dat.gui.js )，详见各个demo右上角，用户可进行控制操作（ <https://github.com/dataarts/dat.gui> ）

## Demo：
(所有demo页右上角有`GUI渲染控制器`，可通过调节它来控制页面的3d效果变化)


1、[平面光3d光源](http://imzouyang.com/project/threejs/areaLight.html)（该页面右上角各GUI参数可控制3d变化）
* 该光源：属于复杂光源、使用它可以定义一个发光的矩形、此光源不再Three.js标准库中，而在它的扩展库中，它不能再使用渲染器WebGLRenderer对象了，而是使用渲染器WebGLDeferredRenderer，俗称延迟渲染器(使用此渲染器还需引入其他js，详见demo，才能使用延迟渲染器)，该渲染器专门处理复杂光源。
<br /><br />

2、[几何体及网格](http://imzouyang.com/project/threejs/meshMaterial.html)
* 注释：Mesh几何体为groundGeom；通过MeshNormalMaterial作为几何体材质展示旋转色变（MeshNormalMaterial ：通过计算法向颜色来决定每个面颜色的材质）。<br />
![几何体及网格示意图](https://github.com/zouyang1230/ThreejsDemos/raw/master/images/meshMaterial.gif)
<br /><br />

3、[gosper曲线](http://imzouyang.com/project/threejs/lineMaterial.html)
* gosper()，该函数返回的是一个gosper曲线。wiki有相关介绍：（ <https://en.wikipedia.org/wiki/Gosper_curve> ）<br />
![osper曲线示意图](https://github.com/zouyang1230/ThreejsDemos/raw/master/images/lineMaterial.gif)
<br /><br />

4、[创建三维文本](http://imzouyang.com/project/threejs/textGeometry.html)
* 实例化new THREE.TextGeometry(),并操作相关属性即可<br />
![创建三维文本示意图](https://github.com/zouyang1230/ThreejsDemos/raw/master/images/textGeometry.jpg)
<br /><br />

5、[创建粒子材质](http://imzouyang.com/project/threejs/pointCloud.html)
* 实例化new THREE.ParticleBasicMaterial(),创建粒子材质，该材质有9个可控属性<br />
![创建粒子材质示意图](https://github.com/zouyang1230/ThreejsDemos/raw/master/images/pointCloud.gif)
<br /><br />

6、[创建下雨3d动画](http://imzouyang.com/project/threejs/rainyScene.html)
* 使用ParticleBasicMaterial的map属性来加载外部图片；并使用 THREE.AdditiveBlending融合模式，此模式会在画新像素时，背景像素的颜色会被添加到新像素上<br />
![创建下雨3d动画](https://github.com/zouyang1230/ThreejsDemos/raw/master/images/rainyScene.gif)
<br /><br />

7、[创建下雪3d动画](http://imzouyang.com/project/threejs/snowyScene.html)<br />
![创建下雨3d动画](https://github.com/zouyang1230/ThreejsDemos/raw/master/images/snowyScene.gif)
<br /><br />

8、[基础材质应用](http://imzouyang.com/project/threejs/basicTexture.html)
* 使用THREE.ImageUtils.loadTexture 来加载一个外部图片
* threejs内有2种材质对光源产生反应：MeshLamberMaterial  和  MeshPhongMaterial，MeshPhongMaterial一般用于创建光亮表面<br />
![基础材质应用](https://github.com/zouyang1230/ThreejsDemos/raw/master/images/basicTexture.gif)
<br /><br />

9、[基础材质应用2](http://imzouyang.com/project/threejs/normalMap.html)
* 使用THREE.UniformsUtils的clone方法
* 创建立方体BoxGeometry<br />
![基础材质应用2](https://github.com/zouyang1230/ThreejsDemos/raw/master/images/normalMap.gif)
<br /><br />

10、[构建真实动态3d场景](http://imzouyang.com/project/threejs/dynamic.html)<br />
* 拖动(滚动)鼠标可360度查看全景，整个场景是由6张jpg图片够成。
![构建真实动态3d场景](c)
<br /><br />


# 以下是一些记录：
1、Three.js本质上是Webgl，如果你的浏览器不支持Webgl，那么肯定你就不能完整的运行Three.js。支持Webgl的浏览器很多，例如Chrome、FireFox、360安 全浏览器6.0等，而IE浏览器对Webgl标准的支持就不太好。<br />

2、在Three.js中，要渲染物体到网页中，我们需要3个组件：场景（scene）、相机（camera）和渲染器（renderer）。有了这三样东西，才能将物体渲染到网页中去。
```javascript
var scene = new THREE.Scene();	// 场景

var camera = new THREE.PerspectiveCamera(75, window.innerWidth/window.innerHeight, 0.1, 1000);// 透视相机

var renderer = new THREE.WebGLRenderer();	// 渲染器

renderer.setSize(window.innerWidth, window.innerHeight);	// 设置渲染器的大小为窗口的内宽度，也就是内容区的宽度
document.body.appendChild(renderer.domElement);
```

3、场景与相机
* 1）场景只有一种，用THREE.Scene来表示，通过new THREE.Scene();
* 2）相机有2种，决定了场景中那个角度的景色会显示出来。
* 透视投影相机：THREE.PerspectiveCamera
* 正投影相机：THREE.OrthographicCamera ( left, right, top, bottom, near, far )  里面的参数分别代表各个面与相机镜头中心点的垂直距离。

4、Threejs使用的是右手坐标系，这源于opengl默认情况下，也是右手坐标系。

5、和three.js紧密结合的动画引擎是Tween.js,可以在这里下载 https://github.com/sole
```
1）引入js<br />
2）构建对象：<br />
function initTween()
{
    new TWEEN.Tween( mesh.position)
            .to( { x: -400 }, 3000 ).repeat( Infinity ).start();
}
TWEEN.Tween的构造函数接受的是要改变属性的对象，这里传入的是mesh的位置。
Tween的任何一个函数返回的都是自身，所以可以用串联的方式直接调用各个函数。
to函数，接受两个参数：
第一个参数是一个集合，里面存放的键值对，键x表示mesh.position的x属性，值-400表示，动画结束的时候需要移动到的位置。
第二个参数，是完成动画需要的时间，这里是3000ms。
repeat( Infinity )表示重复无穷次，也可以接受一个整形数值，例如5次。
Start表示开始动画，默认情况下是匀速的将mesh.position.x移动到-400的位置。
3)渲染函数中执行：TWEEN.update();
```

6、Threejs中的各种光源：
* 光源基类 THREE.Light ( hex )
```
参数hex，接受一个16进制的颜色值。例如要定义一种红色的光源，我们可以这样来定义：
var redLight = new THREE.Light(0xFF0000);
```
* 由基类派生出来的其他种类光源

7、环境光<br />
是经过多次反射而来的光称为环境光，无法确定其最初的方向。环境光是一种无处不在的光。环境光源放出的光线被认为来自任何方向。因此，当你仅为场景指定环境光时，所有的物体无论法向量如何，都将表现为同样的明暗程度。 （这是因为，反射光可以从各个方向进入您的眼睛）
构造函数 : THREE.AmbientLight( hex )
var light = new THREE.AmbientLight( 0xff0000 );
scene.add( light );

8、聚光灯<br />
构造：THREE.SpotLight( hex, intensity, distance, angle, exponent )	
这种光源的光线从一个锥体中射出，在被照射的物体上产生聚光的效果。
使用这种光源需要指定光的射出方向以及锥体的顶角α。


9、方向光（平行光）  
* 它是一组没有衰减的平行的光线，类似太阳光的效果。
* THREE.DirectionalLight = function ( hex, intensity )

10、点光源	
* 点光源的特点是发光部分为一个小圆面，近似一个点
* 是理想化为质点的向四面八方发出光线的光源。点光源是抽象化了的物理概念，为了把物理问题的研究简单化。就像平时说的光滑平面，质点，无空气阻力一样，点光源在现实中也是不存在的，指的是从一个点向周围空间均匀发光的光源。
* 点光源不会产生投影，原因是光源是朝所有方向发出，计算阴影对GPU来说，负担太重。

### 省略一大坨
```
 更多详细笔记，如有需要的童鞋可以私信我邮箱
```
















