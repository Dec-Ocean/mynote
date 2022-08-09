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
