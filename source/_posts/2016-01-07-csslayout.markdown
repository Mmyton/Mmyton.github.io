---
layout: post
title: "前端开发之CSS布局"
date: 2016-01-07 16:05:23 +0800
comments: true
categories: [HTML,CSS]
---
>内容来源于网易微专业前端开发工程师课程与个人总结

###CSS布局
* 将元素以正确的大小摆放在正确的位置上
* 元素的摆放模式
<!--more-->

####[1. display]()
####语法
	display：none | inline | inline-block | block
####取值
	none：隐藏对象。与visibility属性的hidden值不同，其不为被隐藏的对象保留其物理空间
	inline：指定对象为内联元素。
	block：指定对象为块元素。
	nline-block：指定对象为内联块元素。（CSS2）
####兼容性
[如何实现浏览器兼容版的inline-block显示？](http://www.phpvar.com/archives/2211.html)
```css
	/*第一种解决方法：
	1.让块元素设置为内联对象（设置属性display:inline）
	2.然后触发块元素的 layout（如：zoom:1 等）*/
	div{
		display:inline-block;
		*display:inline;
		*zoom:1;
	}
	/*第二种解决方法：
	1.用display:inline-block属性触发块元素
	2.定义display:inline，让块元素呈递为内联对象
	注意：两个display 要先后放在两个CSS样式声明中才有效果，这是IE的一个经典bug，如果先定义了display:inline-block，然后再将display 设回inline或block，layout不会消失。*/
	div{
		display:inline-block;
	}
	div{
		*display:inline;
	}
```

####[2. position]()
####[top right bottom left]()
####语法
	top( right , left , bottom ): <length> | <percentage> | auto
	默认值：auto
####取值
	auto：无特殊定位，根据HTML定位规则在文档流中分配
	<length>：用长度值来定义距离顶部的偏移量。可以为负值。
	<percentage>：用百分比来定义距离顶部（右边，左边，底部）的偏移量。可以为负值。
####说明
	1.检索或设置对象与其最近一个定位的父对象顶部（右边，左边，底部）相关的位置。
	2.必须定义position属性值为absolute、relative或fixed，此取值方可生效。
####示例代码
```css
<div class="sample">sample</div>
.sample{background-color: pink;}
.sample{position: absolute;}
.sample{top: 30px;left: 30px;}
.sample{bottom: 30px;right: 30px;}	
```
**注意：**当同时设置了top，bottom：垂直方面撑开div;同时设置了right,left：水平方向撑开div
####[z-index]()
####语法
	z-index: auto | <integer>
	默认值：auto
####取值
	auto：遵从其父对象的定位
	<integer>：用整数值来定义堆叠级别。可以为负值。
####说明
	1.检索或设置对象的层叠顺序。
	2.并级的对象，此属性参数值越大，则被层叠在最上面。
	3.如两个对象的此属性具有同样的值，那么将依据它们在HTML文档中流的顺序层叠，写在后面的将会覆盖前面的。
	4.必须定义position属性值为absolute、relative或fixed，此取值方可生效。
####示例代码
```css
<div class="container0"><div class="sample0">sample 0</div></div>
<div class="container1"><div class="sample1">sample 1</div></div>
.sample0, .sample1{position: absolute;width: 200px;line-height: 150px;text-align: center;}
.sample0{background-color: #ff0;}
.sample1{background-color: pink;}
.sample1{top: 100px;left: 100px;}	
.sample0{z-index: 9;}
.container0, .container1{position: relative;}
.container1{z-index: 99;}
```
**注意：**两个div在其父元素没有设置z-index时，z-index大的覆盖z-index小的；若其父元素设置z-index，则无论这个两个div的z-index的大小，一律根据父元素的z-index来决定覆盖，大的覆盖小的。
####[static | relative | absolute | fixed]()
####语法
	position：static | relative | absolute | fixed
	默认值：static
####取值
	static：无特殊定位，对象遵循正常文档流。top，right，bottom，left等属性不会被应用。
	relative：对象仍在文档流，但将依据top，right，bottom，left等属性在正常文档流中偏移位置。
	参照物为元素本身，默认宽度仍未原来宽度。
	absolute：对象脱离正常文档流，使用top，right，bottom，left等属性进行绝对定位。而其层叠通过z-index属性定义。
	元素设置此定位后，默认宽度为内容宽度。参照物为第一个定位祖先/根元素
	fixed：对象脱离正常文档流，使用top，right，bottom，left等属性以窗口为参考点进行定位，当出现滚动条时，对象不会随着滚动。IE6及以下不支持此参数值。
	默认宽度为内容宽度，参照物为视窗。
####[常用的场景]()
relative：常用于改变元素z轴上的层级以及作为绝对定位的参照物。  
absolute：参看下面案例  
{% img /images/51.jpg 300 300%}
```css
<div class="is">
	<img src="att.jpg">
	<p class="title"><a href="#">老徐视线：北京潮女出门逛街不穿内衣</a></p>
	<div class="controls">
	   <span></span><span class="cur"></span><span></span><span></span><span></span>
	</div>
</div>
<style>
	.is{position: relative;width: 480px;}/*relative的作用*/
	.is img{display: block;}
	.is .title{position: absolute;bottom: 0;margin: 0;width: 100%;line-height: 45px;background-color: #000;opacity: 0.7;}/*absolute的作用*/
	.is .title a{margin-left: 20px;color: #fff;text-decoration: none;}
	.is .controls{position: absolute;bottom: 18px;right: 10px;line-height: 10px;}/*absolute的作用*/
	.is .controls span{display: inline-block;width: 10px;margin: auto 1px;height: 10px;border-radius: 10px;background-color: gray;}
	.is .controls span.cur{background-color: #fff;}
</style>
```
fixed：参看下面案例  
**固定顶栏**
```css
<div class="top">top bar</div>
<div class="main">main content area</div>
<style>
	body{margin: 0;line-height: 1.8;}
	.top{background-color: pink;color: #fff;}
	.main{height: 3000px;background-color: #eee;}
	body{padding-top: 50px;}/*因为top这个元素的高度为50px，设置这个避免内容被top遮盖*/
	.top{position: fixed;top: 0;width: 100%;height: 50px;}
</style>
```
**遮罩**
```css
<div class="mask"></div>
<div class="content">content area</div>
<style>
	.mask{position: fixed;top: 0;left: 0;z-index: 999;width: 100%;height: 100%;background-color: #000;opacity: 0.3;}
	.content{height: 3000px;}
</style>
```
**三行自适应布局**
```
<div class="head">head</div>
<div class="body">
	<div class="content">content area</div>
</div>
<div class="foot">foot</div>
<style>
	.head{position: absolute;top: 0;left: 0;width: 100%;height: 100px;background-color: #ccc;}
	.body{position: absolute;top: 100px;left: 0;bottom: 100px;right: 0;overflow: auto;}
	.content{height: 2000px;}
	.foot{position: absolute;bottom: 0;left: 0;width: 100%;height: 100px;background-color: #ccc;}
</style>
```
####[3. float]()
####语法
	float：none | left | right
	默认值：	none
####取值
	none：设置对象不浮动
	left：设置对象浮在左边
	right：设置对象浮在右边
####说明
	1.该属性的值指出了对象是否及如何浮动。
	2.当该属性不等于none引起对象浮动时，对象将被视作块对象，即display属性等于block。也就是说，浮动对象的display特性将被忽略。
	3.该属性可以被应用在非绝对定位的任何元素上。
	4.设置浮动属性后，元素宽度为内容宽度。
	5.float的元素在同一文档流中
####float元素半脱离文档流
```css
<body>
	<div class="sample">float: left;</div>
	<div class="sb">A float is a box that is shifted to the left or right on the current line. The most interesting characteristic of a float (or "floated" or "floating" box) is that content may flow along its side (or be prohibited from doing so by the 'clear' property). </div>
</body>
<style>
	body{width: 300px;padding: 5px;line-height: 1.6;border: 1px dashed blue;}
	.sample{height: 100px;margin-right: 5px;padding: 0 5px;line-height: 100px;background-color: pink}
	.sb{background-color: #eee;}
	.sb{outline: 1px dashed red;}
	.sample{float: left;}
</style>
```
**注意：**float元素：对元素脱离文档流；对内容在文档流。  
{% img /images/float_1.jpg %}  
####清除浮动
**第一种方法：空元素**  
```css
<div class="parent">
	<div class="sample">float: left</div><div class="sample">float: left</div><div class="sample">float: left</div>
	<br class="cb">
</div>
<style>
	.sample{float: left;width: 100px;line-height: 100px;text-align: center;background-color: pink;}
	.parent{padding: 5px 0;margin-bottom: 10px;outline: 1px dashed blue;}
	.sample{margin: auto 5px;}
	.sample{float: left;}
	.cb{clear: both;height: 0;overflow: hidden;visibility: hidden;}
</style>

```
{% img /images/float_2.jpg 350 350 %} {% img /images/float_3.jpg 350 350 %}  
**第二种方法：clearfix**
```css
<div>
	<div class="sb clearfix">
		<div class="sample">float: left;</div>
		第12届ChinaJoy动漫游戏展7月31日在上海新国际博览中心开幕，到处是站台表演的帅哥美女。
	</div>
	<div class="sb">
		有些游戏商为了吸引人气，还请来了著名的演员、模特前来助阵。以下是一批漂亮的Show Girl现场照片。
	</div>
</div>
<style>
.sample{float: left;width: 100px;line-height: 100px;text-align: center;background-color: pink;}
.sb{padding: 5px 0;margin-bottom: 10px;outline: 1px dashed blue;}
.sample{margin: auto 5px;}
.sample{float: left;}
.clearfix:after{content:'.';display: block;clear: both;height: 0;overflow: hidden;visibility: hidden;}
</style>
```
{% img /images/float_4.jpg 350 350 %} {% img /images/float_5.jpg 350 350 %}



