# vue介绍
> - 一套构建用户页面的渐进式框架
> - 框架 vue react angular
>    + 拥有完整的解决方案，我们写好人家调用我
> - 库 jquery underscore zepto anmiate
>    + 我们调用他

### 渐进式（增强）
>  - vue 全家桶 vue + vue-router + vuex + axios
>  - 通过组合完成一个完整的框架

### 特点
> - 核心只关注视图层（view）
> - 易学，轻量，灵活的特点
> - 适用于移动端项目
> - 渐进式框架

### 渐进式理解
>  - 声明式渲染（不需要关心怎么实现）
>  - 组件系统
>  - 客户端路由（vue-router）
>  - 大规模状态管理（vuex）
>  - 构建工具(vue-cli)

### 核心
- 相应的数据变化
   + 当数据发生改变 -> 视图的自动更新
- 组合的视图组件
   + ui页面映射为组件树
   + 划分组件可维护，可复用，可测试

### 兼容
> 不支持ie8一下


### MVC 单向

### MVVM 双向


### 安装vue
>  - cdn地址
>  - npm安装  node package manager
>    + 初始化npm 会产生一个package.json的文件，这个文件用来描述项目的依赖
> - MIT ISC

### 初始化
>  - vue会抛出一个构造函数Vue,实例化vue,参数是一个对象
>  - let vm = new Vue({}) // vm-> view model
>  - options
>      + el -> not(html,body) -> querySelector
>      + data -> object -> 需要绑定的数据，里面的数据会被vm代理 -绑定到el中{{ msg }}表达式 vm.msg(test)
>  + 表达式 赋值取值三元
>  + 表单元素可以实现双向 -> 指令实现（v-model='data'）value被忽略掉
>  + 指令 dom上的行间属性 directive 都是以v-开头

