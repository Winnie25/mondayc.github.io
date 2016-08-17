---
layout:     post
title:      "Web 导航栏--长Tab 响应式设计"
subtitle:   ""
date:       2016-08-17 18:00:00
author:     "粥一"
catalog:	true
header-img: "img/tag-bg.jpg"
tags:
    - Web
    - Responsive/响应式
    - 交互设计
    
---
最近在思考有关Tab「极端」情况的设计。

先从Bootstrap 框架说起。Bootstrap 页面框架中的汉堡包导航方式无处不在，先看两个典型的例子-->>
![hamburger-1](/img/in-post/2016-08-17/01.gif)

![hamburger-2](/img/in-post/2016-08-17/02.gif)

以上导航的方式，一种是刚开始就以汉堡包折叠了起来，另一种则是当页面窄到某一数值，就将菜单折叠起来变成汉堡包。讲真，总有一种强行加特技的赶脚。好端端的导航，却要隐藏起来，徒增切换成本。隐藏起来页面的确会显得更简洁，但在切换时多了一步操作，用户更容易分心。

再放一个在小屏幕上展开的图：

![hamburger-滚动](/img/in-post/2016-08-17/03.gif)
一展开，全屏幕都是导航Tab，每个Tab 独占一行，大概是想要上天？

是病得治，Material Design 设计规范如是说-->>[Tabs - Components - Google design guidelines](https://material.google.com/components/tabs.html#tabs-usage). 现在越来越多的移动应用抛弃了汉堡包，取而代之的是垂直两端的Tab 导航栏。

![](/img/in-post/2016-08-17/01.png)

正如上图所示，没有那么宽，还要霸占一行的位置→_→，顺便把内容都挤下去了。于是我在思考，如果有较多的Tab，优先考虑横向排列，至于小屏溢出部分则可以左右切换。

用户往往更青睐于滑动、滚动的操作，而讨厌反复点击。幸运的是，[Angular Material](https://material.angularjs.org/) 就是这么做的！当标签位置超出窗口尺寸，便可以横向滑动进行切换。
![Angular Tabs demo](/img/in-post/2016-08-17/04.gif)

---
顺着这个思路，我做了个对应的二级Tab 导航demo：

![](/img/in-post/2016-08-17/05.gif)

为了节省屏幕空间，也可以省略两端的方向图标。codepen 链接[戳这里](http://codepen.io/fishfish/pen/vKbzAw).