

#操作dom
>在指定上下文[context]中，通过元素的标签名来获取一组元素
```
	var newlist = newsbox.getElementsByTagName('li');
	//=>获取的结果也是一个对象数据类型的值
	//1，以数字作为属性名，每一个属性存储的都是获取到的每一个li,js中我们把数字属性名叫做‘索引’（索引是逐级递增的）
	newlist[0] 第一个
	newlist[1] 第二个	
	//2有一个length属性存储的是当前集合中li的个数
	newslist.length
	//具备以上两个特点特别想数组，但不是数组，所以我们把它称之为类数组
```
