> 前言

本文主要内容:

- 过渡: transition
- 2D 转换: transform
- 3D 转换: transform
- 动画: animation

> 过渡: **transition**

`transition`的中文含义是**过渡**。
过渡是CSS3中具有颠覆性的一个特征,可以**实现元素不同状态间的平滑过渡(补间动画)**,经常用来制作动画效果。

- 补间动画：自动完成从起始状态到终止状态的过渡。
- 帧动画：以固定的顺序和速度播放播放每一帧动画。

transition 包括以下属性:
- `transition-property: all;` 使所有属性发生过渡；
- `transition-duration: 1s;` 过渡动画的持续时间；
- `transition-timing-function: linear;` 运动曲线。属性如下：
  
    - linear 线性
    - ease 减速
    - ease-in 加速
    - ease-out 减速
    - ease-in-out 先加速后减速

- `transition-delay: 1s;` 过渡动画延迟。多久后再执行这个过渡动画

复合格式:

``` css
{
    transition: 过渡属性 持续时间 运动曲线 延迟;

    transitionL all 3s linear 0s;
}
```

> 2D 转换

**转换**是 CSS3 中具有颠覆性的一个特征,它可以实现**元素的位移/旋转/变形/缩放**,甚至支持矩阵方式。
转换再配合过渡和动画，可以取代大量早期只能靠 flash 才可以实现的效果。

在 CSS3 当中，通过 `transform` 转换来实现 2D 转换或者 3D 转换。
- 2D 转换包括：缩放、移动、旋转。

1. 缩放：`scale`

``` CSS
{
    transform: scale(x, y);

    transform: scale(2, 0.5);

    /* value>1 表示放大，value<1 表示缩小。值不能为百分比 */
    /* X：表示水平方向的缩放倍数。 */
    /* Y：表示垂直方向的缩放倍速 */
    /* 如果只写一个值就是等比缩放。 */
}
```

2. 位移：`translate`

``` CSS
{
    transfrom: translate(水平位移， 垂直位移);
    
    transform: translate(-50%, -50%);

    /* 参数为百分比,相对于自身移动。 */
    /* 正值：向右和向下、 */
    /* 负值：向左和向上。 */
    /* 只写一个值，表示水平移动。 */
}
```

> 应用
通过 `translate` 让绝对定位的盒子在父类中居中

``` CSS
{
    div{
        width: 600px;
        height: 60px;
        position: absolute; 
        /* 绝对定位的盒子 */
        left: 50%;
        /* 1.让盒子左边的线段居中 */
        top: 0;
        transform: translate(-50%);
        /* 2.利用 translate ,让盒子往左走自己宽度的一般. */
        /* 推荐写法 */
    }
}
```

另外的办法:

``` CSS
{
    div {
        weight: 600px;
        height: 60px;
        position: absolute;
        /* 绝对定位的盒子 */
        left: 50%;
        /* 让盒子的左边的线段居中 */
        top: 0;
        margin-left: -300px; 
        /* 向左移动宽度的一半 */
    }
}
```

3.旋转: rotate

``` CSS
{
    transform: rotate(角度);

    transform: rotate(45deg);
    /* value > 0 为顺时针; */
    /* value < 0 为逆时针; */
}
```

`rotate`旋转时,默认是以盒子的正中心为原点坐标.  
如果想要改变旋转的坐标原点,可以用 `transform-origin` 属性.

``` CSS
{
    transform-origin: 水平坐标 垂直坐标;

    transform-origin: 50px 50px;
    
    transform-origin: center bottom;
    /* 旋转时,以盒子底部的中心为坐标原点 */
}
```

4.倾斜

>3D 转换

1. 旋转： `rotateX` ` rotateY` `rotateZ`

**浏览器的平面是 X轴、Y轴；**
**垂直于浏览器的平面是 Z轴**

``` CSS
{
    transform: rotateX(360deg); 
    /* 绕 X轴旋转360度 */

    transform: rotateY(360deg);
    /* 绕 Y轴旋转360度 */

    transform: rotateZ(360deg);
    /* 绕 Z轴旋转360度 */
}
```
2. 移动： `translateX` `translateY` `translateZ`

``` CSS
{
    transform: translateX(100px);
    /* 沿着　X轴移动 */
    
    transform: translateY(100px);
    /* 沿着　Y轴移动 */

    transform: translateZ(100px);
    /* 沿着　Z轴移动 */
}
```

3. 透视: `perspective`

透视可以将一个 2D 平面，在转换的过程当中，呈现出 3D效果。但仅仅只是视觉呈现出 3D效果，并不是真正的 3D。

`perspective`格式：
- 作为一个属性，设置给父元素，作用于所有 3D转换的子元素；
- 作为`transform`属性的一个值，作用于元素自身。

4. 3D呈现 `transform-style`

3D 元素构成是指某个图形是由多个元素构成的，可以给这些元素的父元素设置`transform-style: preserve-3d` 来使其变成一个真正的3D图形。

``` CSS
{
    transform-style: preserve-3d;
    /* 让 子盒子 位于三位空间 */

    transform-style：float；
    /* 让子盒子位于此元素所在的平面（扁平化） */
}
```

>动画

动画是CSS3中具有颠覆性的特征，可通过设置**多个节点**来精准控制一个或一组动画，常用来实现**复杂**的动画效果。

1. 定义动画的步骤：
   1. 通过 @keyframes 定义动画；
   2. 将这段动画通过百分比，分割成多个节点；任何各节点中分别定义各属性；
   3. 在指定元素里，通过`animation`属性调用动画。

``` CSS 
{
    定义动画:
        @keyframes name{
            from{初始状态}
            to{结束状态}
        }

    调用：
        animation: 动画名称 持续时间;
        animation: name duration;

        animation: 动画名称 持续时间 执行次数 是否方向 运动曲线 延迟执行；（infinite，表示无限次）

        /* 动画名称 */
        animation-name: move;

        /* 动画的持续时间 */
        animation-duration: 4s;

        /* 动画的执行次数 */
        animation-iteration-count: 1; //iteration的含义表示迭代

        /* 动画的方向 */
        animation-direction: alternate;

        /* 动画延迟执行 */
        animation-delay: 1s;

        /* 设置动画结束后的盒子的状态 */
        animation-fill-mode: forwards；
        /* forwards 保持动画结束后的状态（默认） */
        /* backwards 回到最初的状态 */

        /* 运动曲线 */
        animation-timing-function: ease-in;
        /* linear 线性 */
        /* ease-in-out 加速/减速/减速后加速/加速后减速 */
        /* steps() 阶段性动画 */
}
```

