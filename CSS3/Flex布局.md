# Flex 布局图文详解

> 前言
> CSS3 中的 flex 属性,在布局方面做了非常大的改进，使得我们对多个元素之间的布局排列变得十分灵活，适应性非常强。其强大的伸缩性和自适应性，在网页开发中发挥极大作用。

> flex 布局的优势

1. flex 布局的子元素不会脱离文档流,很好地遵循了文档流的特性。
2. flex 是一种现代的布局方式，是 W3C 第一次提供真正用于布局的 CSS 规范。

> flex 的兼容性问题
> flex 布局不支持IE9及以下的版本；IE10及以上也只是部分支持。

> 概念1 弹性盒子、子元素/弹性元素
- 弹性盒子：指使用`display: flex`或`display: inline-flex`声明的父容器。
- 子元素/弹性元素：指的是父容器里的子元素（父容器为弹性盒子的情况下）。

> 概念2 主轴和侧轴

- 主轴：flex容器的主轴，默认是水平方向，从左到右。
- 侧轴：与主轴垂直的轴称作侧轴，默认是垂直方向，从上至下。

PS：主轴和侧轴可以通过`flex-direction`更换方向。

> 弹性盒子

### 定义声明

使用 `display: flex` 或 `display: inline-flex` 声明一个容器为弹性盒子。此时，这个容器里的子元素会遵循弹性布局。
PS：一般使用 `display:flex`，而 `display: inline-flex` 用的较少。

> flex-direction
> 设置盒子中子元素的排列方式。

// reverse 有反转/失败之意

| 属性值      | 描述                   |
| ----------- | ---------------------- |
| row         | 从左到右水平排列(默认) |
| row-reverse | 从右到左排列           |
| column      | 从上到下垂直排列       |
| column      | 从上到下垂直排列       |

> flex-wrap 
> 控制子元素溢出时的换行处理

> 弹性元素

## justify-content属性
`justify-content: flex-start;` 设置子元素在**主轴上的对齐方式.**

| 属性值        | 解释                   |
| ------------- | ---------------------- |
| flex-start    | 从主轴的起点对齐(默认) |
| flex-end      | 从主轴的终点对齐       |
| center        | 居中对齐               |
| space-around  | 在父盒子里平分         |
| space-between | 两端对齐 评分          |

## align-items 属性
`align-items`: 设置子元素在侧轴上的对齐方式。

| 属性值     | 解释                   |
| ---------- | ---------------------- |
| flex-start | 从侧轴开始的方向对齐   |
| fiex-end   | 从侧轴结束的方向对齐   |
| baseline   | 基线。默认同flex-start |
| center     | 中间对齐               |
| stretch    | 拉伸                   |

## `flex: value;(value > 0)`设置子盒子的权重

>相关链接

[【中文翻译】CSS Flexbox 可视化手册](https://zhuanlan.zhihu.com/p/56046851)
[【英文原版】CSS Flexbox Fundamentals Visual Guide](https://medium.com/swlh/css-flexbox-fundamentals-visual-guide-1c467f480dac)

>推荐文章

[flex 效果在线演示](https://demos.scotch.io/visual-guide-to-css3-flexbox-flexbox-playground/demos/)
[【中文翻译】CSS3 Flexbox 布局完全指南](https://www.html.cn/archives/8629)
[【英文原版】A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)