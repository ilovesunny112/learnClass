

#DOM基础
> dom : document object model 文档对象模型，提供一些属性和方法可以操作dom元素

### 获取dom元素的方法
- document.getElementById 
  + 获取id 一个元素
  + //此方法的上下文只能document
  + id不能重复的
- document.getElementsByTagName
  + 上下文是可以自己来指定的
  + 获取到的结果是一个元素集合（类数组集合）
- getElementsByClassName 元素集合
  + 上下文也可以随意指定
  + 经常根据样式类名来获取元素 IE678不兼容
  + 后期会实现一个自己的方法
-  getElementsByName
  + 通过元素的name属性值获取一组元素（类数组：节点集合nodelist）
  + 上下问是document
  + ie浏览器中只能识别表单元素的name属性值，所以我们这个方法都是操作表单元素的
-  document.getElementsByName 节点集合
- doument.documentElement 获取整个html对象
  + 获取文档
- document.body 获取body对象
  + 获取body元素的
```javascript
	var winH = document.documentElement.clientWidth || document.body.clientWidth
	//获取当前浏览器窗口可视区的宽度（当前屏幕的宽度）
```
- querySelector 一个元素对象
 + ie678不兼容，多用于移动端
 + 获取一个元素对象
- querySelectorAll 获取元素集合
 + ie678不兼容，多用于移动端
 + 获取一个元素集合