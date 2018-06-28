

#导入js方式

### 方式
1. 行内导入
```
	<div onclick="alert('hello word')">hell word</div>
```
2. 内嵌式引入
```
	<script>
		alert('hello word')
	</script>
```
3. 外链式
```
	<script src="helloword.js"></script>
	//hellowd.js
	alert('hello word')
```
4. 外链和内嵌混写 是不可以的
```
	<script src="helloword.js">
		alert('内嵌') // error no active
	</script>
```
5. 位置：body结束之前 约定规范
6. 为什么把js放到body末尾
	- js要操作这些元素，首先保证有这个元素
7. 异步引入
```
	<script async></script>
	<script deffer></script>
	// https://segmentfault.com/q/1010000000640869
```
8. 解决顺序问题
```
	js: window.onload = function(){}
	jq: $(document).ready(function(){})
	window.addEventListener('load', function(){}, false)
	widnow.attachEvent('onreadystatechange', function(){})
```
### 额外补充
> 1. 写静态页面
		- ui设计师（给设计稿psd）
		- 用html和css转化成静态页面
> 2. 拿js写一些用户交互的效果
		- 点击按钮弹出个框框
		- js常用操作就是操作页面的html标签（dom元素）