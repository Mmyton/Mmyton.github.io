---
layout: post
title: "前端开发之CSS变形"
date: 2016-01-10 12:23:20 +0800
comments: true
categories: [CSS]
---
>内容来源于网易微专业前端开发工程师课程与个人总结

CSS3变形可以实现对文字或图像的旋转、缩放、倾斜、移动，分别对应Transform属性中的rotate、scale、skew、translate这个四个方法。四种变形的不同组合，就会产生不同的效果。  
**注意：**这个四个方法使用顺序的不同，产生的效果是不一样。<!--more-->

####[transform()]()
####语法
	transform : none | <transform-function> +
	<transform-function> : rotate() scale() skew() translate()
	transform : translate(50%) rotate(45deg)
	transform : rotate(45deg) translate(50%) 
{% img /images/transform_1.png 300px 300px%} {% img /images/transform_2.png 300px 300px%}  
**注意：**改变transform属性值的顺序产生的图像是不一样的。
####[rotate()]()
####语法
	rotate(<angle>)
	transform:rotate(45deg);
	transform:rotate(-60deg);
CSS中使用rotate方法来实现对元素的旋转，在参数中加入角度值。  
**注意：**旋转方式为顺时针旋转。
####demo
```css
<body>
	<div class="m-demo m-demo-1">
	    <pre>C</pre>
	</div>
</body>
<style type="text/css">
	.m-demo-1 pre{transform:rotate(45deg);font-size:200px;line-height:300px;text-align:center;}
</style>
```
{% img /images/rotate.png 300px 300px%}
####[translate()]()	
####语法
	translate(<translation-value> [,<translation-value>]?)
	translateX(<translation-value>)
	translateY	(<translation-value>)
指定对象的2D translation（2D平移）。第一个参数对应X轴，第二个参数对应Y轴。如果第二个参数未提供，则默认值为0。
####demo
```css
<body>
	<div class="m-demo m-demo-1">
	    <pre></pre>
	</div>
</body>
<style type="text/css">
	.m-demo-1 pre{transform:translate(50px);}/*1*/
	.m-demo-1 pre{transform:translate(50px,20%);}/*2*/
	.m-demo-1 pre{transform:translateX(-50px);}/*3*/
	.m-demo-1 pre{transform:translateY(20%);}/*4*/
</style>
```
{% img /images/translate_1.png 150px 150px%} {% img /images/translate_2.png 150px 150px%} {% img /images/translate_3.png 150px 150px%} {% img /images/translate_4.png 150px 150px%}
####[scale()]()	
####语法
	scale(<number> [,<number>]?)
	scaleX(<number>)
	scaleY(<number>)
指定对象的2D scale（2D缩放）。第一个参数对应X轴，第二个参数对应Y轴。  
**注意：**如果第二个参数未提供，则默认取第一个参数的值。
####demo
```css
<body>
	<div class="m-demo m-demo-1">
	    <pre></pre>
	</div>
</body>
<style type="text/css">
	.m-demo-1 pre{transform:scale(1.2);}
	.m-demo-1 pre{transform:scale(1,1.2);}
	.m-demo-1 pre{transform:scaleX(1.2);}
	.m-demo-1 pre{transform:scaleY(1.2);}
</style>
```
{% img /images/scale_1.png 150px 150px%} {% img /images/scale_2.png 150px 150px%} {% img /images/scale_3.png 150px 150px%} {% img /images/scale_2.png 150px 150px%}
####[skew()]()
####语法
	skew(<angle> [,<angle>]?)
	skewX(<angle>)
	skewY(<angle>)
指定对象skew transformation（斜切扭曲）。第一个参数对应X轴，第二个参数对应Y轴。  
**注意：**如果第二个参数未提供，则默认值为0
####demo
```css
<body>
	<div class="m-demo m-demo-1">
	    <pre></pre>
	</div>
</body>
<style type="text/css">
	.m-demo-1 pre{transform:skew(30deg);}/*1*/
	.m-demo-1 pre{transform:skew(30deg,30deg);}/*2*/
	.m-demo-1 pre{transform:skewX(30deg);}/*3*/
	.m-demo-1 pre{transform:skewY(30deg);}/*4*/
</style>
```
{% img /images/skew_1.png 150px 150px%} {% img /images/skew_2.png 150px 150px%} {% img /images/skew_1.png 150px 150px%} {% img /images/skew_3.png 150px 150px%}
####[transform-origin()]()
####语法
	[ <percentage> | <length> | left | center① | right ] [ <percentage> | <length> | top | center② | bottom ]?
	默认值：50% 50%，效果等同于center center
	适用于：所有块级元素及某些内联元素
	继承性：无
####取值
	<percentage>：用百分比指定坐标值。可以为负值。
	<length>：用长度值指定坐标值。可以为负值。
	left：指定原点的横坐标为left
	center①：指定原点的横坐标为center
	right：指定原点的横坐标为right
	top：指定原点的纵坐标为top
	center②：指定原点的纵坐标为center
	bottom：指定原点的纵坐标为bottom
####说明
	1. 设置或检索对象以某个原点进行转换。
	2. 该属性提供2个参数值。
	3. 如果提供两个，第一个用于横坐标，第二个用于纵坐标。
	4. 如果只提供一个，该值将用于横坐标；纵坐标将默认为50%。
