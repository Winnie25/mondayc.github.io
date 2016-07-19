---
layout:     post
title:      "记录第一次写网页的心路历程"
subtitle:   ""
date:       2016-05-07 21:00:00
author:     "粥一"
header-img: "img/post-rh.jpg"
tags:
    - Web
    - 小结
    - 前端
    
---
##网页主要内容
UX Team 主页，访问对象为公司内部同事。主页主要用来展示三个内容入口：Project，Design， Resource。
页面元素这么少，写起来也应该很简单。但对于一只没写过完整Web 页面的设计汪来说，还是有点额头冒汗。
##使用到的工具
Sketch＋Sublime Text3。两个应用安装包加起来不到50M ¬_¬

在预览和调整时，主要是 Chrome 浏览器，后来也开始用Github 来控制版本信息和方便在线预览。
##步骤

就三个按钮嘛，不用画图，引用一下font icon 就直接搞定咯。好像有点单调，那就再加个hover 后blingbling 的动效，然后……就完成啦。

是的……你没有看错，这是Version 0.1（看了下图不取关的都是真爱粉 0.0）

![Version 0.1](http://upload-images.jianshu.io/upload_images/674139-0192354a449abfa7.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
－“是不是有点偷懒……？”
－“嗯，很有自知之明。”
－“嘿嘿……我只是尝试一下这样的效果……”

默默滚回位置上，打开Sketch 开始画图…

用Shadowman 的红＋黑为主要颜色，背景使用icon 填充，中间的三个色块分别对应 Project，Design， Resource。

![Version 0.2](http://upload-images.jianshu.io/upload_images/674139-1c3664b2dee006bf.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

这厚重的颜色，终于有人看不下去了……于是就被改成了下面的Version 0.3 ：

总体居中对齐，颜色改为了红＋白，但看起来还是不太顺眼：
- 「Visit UX Mojo」放在正中，就像一些页面的「Download」按钮一样，被视为了重点，但重点应该是中间三个入口呀。嗯，应该放到右上角这个相对最不容易被注意到的角落去…
- content 高低不齐，footer 背景高低不齐， 页面背景也是花花的，看起来有些凌乱；
- footer 文字居中对齐，logo 却偏到最左侧，莫名其妙；
- 标题＋段落＋button 占据了接近300px（不是响应式页面），整个页面高度接近1000px了……在绝大多数电脑屏幕上都不能完整显示。

![Version 0.3](http://upload-images.jianshu.io/upload_images/674139-81d86288183e10b1.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

改改改，于是有了当前版本：
- 标题方面：
  - 修改长标题，使视觉上更简洁，同时将「PnT DevOps」作为子标题，毕竟这是UX TEAM 的主页…
  -  在标题和小标题处适当使用大写，视觉上更为整齐；
- 按钮：
  -  「Mojo」按钮放到右上角，突出中间三个入口；
  - 中间三幅图水平且垂直居中，对齐到一条直线上；
-  header 和 footer：
  -  分别在屏幕中间700像素范围内两端对齐。


![Version 0.5](http://upload-images.jianshu.io/upload_images/674139-29387fadd3be4276.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

嗯，终于改好啦！考虑到图片大小问题，又在tinypng 上压缩了一下图片，然后打包上传Github。于是我满心欢喜地把[demo](http://mondayc.github.io/test01/)  链接发给了小伙伴们。

咦……元素全部错位了，字体不对，大小也错了，页面也会水土不服嘛。原来小伙伴是用Firefox打开的，而我一直是用Chrome 来调试页面的，看来还得来调整一下元素写法，解决浏览器兼容的问题。

---
## 问题的解决

####1. 在CSS 中，样式的覆盖规则:
- 外部样式< 内部样式< 内联样式
- 由于继承而发生样式冲突时，最近祖先获胜
- 继承的样式和直接指定的样式冲突时，直接指定的样式获胜
- 直接指定的样式发生冲突时，样式权值高者获胜

|CSS选择器| 权值 |
|:-------------:|:-------------:|
|标签选择器|1
|类选择器|10
|ID选择器|100
|内联样式|1000
|伪元素(:first-child等)|1
|伪类(:link等)|10

- 当权值相等时，后出现的样式表设置要优于先出现的样式表设置
- !important的样式属性不被覆盖

>参考：
[CSS 样式覆盖规则](http://bbs.csdn.net/topics/390403416)
[如何和何时使用CSS 的 !important](http://www.w3cplus.com/css/the-important-css-declaration-how-and-when-to-use-it.html)

####2. 有关jQuery 加载方式

有时会看到在引入jQuery 时有这样一段代码：

```
<script src="http://libs.useso.com/js/jquery/2.1.1/jquery.min.js" type="text/javascript"></script>
<script>window.jQuery || document.write('<script src="jquery-2.1.1.min.js"><\/script>')</script>
```

这样的写的话，就可以实现考第一种方式jQuery 未能加载成功的情况下，自动加载本地jQuery 文件。
>参考：
[加载jQuery 的正确方式](https://blog.netsh.org/posts/how-to-load-jquery_1645.netsh.html)

####3. display: block 、inline、 inline-block 的作用
`display: block` 将元素显示为块级元素。对`<div>`这样的块元素，display 属性默认值为block，没必要再定义（除非之前对display 属性进行过修改 ，如：`display:hidden;`）；常用于`<a> <span>`这两个标签，因为对于非块级元素，定义width height 等和长宽相关的CSS 属性时会发现完全不生效。

栗子：

```
<li><a href="#">超链接</a></li>
<!--默认，鼠标移动到文字区域有效-->

<li><a href="#"  style:{width:100px;height:100px; display:block; color:red; text-decoration:none;} >超链接</a></li>
<!--鼠标移动到100*100范围内都有效-->
```

`display: inline` 内联元素，和其他元素都在同一行；高、行高、顶和底边距不可改变，宽度就是文字或者图片内容的宽度，不可自定义。

`display: inline-block`内联对象，并可以控制对象内容的高、宽等。
>参考：
[display:inline、block、inline-block的区别](http://www.cnblogs.com/jdonson/archive/2011/06/10/2077932.html)

####4. 不同浏览器兼容性问题
这次我主要考虑 Chrome、Firefox 和Safari 三种浏览器（IE 浏览器比较麻烦，所幸公司里没同事用IE…）。

页面里面出现的问题：
**1 . 引入的字体无法在Firefox 上正常显示**
－ “你好大的胆子…只引一种格式的字体文件”
－ “我去加上…”

对于字体格式，不同浏览器支持情况都不同：

|字体格式|支持的浏览器|
|:--:|:--:|
|.ttf|IE9+, Firefox3.5+, Chrome4+, Safari3+, Opera10+, iOS Mobile Safari4.2+
|.otf|Firefox3.5+, Chrome4+, Safari3.1+, Opera10+,  iOS Mobile Safari4.2+
|.woff|(web 字体最佳格式) IE9+, Firefox3.5+, Chrome6+, Safari3.6+, Opera11.1+
|.eot|IE4+
|.svg|Chrome4+, Safari3.1+, Opera10.0+, iOS Mobile Safari3.2+

我只引用了 .ttf 格式的字体，这三种浏览器应该是支持的呀，但在Firefox 上还是出了问题，于是乖乖加上其他几种格式字体……

```
@font-face{
font-family: 'overpass';
src:url(fonts/Overpass.ttf) format("truetype");/* 最初我只写了这一种 */
src:url(fonts/Overpass.eot) format("eot");/* IE4＋ */
src:url(fonts/Overpass.svg) format("svg");/* iOS Safari 3.2+ */
src:url(fonts/Overpass.woff) format("woff");/* Modern Browser */
}
```

**2 . 元素位置出现偏差**
Firefox 和Safari 中的字体明显小了几号，后来发现是em 单位的问题。

em单位有如下特点：
1 . em的值并不是固定的;
2 . em会继承父级元素的字体大小（嗯，问题就出在这）。栗子：

```
	#content{
	font-size = 1.2em;
	}
	#p{
	font-size = 1em;
	}/* 这里p 的字体大小就是 1.2*16px 啦 */
```

这次如果再加上 IE 浏览器旧版本的兼容性问题，一定会头大0.0
>参考：
[在线字体格式转换工具](https://onlinefontconverter.com/)

---
此外，分享一下最近发现的几个自认为有趣的网站：
[Free online IDE and Terminal](http://www.tutorialspoint.com/codingground.htm)
[马克飞象（Markdown for Evernote）](https://maxiang.io/)

##小结

边学边写，大约花了一周的时间。这个页面不需要任何复杂的框架，也不需要引入JavaScript 和jQuery ，但心境却和之前看页面源代码、临摹时完全不一样了，毕竟这次是在没有参照的情况下，自己来设计和实现。同时我也感觉流程和想象中的不太一样…看着不对、或者不会写了，就回去改设计稿（嘘）。这个问题，还是慢慢用技术来改变吧…

善用Google，解决问题的同时也可以发现不少充满小惊喜的资源；第一次使用Github ，现在真后悔没有早点亲身体验这么实用的工具；发现了不少干货满满的前端技术博客，还发现了同学院校友一枚2333。

不懂前端的产品不是好设计师，哈哈。期待做下一项产品。