### defineProperty
> - options
>    + value 值
>    + configurable  是否删除
>    + writable 是否可重新修改
>    + enumerable 是否可以枚举
>    + get() { //取obj的内部属性会触发 return 'getname'}
>    + set(val) {}
```javascript
		var obj = {};
		var obj1 = {};
		Object.defineProperty(obj, 'name', {
			get:function(){
				return obj1['name'];
			},
			set:function(val){
				obj1['name'] = val;
				def.value = val;
			},
		})
		def.value = obj.name;
		def.addEventListener('input', function(){
			obj.name = this.value;
			console.log(obj.name)
		},false)
		console.log(obj.name,2121)
```



### 基础指令
> v-text 
> v-html
> v-model
> v-once


### 数据响应的变化
>  vue会循环data中的数据（数据劫持） 依次的增加getter和setter
>  使用变量时 先要初始化，否则新加的属性不会导致页面刷新
>  vm.$set(obj,key,value); 此方法可以给对象添加响应式的数据变化
>   
>    
>    vm.arr[0] = 1; vm.arr.length-=2 //错误的写法
>    变异方法 pop push shift sort reserve splice
>    vm.arr = vm.arr.map/fiflter/some/every


### v-for
>  item,index of/in obj/arr


### event
> v-on:(@)click=""  -> methods
> 修饰符


### 简单todolist


------------

# 第二章

### 需要用到的依赖库
> npm install vue axios bootstrap

### checkbox
> - data.check  
> - v-model=check 
> - 必须带有value 
```javascript
    <input type="checkbox" v-model="check" value="1">1
    <input type="checkbox" v-model="check" value="2">2
    <input type="checkbox" v-model="check" value="3">3 <br>
    {{ check }}
```

### select
> disabled请选择
> value没写会取text值
> multiple
```javascript
    <select v-model="sele" multiple>
        <option value="" disabled>请选择</option>
        <option>1</option>
        <option value="22">2</option>
        <option value="33">3</option>
    </select>
    {{ sele }}
```

### radio
```javascript
    <input type="radio" v-model="radio" value="man">男
    <input type="radio" v-model="radio" value="women">女
    {{radio}}
```


### review
> v-text 解决行的闪烁问题
> v-cloak 解决块级的闪烁问题[v-cloak]{dis:none}


### vuetools.crx 调试插件

### 购物车
-  钩子函数 created 
   + 在数据被初始化后调用，this指向值得vm实例
   + 专门用来发送ajax请求的方法
- axios
- json
- promise+ajax
- v-bind 动态绑定数据 
- v-model.number.lazy
   + number 输入框的值编程数字
   + lazy 失去焦点的时候更新数据
- 过滤器{{ | }}
- filter:{}//自定义过滤器 
    + arg1-> 值 默认
    + arg2 -> params1 ->参数1
- computed


### v-if vs v-show
> if操作的是dom
> show才做的是style


### transition
> enter-acrive-class leave-active-calss
> name='aaaa'    
>    + aaaa-enter-class
>    + aaaa-enter-active
>    + aaaa-leave-active


-------

# 第三章
### 事件
> - 修饰符：
>    + .stop 阻止冒泡
>    + .capture 进行捕获
>    +prevent 阻止默认行为
>    + .once 触发一次
>    + .self 事件源只是自己的时候


### Vue.filter

### computed 计算属性
- 方法不会有缓存，computed 会根据依赖（归vue管理的属性，可以响应式变化的）的属性进行缓存
- 两部分组成get,set(不能只写set)


### watch和computed
> - computed默认调用get方法，需要有个reuturn,不支持异步
> - watch：{a(newval, oldwal){}} 支持异步
> - 计算值里面有三个 用computed


### 动态绑定样式
> template 无意义的标签，用来包裹元素用的  v-if能用v-show不能用
> v-bind简写（:）  动态绑定属性
### 绑定样式
> :class="{z:flag}"
> :class="[classname,classname]"
> :style="{}"
> :style="[style,{}]"


### 实现单页开发的方式
> 1. 浏览器自带的历史管理history(history.pushState('','','/dir'))
> 2. hash
>  开发hash 线上使用history方式


### todolists

### directives指令
> directives：{color(el,bindings){  el当前元素，bindings集合 }}

> watch: {
>    todos: {
>        handler(){},deep,true
>    }
> }


### localStorage



----------------


# 第四章
### 钩子函数之声明周期
> 根实例初始化会调用很多方法（钩子函数）
```javascript
    /*周期：
    *   beforeCreate created
    *   beforeMount mounted
    *   beforeUpdate updated
    *   beforeDestroy destroyed
    *
    * */
    new Vue({ // 根实例，初始化时会调用很多方法（钩子函数）
        data:{a:1},
        beforeCreate() {
            // 方法用不到
        },
        created() {
            //获取ajax,初始化操作
        },
        template:'',//如果template属性会用模板替换掉外部html；只要有此属性app中的内容就没有意义了，只能有一个根元素不能是文本节点
        beforeMount() {},
        mounted() {},//只是dom渲染完了，可以操作dom了
        beforeUpdate() {}, //一般用watch来替换掉
        updated() {},
        beforeDestroy() {}, //可以清除定时器或绑定事件
        destroyed() {}
    }).$mount('')// 编译元素
```


### 实例上的方法
> - ref>  $refs
>    + 如果dom不是v-for循环出来的，只能获取一个，通过v-for可以获取多个
>    + dom渲染是异步的  通过修改数组视图没有变化
>    + 如果数据变化后想获取真实dom中的内容，需要等待页面渲染完后再获取，所有dom操作最好在nextTick里面去操作
>    + 父调子方法
> - $.options 实力上的方法
> -   vm.$data vm上的数据
> -   $watch 监控
> -   $el 绑定的元素
> -   $set 后加的属性实现响应式变化
> -   $nextTick() 异步方法，等待渲染dom完成后来获取vm




### 组件
#### 分类
> 1. 页面组件
> 2. 将可复用部分抽离出来   基础组件

#### 好处
> - 提高开发效率
> - 方便复用使用
> - 便于协同开发
> - 更容易管理和维护

### vue中组件
> - 一个自定义标签 vue就会把他看成一个组件  vue可以给这些标签赋予一定义
> - 用法划分为
>    + 全局组件
>    + 局部组件


####  全局组件
> 可以声明在任何地方使用
> 摆放位置







###局部组件
> - 必须告诉这个组件属性谁
> - 使用方法三部曲
>     + 创建这个组件
>     + 注册这个组件
>     + 引入这个组件
> - 组件是独立的不能跨作用域
> - 组件嵌套


### 父传子
![Alt text](./1531907601430.png)



### 发布订阅模型


### 子传父 
> 单项数据流
> ![Alt text](./1531910034344.png)

### ref

### 修饰符.sync

### 模态框
![Alt text](./1531911169766.png)


### solt 插槽
![Alt text](./1531911821750.png)


###  组件
<component is="home">


### 缓存组件
<keep-alive></keep-alive>


------------

# 第五章

5-1.ref的作用
5-2.强调nextTick的用法
5-3.slot的用法
5-4.组件的循环
5-5.eventBus

### 基本路由

> 路由：访问不同的路径，返回不同的结果
> 多页面：spa (single page application)
> 前后端分离
> hash不支持seo history后端配合

#### 基本路由
 ![Alt text](./1531921324919.png)
 


#### 编程式导航
 
 ![Alt text](./1531959300990.png)
 
---------

![Alt text](./1531959573312.png)

------

![Alt text](./1531959898031.png)

-----

![Alt text](./1531960293254.png)

#### 路由嵌套

![Alt text](./1531960480983.png)


#### 路由参数变化

![Alt text](./1531961742268.png)
----
![Alt text](./1531961775160.png)

-----
![Alt text](./1531961844390.png)

-----

![Alt text](./1531961953301.png)

-----

![Alt text](./1531962143556.png)
----

![Alt text](./1531962196349.png)



### 安装需要的文件
![Alt text](./1531962249668.png)
![Alt text](./1531962266377.png)


-----

# 第六章

### 模块
> 介绍 对比  伤害

### 插件
![Alt text](./1532001011789.png)








# 参考
> http://www.zhufengpeixun.cn/docs/html/