####demo
```css
<body>
	<div class="m-demo m-demo-1">
	    <pre></pre>
	</div>
</body>
<style type="text/css">
	.m-demo-1 pre{transform:rotate(45deg);transform-origin:0 0;}
</style>
```
{% img /images/transform-origin.png 300px 300px%}
####[perspective]()
####语法
	perspective:none | <length>
####demo
```css
<body>
	<div class="m-demo m-demo-1">
	    <pre></pre>
	</div>
</body>
<style type="text/css">
	.m-demo-1 pre{transform:rotateY(45deg);}
	.m-demo-1{perspective:2000px;}
</style>
```
{% img /images/perspective.png 300px 300px %}
####[perspective-origin()]()
####语法
	[ <percentage> | <length> | left | center① | right ] [ <percentage> | <length> | top | center② | bottom ]?
	默认值：50% 50%，效果等同于center center
####取值
	<percentage>：用百分比指定坐标值。可以为负值。
	<length>：用长度值指定坐标值。可以为负值。
	left：指定透视点的横坐标为left
	center①：指定透视点的横坐标为center
	right：指定透视点的横坐标为right
	top：指定透视点的纵坐标为top
	center②：指定透视点的纵坐标为center
	bottom：指定透视点的纵坐标为bottom
####说明
	1. 该属性提供2个参数值。
	2. 如果提供两个，第一个用于横坐标，第二个用于纵坐标。
	3. 如果只提供一个，该值将用于横坐标；纵坐标将默认为50%。
####demo
```css
<body>
	<div class="m-demo m-demo-1">
	    <pre></pre>
	</div>
</body>
<style type="text/css">
	.m-demo-1{perspective:2000px;perspective-origin:0 1000px;}
	.m-demo-1 pre{transform:rotateY(45deg);}
</style>
```
{% img /images/perspective-origin.png 300px 300px%}

####[translate3d()]()
####语法
	translate3d(<translation-value>,<translation-value>,<lenght>)
	translateX(<translation-value>)
	translateY(<translation-value>)
	translateZ(<lenght>)
####demo
```css
<body>
	<div class="m-demo m-demo-1">
	    <pre></pre>
	</div>
</body>
<style type="text/css">
	.m-demo{perspective:2000px;}
	.m-demo-1 pre{transform:translate3d(10px,20%,200px);}
</style>
```
{% img /images/translate3d_1.png 300px 300px%}
####[scale3d()]()
####语法
	scale3d(<number>,<number>,<number>)
	scaleX(<number>)
	scaleY(<number>)
	scaleZ(<number>)
####demo
```css
<body>
	<div class="m-demo m-demo-1">
	    <pre></pre>
	</div>
</body>
<style type="text/css">
	.m-demo{perspective:2000px;}
	.m-demo-1 pre{transform:scale3d(1.2,1.2,1);}
</style>
```
{% img /images/scale3d_1.png 300px 300px%}
####[rotate3d()]()
####语法
	rotate3d(<number>,<number>,<number>,<angle>)
	rotateX(<angle>)
	rotateY(<angle>)
	rotateZ(<angle>)
####demo
```css
<body>
	<div class="m-demo m-demo-1">
	    <pre></pre>
	</div>
</body>
<style type="text/css">
	.m-demo{perspective:2000px;}
	.m-demo-1 pre{transform:rotate3d(0,0,1,45deg);}
	.m-demo-1 pre{transform:rotate3d(0,1,0,45deg);}
	.m-demo-1 pre{transform:rotate3d(0,0,1,45deg);}
	.m-demo-1 pre{transform:rotate3d(1,1,1,45deg);}
</style>
```
{% img /images/rotate3d_1.png 300px 300px%}
####[transform-style]()
####语法
	transform-style : flat | preserve-3d
	flat : 扁平效果
	preserve-3d : 保留3d效果
####demo
```css
<body>
	<div class="m-demo m-demo-1">
	    <pre>
	    	<pre></pre>
	    </pre>
	</div>
</body>
<style type="text/css">
	.m-demo{perspective:2000px;}
	.m-demo-1>pre{transform:rotateX(45deg);transform-style:preserve-3d;}/*内部保留3d效果需要设置preserve-3d*/
	.m-demo-1>pre>pre{transform:rotateY(45deg);}
</style>
```
{% img /images/preserver_1.png 300px 300px%} &nbsp;to&nbsp; {% img /images/preserver.png 300px 300px%}
####[backface-visibility]()
####语法
	backface-visibility : visible | hidden
	背面设置可见或者不可见
####demo
```css
<body>
    <div class="m-demo m-demo-2">
        <div>
            <pre>C</pre>
            <pre>E</pre>
        </div>
    </div>
    <div class="m-demo m-demo-2 m-demo-backface">
        <div>
            <pre>C</pre>
            <pre>E</pre>
        </div>
    </div>
</body>
<style type="text/css">
    .m-demo{perspective:2000px;}
    .m-demo > div{transform-style:preserve-3d;position:absolute;top:0;left:0;width:100%;height:100%;}
    .m-demo pre{font-size:200px;text-align:center;}
    .m-demo pre:first-child{transform:rotateY(180deg) translateZ(1px);}
    .m-demo pre:last-child{transform:none;}
    .m-demo-2 > div{transform:rotateY(45deg);}
    .m-demo-backface pre{backface-visibility:hidden;}
</style>
```
{% img /images/backface_1.png 300px 300px%} &nbsp;to&nbsp; {% img /images/backface_2.png 300px 300px%}