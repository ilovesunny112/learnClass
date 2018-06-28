# Date日期操作
> date日期类，它可以对时间进行处理
```
var time = new Date() //获取当前客户端本机时间（当前获取的时间不能作为重要的参考依据）
//获取的结果是一个日期格式的对象
```
> 方法
>  - time.getFullYear() 获四位整数年
>  - time.getMonth() 获取月（0～11代表1～12）
>  - time.getDate() 获取日
>  - time.getDay() 获取星期（0～6 周日到周六）
>  - time.getHours() 小时
>  - time.getMinutes() 分
>  - time.getSeconds() 秒
>  - time.getMilliseconds() 毫秒
>  - time.getTime() 获取当前日期距离 ‘1970-01-01 00:00:00’
>  - new Date('2017-10-22') //相当于把这个字符串转换成标准的时间对象模式（转换完成后，就可以调取上面我们讲的那些方法来）
>   + ie识别不来2017-10-22  可以写出2017/1/1 返回的结果是不一样的
>   + 3343 不能是字符串是数字类型