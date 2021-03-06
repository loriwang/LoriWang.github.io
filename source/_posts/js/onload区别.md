---
title: window.onload与$(document).ready()区别
date: 2017-04-24 22:02
categories: 'jquery'
type: 'jquery'
---
jQuery中`$(document).ready()`的作用类似于传统JavaScript中的`window.onload`方法，不过与`window.onload`方法还是有区别的。<br>
## 1.简化写法 
window.onload没有简化写法 <br>
$(document).ready(function(){})可以简写成$(function(){});
```javascript
$(function() {
  // do something
})
````
## 2.编写个数不同 
window.onload不能同时编写多个，如果有多个window.onload方法，只会执行一个 <br>
```javascript
window.onload=function() {
  alert(1)
};
window.onload=function() {
  alert(2)
}
````
结果只输出`2`<br><br>

$(document).ready()可以同时编写多个，并且都可以得到执行 
```javascript
$(function(){
    alert('hello world1')
});
$(function(){
    alert('hello world2')
});
````
两次都能正常输出
## 3.执行时间 
window.onload必须等到页面内包括图片的所有元素加载完毕后才能执行。 <br>
$(document).ready()是DOM结构绘制完毕后就执行，不必等到加载完毕。

## 4.注意项
由于在 $(document).ready() 方法内注册的事件，只要 DOM 就绪就会被执行，因此可能此时元素的关联文件未下载完。例如与图片有关的 html 下载完毕，并且已经解析为 DOM 树了，但很有可能图片还没有加载完毕，所以例如图片的高度和宽度这样的属性此时不一定有效。<br>
要解决这个问题，可以使用 Jquery 中另一个关于页面加载的方法 ---load() 方法。 Load() 方法会在元素的 onload 事件中绑定一个处理函数。如果处理函数绑定给 window 对象，则会在所有内容 ( 包括窗口、框架、对象和图像等 ) 加载完毕后触发，如果处理函数绑定在元素上，则会在元素的内容加载完毕后触发。 <br>
```javascript
// jquery 中
$(window).load(function (){ 
       // 编写代码  
});
// 等价于 JavaScript 中的以下代码 
Window.onload = function (){ 
     // 编写代码 
}
````

<p align=right>---by  lori.Wang</p>