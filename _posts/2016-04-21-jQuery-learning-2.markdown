---
layout:     post
title:      "jQuery 学习笔记(二)"
subtitle:   ""
date:       2016-04-21 21:04:00
author:     "粥一"
header-img: "img/tag-bg.jpg"
tags:
    - jQuery
    - 前端
    
---
##jQuery Effects
---
####隐藏和显示
1. hide / show 句法：

`$(selector).hide(speed,callback);`

`$(selector).show(speed,callback);`

例子：

``` javascript
$(document).ready(function(){ 
    $("button").click(function(){ 
      $("p").hide(1000); 
    });
});
```

2. toggle 句法：

`$(selector).toggle(speed,callback);`

通过一个button，可以在隐藏和显示之间切换例子：

```javascript
$(document).ready(function(){ 
    $("button").click(function(){ 
      $("p").toggle(2000); 
    });
});
```

####淡入淡出
fade 相关句法：

淡入 `$(selector).fadeIn(speed,callback);`

淡出 `$(selector).fadeOut(speed,callback);`

切换 `$(selector).fadeToggle(speed,callback);`

渐变到 `$(selector).fadeTo(speed,callback);`

例子：

```javascript
$(document).ready(function(){ 
  $("button").click(function(){ 
    $("#div1").fadeToggle(); 
    $("#div2").fadeToggle("slow"); 
    $("#div3").fadeToggle(3000); 
  });
});
```

####滑动
slide 相关句法：

`$(selector).slideDown(speed,callback);`

`$(selector).slideUp(speed,callback);`

`$(selector).slideToggle(speed,callback);`

例子：

```javascript
$(document).ready(function(){ 
  $("#flip").click(function(){ 
    $("#panel").slideToggle("slow"); 
  });
});
```

####动效
animation 句法：

`$(selector).animate({params},speed,callback);`

在`{params}`中可以同时设置多个参数，同时也可以使用相对值或预先定义过的属性词例子：

```javaScript
$(document).ready(function(){ 
  $("button").click(function(){ 
    $("div").animate({ 
      left: '250px', opacity: '0.5', height: '150px', width: '150px' 
    }); 
  });
});//同时设置多个参数

$(document).ready(function(){ 
  $("button").click(function(){ 
    $("div").animate({ 
      left: '250px', height: '+=150px', width: '+=150px' 
    }); 
  }); 
});//使用相对值
```

####返回值
通过返回值，可以在动效触发时同时加上其他的事件：例子：

```javascript
$("button").click(function(){ 
$("p").hide("slow", function(){ 
alert("The paragraph is now hidden"); 
});
});
```

#### jQuery 方法链

```javascript
$("#p1").css("color", "red").slideUp(2000).slideDown(2000);
//or
$("#p1").css("color", "red") .slideUp(2000) .slideDown(2000);
```

---
####其他问题
1. 在网页源代码首页经常会看见这样一段：

 ``` 
 <link rel="dns-prefetch" href="//code.jquery.com" /> <link rel="dns-prefetch" href="//fonts.googleapis.com" />  
 ``` 
 
 DNS Prefetch（预获取），是前端优化的一部分。  在前端优化中关于DNS主要是两部分： - 减小DNS请求次数 - 进行DNS预先获取> 默认情况下浏览器会对页面中和当前域名（正在浏览网页的域名）不在同一个域的域名进行预获取，并且缓存结果，这就是隐式的DNS Prefetch。如果想对页面中没有出现的域进行预获取，那么就要使用显示的DNS　Prefetch了，也就是使用link标签： `<link rel=”dns-prefetch” href=”http://api.twitter.com”/>` > DNS Prefetch应该尽量的放在网页的前面，推荐放在`<meta charset=”/>`后面。同时，也可以通过下面的标签禁止隐式的DNS Prefetch：`<meta http-equiv=”x-dns-prefetch-control” content=”off”> `