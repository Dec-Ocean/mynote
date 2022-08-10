# CSS3新增属性  

> 文本  

**text-shadow:设置文本的阴影**  

```
{
  text-shadow: 20px 27px 22px pink，-1px -1px 1px #fff;
  #参数解释：水平位移 垂直位移 模糊程度 阴影颜色
  #text-shadow可设置多个阴影，阴影之间用","隔开
}
```  

> **盒子模型中的box-sizing属性**  

CSS3对盒子模型做出了新的定义：允许开发人员**指定盒子宽度和高度的计算方式**。

```
{
  #外加模式：（默认方式）
  box-sizing: content-box;
  #设置的width和height为content（内容）区域的宽高
  #盒子的实际宽度 = width + padding + border
  #盒子的实际高度 = height + padding + border
  
  #内减模式：
  box-sizing: border-box；
  #设置的width和height为盒子的总宽高。
  #盒子的实际宽度 = width
  #盒子的实际高度 = height
  #此时padding和border的大小，会改变内容的宽和高，不影响盒子的宽和高
  }
```  

> **处理兼容性问题：私有前缀**  

我们可以通过<caniuse>(http://caniuse.com/)查询CSS3各特性的支持程度。
  在处理兼容性问题，我们常用的方法：为属性添加**私有前缀**。  

  格式如下:
  ```
  {
    -webkit-: 谷歌 苹果
    -moz-:火狐
    -ms0:IE
    -o-:欧朋
  }
``` 

举例如下:
```
{
  background: -webkit-linear-gradient(left, green, yellow);
  background: -moz-linear-gradient(left, green, yellow);
  background: -ms-linear-gradient(left, green, yellow);
  background: -o-linear-gradient(left, green, yellow);
  background: linear-gradient(left, green, yellow);
}
``` 

>边框

边框的属性很多,其中**边框圆角**和**边框阴影**这两个属性,应用十分广泛,兼容性也相对较好,且**符合渐进增强的原则**,需要重点熟悉.  
边框圆角:`border-radius`属性  
边框的每个圆角,本质上是一个圆,圆有**水平半径**和**垂直半径**:如果二者相等,就是圆;如果二者不等,就是椭圆. 

单个属性的写法:
```
{
  #参数解释:水平直径 垂直直径
  #左上角
  border-top-left-radius: 60px 120px; 
  #右上角
  border-top-right-radius: 60px 120px;
  #左下角
  border-bottom-left-radius: 60px 120px;
  #右下角
  border-bottom-right-radius: 60px 120px;
}
``` 

复合写法:
```
{
  border-radius: 60px/120px;  //参数: 水平半径/垂直半径

  border_radius: 20px 60px 100px 140px; //从左上角开始,顺时针赋值.如果当前角没有值,取对角的值

  border-radius: 20px 60px;

  border-radius: 60px;
}
``` 

>边框阴影:`box-shadow`属性

格式举例:
```
{
  box-shadow: 水平偏移 垂直偏移 模糊程度 阴影大小 阴影颜色

  box-shadow: 15px 21px 48px -2px #666;

  box-shadow: 3px 3px 3px 3px #666 inset; //inset属性,表示内阴影.如果不写,则默认为外阴影.
}
```

参数解释:
- 水平偏移: 正值向右 负值向左.
- 垂直偏移: 正值向下 负值向上.
- 模糊程度: 不能为负值.


