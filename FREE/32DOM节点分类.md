


# DOM节点分类
>dom中节点和描述节点关系的属性

### DOM的节点
> node: 节点， 浏览器认为在一个html页面中的所有内容都是节点（标签，注释，文字文本）
>  - 元素节点： html标签
>  - 文本节点： 文字内容（大部分浏览器会把空格和换行也当作文本节点，除ie678）
>  - 注释节点：注释内容
>  - document文档节点： 整个文档

### 元素节点
- nodeType: 1
- noeName: 大写的标签名（部分浏览器的怪异模式下，写的标签名是小写，它获取的就是小写）
- nodeValue: null
- ele.tagName: 获取当前元素的标签名（返回的一般都是大写相比nodename好用）

### 文本节点
- nodeType: 3
- nodeName: #text
- nodeValue: 文本内容


### 注释节点
- nodeType: 8
- nodeName: #comment
- nodeValue: 注释内容

### 文档节点
- nodeType: 9
- nodeName: #document
- nodeValue: null

### 节点关系属性
> 节点是用来描述页面中每一部分之间关系的
> 画出dom树举例子
> 知道其中一个就可以获取到所有的节点

> - `childNodes`
>  + 获取当前元素所有的子节点集合（类数组）
>  + 注：不仅仅是元素子节点，文本，注释等都会包含在内；子节点说明只是在儿子备份查找
> - `children`
>  + 获取所有的元素子节点（元素集合）
>  + ie678和标准浏览器中有区别（6～8会把注释节点当作元素节点）
> - `parentNode`
>  + 获取当前元素的父节点(元素对象)
> - `previousSibling`
>  + 获取当前节点的上一个哥哥节点（不一定是元素节点可能是文本或者注释）
> - `nextSibling`
>   + 获取当前节点的上一个弟弟节点（不一定是元素节点可能是文本或者注释）
> - `previousElementSibling`
>    + 获取当前节点的上一个哥哥元素节点
>    + 678不兼容没有这属性
> - `nextElementSibling`
>    + 678不兼容没有这属性
> - `firstChild`
>   + 当前元素所有子节点中的第一个（也不一定是元素节点） 
> - `lastChild`
>   + 当前元素所有节点的最后一个
> - `firstElementChild` 
>    + 678不兼容没有这属性
> - `lastElementChild`
>    + 678不兼容没有这属性


###dom增删改
> 真实项目中，要动态创建一些html标签，然后把其增加到页面中
#### 动态创建标签
> - document.createElement
>  + 在js中动态创建一个html标签
> - appendChild
>  + 容器.appendChild(新元素)
>  + 把当前创建的新元素添加到容器的末尾位置
> - insertBefore
>  + 容器.insertBefore(新元素，老元素)
>  + 在当前容器中，把新元素的元素添加到老元素之前

```
		var oDiv = document.createElement('a');
		oDiv.href = 'http://baidu.com?fdfd=4234#sasa'
		// oDiv.hash
		// oDiv.hostname
		// oDiv.pathname
		// oDiv.protocol
		// oDiv.search
		// oDiv.href
		console.dir(oDiv)

		var text = document.createTextNode('<span>11111</span>')
		oDiv.id = 'div1';
		oDiv.className = 'box';

		document.body.insertBefore(oDiv, document.getElementById('box2'))
		//'a=&b=3'.split(/&|=/g) 
```

### dom元素删除
> 容器.removeChild(元素)
> 容器.replaceChild(新元素，老元素)


### cloneNode
> 元素.cloneNode(false/true)
> 把原有的元素克隆一份一摸一样的
> false只克隆元素本身
> true 以及元素后代都进行克隆
```
		var box2 = document.getElementById('box2');
		var box11 = document.getElementById('box1');
		box11.onclick = function() {
			alert(1)
		}
		//document.body.removeChild(box11)
		//box11.parentNode.removeChild(box2)
		var box3 = box11.cloneNode(true);
		console.dir(box3)
		document.body.appendChild(box3)
```

### set/get/remove Attribute
> 给当前元素设置/获取/移除属性的（自定义属性居多）
> .index =0 和 set(index,0)区别 (和页面中的html没关系)
>  + .index: 是把当前操作的元素当作一个普通对象，为其设置一个属性名
>  + set: ：把元素当作特殊的元素对象来处理的，设置自定义属性和页面结构中的dom元素映射在一起
>  + 举例子
>    + 于页面html结构无关的普通对象
>    + 与页面html结构存在映射关系的元素对象
>  + 元素对象中的内置属性，大部分都和页面的标签存在映射关系 style例子


### demo 获取哥哥元素
`prev方法实现`
> 需求： 获取当前元素的上一个哥哥元素节点，兼容所有浏览器
> 1. curEle: 获取当前节点
>   + document.getElementById
> 2. 获取上一哥哥节点
>   + 判断是不是元素节点，不是继续向上找，找到为止，最后没有直接返回null
```
		function prev(curEle) {
			var p = curEle.previousSibling;
			while (p && p.nodeType != 1) {
				p = p.previousSibling;
			}
			return p;
		}
```


### while循环
while(条件) {循环体}

### 作业题
`next, prevAll, nextAll, siblings, index`