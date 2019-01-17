---
title: CSS:绘制矩形、圆角矩形、圆形、椭圆形、三角形、弧
date: 2019-01-17 13:27:53
tags:
---
Demo: [https://codepen.io/xc454981894/pen/oJROBZ](https://codepen.io/xc454981894/pen/oJROBZ)
## 1.矩形  
绘制矩形应该是最简单的了，直接设置div的宽和高，填充颜色，效果就出来了。

## 2.圆角矩形
绘制圆角矩形也很简单，在1的基础上，在使用css3的border-radius，即可。

## 3.圆
根据圆的特性，在2的基础上，设置div的宽和高一直，为正方形，然后设置border-radius为50%即可。

## 4.椭圆
椭圆也很简单了，只需要在3的基础上，让div的宽和高不一致即可。为了更好看，建议宽设置为高的1.5倍。

## 5.三角形
三角形相对其他来说，就有点难了。这里我们要用到border-style属性在配合分别设置四个边的border的宽度来实现。最终效果见下面的代码。

## 6.弧
本质上是利用圆角来实现，现在需要把矩形的左上角的圆角绘制成弧形，那么把右边和底边border的宽度设成0px，让他们不可见，设置左上角圆角的半径，让其变大，看得明显些，其余的圆角半径全都设成0px，这样一个弧形就完成了。

## 7.平行四边形

平行四边形是在矩形的基础上运用了一个CSS3的transform属性。使用了变形效果。

## 8.六角星
六角星是使用了一个“:after”制作了另一个反方向的三角形，在定位层叠到一起，从而形成六角星，说白一点就是两个三角拼在一起变成了六角星。

## 9.五角星
五角星主要也是使用了CSS3的transform属性，并配合“:after”来使用。

## 10.心形、阴阳图、Point Burst、仿微信消息框、Pac-Man等

## Code
```
<!-- 绘制矩形 -->
<div class="rectangle"></div>
<!-- 绘制圆角矩形 -->
<div class='rounded-rectangle'></div>
<!-- 绘制圆 -->
<div class='circle'></div>
<!-- 绘制椭圆 -->
<div class='ellipse'></div>
<!-- 绘制三角形 -->
<div class='triangle'></div>
<!-- 绘制直线 -->
<div class='line'></div>
<!-- 绘制弧 -->
<div class='arc'></div>
<!-- 绘制平行四边形 -->
<div class='parallelogram'></div>
<!-- 绘制6角星 -->
<div class='star-six'></div>
<!-- 绘制五角星 -->
<div class='star-five'></div>
<!-- 绘制心形 -->
<div class='heart'></div>
<!-- 绘制pac-man -->
<div class='pac-man'></div>
<!-- 绘制微信消息框 -->
<div class='talkbubble'></div>
<!-- 绘制Point Burst -->
<div class='burst-12'></div><br/>
<!-- 绘制阴阳图 -->
<div class='yin-yang'></div>
```
```
.rectangle {
	width: 150px;
	height: 100px;
	background-color: orangered;
	margin-bottom: 5px;
}

.rounded-rectangle {
	width: 150px;
	height: 100px;
	background-color: orangered;
	border-radius: 10%;
	margin-bottom: 5px;
}

.circle {
	width: 100px;
	height: 100px;
	background-color: orangered;
	border-radius: 50%;
	margin-bottom: 5px;
}

.ellipse {
	width: 150px;
	height: 100px;
	background-color: orangered;
	border-radius: 50%;
	margin-bottom: 5px;
}

.triangle {
	width: 0px;
	height: 0px;
	border-style: solid;
	background-color: transparent;
	border-top-color: transparent;
	border-right-color: transparent;
	border-bottom-color: blue;
	border-left-color: transparent;
	border-top-width: 50px;
	border-bottom-width: 50px;
	border-left-width: 50px;
	border-right-width: 50px;
	margin-bottom: 5px;
}

.line {
	width: 100px;
	height: 3px;
	background-color: orangered;
	margin-bottom: 5px;
}

.arc {
	width: 100px;
	height: 100px;
	border-style: solid;
	border-top-width: 10px;
	border-bottom-width: 0px;
	border-left-width: 10px;
	border-right-width: 0px;
	border-top-color: blue;
	border-bottom-color: red;
	border-left-color: red;
	border-right-color: red;
	background-color: transparent;
	border-top-right-radius: 0px;
	border-top-left-radius: 100px;
	border-bottom-right-radius: 0px;
	border-bottom-left-radius: 0px;
}

.parallelogram {
	width: 150px;
	height: 100px;
	-webkit-transform: skew(20deg);
	-moz-transform: skew(20deg);
	-o-transform: skew(20deg);
	transform: skew(20deg);
	background: red;
	margin-top: 20px;
	margin-left: 20px;
}

.star-six {
	width: 0;
	height: 0;
	border-left: 50px solid transparent;
	border-right: 50px solid transparent;
	border-bottom: 100px solid red;
	position: relative;
}

.star-six:after {
	width: 0;
	height: 0;
	border-left: 50px solid transparent;
	border-right: 50px solid transparent;
	border-top: 100px solid red;
	position: absolute;
	content: "";
	top: 30px;
	left: -50px;
}

.star-five {
	margin: 50px 0;
	position: relative;
	display: block;
	color: red;
	width: 0px;
	height: 0px;
	border-right: 100px solid transparent;
	border-bottom: 70px solid red;
	border-left: 100px solid transparent;
	-moz-transform: rotate(35deg);
	-webkit-transform: rotate(35deg);
	-ms-transform: rotate(35deg);
	-o-transform: rotate(35deg);
	transform: rotate(35deg);
}

.star-five:before {
	border-bottom: 80px solid red;
	border-left: 30px solid transparent;
	border-right: 30px solid transparent;
	position: absolute;
	height: 0;
	width: 0;
	top: -45px;
	left: -65px;
	display: block;
	content: '';
	-webkit-transform: rotate(-35deg);
	-moz-transform: rotate(-35deg);
	-ms-transform: rotate(-35deg);
	-o-transform: rotate(-35deg);
	transform: rotate(-35deg);
}

.star-five:after {
	position: absolute;
	display: block;
	color: red;
	top: 3px;
	left: -105px;
	width: 0px;
	height: 0px;
	border-right: 100px solid transparent;
	border-bottom: 70px solid red;
	border-left: 100px solid transparent;
	-webkit-transform: rotate(-70deg);
	-moz-transform: rotate(-70deg);
	-ms-transform: rotate(-70deg);
	-o-transform: rotate(-70deg);
	transform: rotate(-70deg);
	content: '';
}

.heart {
	width: 160px;
	height: 200px;
	position: relative
}

.heart:before {
	content: " ";
	border: 0 solid transparent;
	-moz-border-radius: 100px;
	-webkit-border-radius: 100px;
	border-radius: 100px 100px 0 0;
	width: 80px;
	height: 120px;
	background: #669;
	-moz-transform: rotate(-45deg);
	-ms-transform: rotate(-45deg);
	-o-transform: rotate(-45deg);
	-webkit-transform: rotate(-45deg);
	position: absolute;
	left: 20px;
}

.heart:after {
	content: " ";
	border: 0 solid transparent;
	-moz-border-radius: 100px;
	-webkit-border-radius: 100px;
	border-radius: 100px 100px 0 0;
	width: 80px;
	height: 120px;
	background: #669;
	-moz-transform: rotate(45deg);
	-ms-transform: rotate(45deg);
	-o-transform: rotate(45deg);
	-webkit-transform: rotate(45deg);
	position: absolute;
	left: 48px;
	top: 0px;
}

.pac-man {
	width: 0px;
	height: 0px;
	border: 60px solid red;
	border-color: red transparent red red;
	-moz-border-radius: 60px;
	-webkit-border-radius: 60px;
	border-radius: 60px;
}

.talkbubble {
	width: 120px;
	height: 80px;
	background: red;
	position: relative;
	-moz-border-radius: 10px;
	-webkit-border-radius: 10px;
	border-radius: 10px;
	margin-left: 20px;
	margin-bottom: 20px;
}

.talkbubble:before {
	content: "";
	position: absolute;
	right: 100%;
	top: 26px;
	width: 0;
	height: 0;
	border-top: 13px solid transparent;
	border-right: 26px solid red;
	border-bottom: 13px solid transparent;
	margin-left: 20px;
	margin-bottom: 20px;
}

.burst-12 {
	background: red;
	width: 80px;
	height: 80px;
	position: relative;
	text-align: center;
	margin-left: 20px;
}

.burst-12:before,
.burst-12:after {
	content: "";
	position: absolute;
	top: 0;
	left: 0;
	height: 80px;
	width: 80px;
	background: red;
}

.burst-12:before {
	-webkit-transform: rotate(30deg);
	-moz-transform: rotate(30deg);
	-ms-transform: rotate(30deg);
	-o-transform: rotate(30deg);
	transform: rotate(30deg);
}

.burst-12:after {
	-webkit-transform: rotate(60deg);
	-moz-transform: rotate(60deg);
	-ms-transform: rotate(60deg);
	-o-transform: rotate(60deg);
	transform: rotate(60deg);
}

.yin-yang {
	width: 96px;
	height: 48px;
	background: #eee;
	border-color: red;
	border-style: solid;
	border-width: 2px 2px 50px 2px;
	border-radius: 100%;
	position: relative;
}

.yin-yang:before {
	content: "";
	position: absolute;
	top: 50%;
	left: 0;
	background: #eee;
	border: 18px solid red;
	border-radius: 100%;
	width: 12px;
	height: 12px;
}

.yin-yang:after {
	content: "";
	position: absolute;
	top: 50%;
	left: 50%;
	background: red;
	border: 18px solid #eee;
	border-radius: 100%;
	width: 12px;
	height: 12px;
}
```