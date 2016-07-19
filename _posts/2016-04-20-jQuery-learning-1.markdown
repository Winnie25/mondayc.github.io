---
layout:     post
title:      "jQuery 学习笔记(一)"
subtitle:   ""
date:       2016-04-20 21:04:00
author:     "粥一"
header-img: "img/tag-bg.jpg"
catalog:		true
tags:
    - jQuery
    - 前端
    
---
作为一名设计汪，也需要懂点前端知识。HTML/CSS 是最基础的，为了更好的交互效果，JavaScript也需要学一点，jQuery 作为一种强大易用的js 框架，被小伙伴们广为推荐。

学习资源建议直接看W3school 的教程，若不能翻墙，也可以直接访问这个镜像网站： http://w3schools.bootcss.com/
##1. 基础定义 
基本句法：

```javascript
$(selector).action
```

理解：

- `$` 定义 jQuery
- `（selector）`用来访问 HTML 元素
- `action( )` 用来操作元素


######例子：
1.使用CSS选择器 

```javascript
$(this).hide() - 隐藏当前元素
$("p").hide() - 隐藏所有的<p> 标签元素
$(".test").hide() - 隐藏所有包含"test" 类的元素
$("#test").hide() - 隐藏所有ID为"test" 的元素
```

2.防止在文件加载完成之前jQuery 启动：

```
$(document).ready(function(){//jQuery ...});
```

## 2. 选择器
- 标签选择器 
- id选择器（#eg）
- class选择器（.eg）
- 其他：
    - `“ * ”` 选择全部 
    -  `“this”` 选择当前HTML 元素 
    -  ` $("p.intro")`选择所有p 标签下“intro” 类的元素 
    -  ` $("p:first")`选择第一个p 标签
    -  `$("ul li:first")`选择第一个ul 的第一个li  
    -  `$("ul li:first-child")`选择每一个ul 下的第一个li  
    -  `$("[href]")`选择所有有href 属性的元素 
    -  `$("a[target='_blank']")`选择所有a 标签下的target值为 _blank 的元素 
    -  `$("a[target！='_blank']")`选择所有a 标签下的target值不为 _blank 的元素 
    -  `$(":button")`选择所有`<button> `和` <input>`中`type= button`的 
    -  `$("tr:even")`选择所有偶数的tr  
    -  `$("odd:even")`选择所有奇数的 tr 


## 3. 事件

| 鼠标事件 | 键盘事件 | 表单事件 |	文件/窗口事件
| :--------:	 |		 :--------: 	| 	:----------:	 | 	:--: 	|
| click | keypress | submit | load
| dbclick | keydown | change |resize
| mouseenter | keyup | focus |scroll
| mouseleave | | blur |unload

例子: 

```javascript
$(document).ready(function(){ 
  $("p").click(function(){ 
    $(this).hide();
   });
// 鼠标点击 

  $("input").focus(function(){ 
    $(this).css("background-color", "#cccccc");
   }); 
  $("input").blur(function(){ 
    $(this).css("background-color", "#ffffff");
   });
// 表单获取/失去焦点 

  $("p").on({ 
    mouseenter: function(){ $(this).css("background-color", "lightgray"); }, 
    mouseleave: function(){ $(this).css("background-color", "lightblue"); }, 
    click: function(){ $(this).css("background-color", "yellow"); } 
   });
// 鼠标事件
});
```

##4. 遇到的其它小问题
经常在网页中看到这样虾面这样一段代码，其实是百度统计的东东。

```javascript
<script>
  var _hmt = _hmt || [];
  (function() {var hm =  document.createElement("script");
  hm.src = "//hm.baidu.com/hm.js?10701d9b4e040e37e58bee7e1ec1d252";
  var s = document.getElementsByTagName("script")[0];
  s.parentNode.insertBefore(hm, s);
})();
</script>
```