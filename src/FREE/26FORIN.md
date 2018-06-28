
# for in
> 语法：用来遍历对象键值对的
> 循环次数 不一定循环对数 。hasOwnProperty
> key存储的值都是字符串格式的（typeof key -> string）
> 在for in循环遍历的时候，大部分浏览器都是先把对象中的键值对进行排序的（把数字属性名的拍在前面，并且排列的时候按照数字由小到大排列），其次在把非数字的属性名按照之前的编写的排列顺序(小数算做字母不算数字)
> 
```
	var obj = {
		name: 'rain',
		sex: '男'，
		age: 1，
		5: 1
	}
	
	for(var key in obj) {
		//if(obj.hasOwnProperty(key)) {
			console.log(obj[key]) //默认没有就是undefined
		//}
		
	}
```