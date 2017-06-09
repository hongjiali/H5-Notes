# CAnvas Lines 
just to record my HTML5 notes 

做的项目中有一个比较特殊的矩形需要去绘制，感觉只能通过canvas来实现绘制了，于是在网上找了博客去学习，结果发现一个写的比较有意思的博客，
看的通俗易懂还比较轻松

[有需要的可以点这里去看看，里面的干货不少，值得学习](http://www.cnblogs.com/vajoy/p/3589717.html)

## H5 Canvans入门级别笔记

在此之前，我还比较懵懵懂懂的使用了chart.js来实现许多图表的实现。用过之后发现他们很多的时候都是通过一个<canvas></canvas> 标签来实现图表的展示。
可以说使用canvas的基本用法就是在html页面上定义一个canvas的标签，通过标签定义这块画布上面的内容。所以说，当你要决定绘制一个图片的时候你必须先给他
定义好一个你所需要的宽高 ， 然后再在上面绘制内容 ， 不然默认的canvas的大小是 **width : 300px height 100 px**。简单的例子看下面
```
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title>canvas标签的入门使用</title>
	</head>
	<style>
		html,body {
			margin: 0;
			padding: 0;
		}
		
		#canvas {
			width: 200px;
			height: 200px;
			background: #525252;
		}
	</style>

	<body>
		<canvas id="canvas"></canvas>
	</body>
  <script>
		var ctx = document.getElementById("canvas").getContext("2d");
  </script>
</html>
````
主要是通过 **document.getElementById("canvas").getContext("2d")** 这句代码来获取这块画布，然后，嘿嘿嘿，我们想干嘛就干嘛。

补充多说一句，2D 也很好理解，即平面二维 ， 我也不太了解canvas支持了3D没有，但是有CSS6可以实现所需要的3D炫彩的功能吧。
***
> Canvas Lines

什么都要从最简单学起来嘛，理所当然的，我们也必须要先了解最简单直观的————画线，就像把妹一样，我们不可能一下子就那个啥了对吧？（那个啥？我什么都不懂）

说道理由canvas来绘制lines ， 那么我们肯定接触到的两个最基本的方法：

**moveTo()**

**lineTo()**

看字面十分好理解，moveTo 是指我们绘制开始的坐标值。 lineTo则是指我们绘制结束之后的坐标值。 
需要注意的是**这里的坐标不是根据页面来定位坐标的，而是通过定义的画布canvas来相对坐标的起始位置**

代码演示一下下啦 (绘制了一条斜线，45°的那种)
````
var ctx = document.getElementById("canvas").getContext("2d");
ctx.moveTo(0, 150);//绘画开始的坐标位置
ctx.lineTo(150, 0);//绘画结束的坐标位置
````
既然如此，那么绘制一个五角星好像也不是那么难了
````
<!DOCTYPE html>
<html>

	<head>
		<meta charset="utf-8" />
		<title></title>
	</head>
	<style>
		html,
		body {
			margin: 0;
			padding: 0;
		}
		
		#canvas {
			width: 200px;
			height: 200px;
			background: #525252;
		}
	</style>

	<body>
		<canvas id="canvas"></canvas>
	</body>
	<script>
		var ctx = document.getElementById("canvas").getContext("2d");
		ctx.moveTo(0, 150);//绘画开始的坐标位置
		ctx.lineTo(150, 0);//绘画结束的坐标位置
		ctx.lineTo(300,150);
		ctx.lineTo(0,70);
		ctx.lineTo(300,70);
		ctx.lineTo(0,150);
		
		var grd = ctx.createLinearGradient(0,0,0,150);
		grd.addColorStop(0,"aqua");
		grd.addColorStop(0.5,"chartreuse");
		grd.addColorStop(1,"coral");
		ctx.strokeStyle = grd;
		ctx.stroke();
	</script>

</html>
````
我也不太知道为什么看起来感觉有点丑，可能人比较帅吧...这里的代码是给他设置会渐变的颜色，在我上面推荐的博客里讲的十分好，就这样吧
````
		var grd = ctx.createLinearGradient(0,0,0,150);
		grd.addColorStop(0,"aqua");
		grd.addColorStop(0.5,"chartreuse");
		grd.addColorStop(1,"coral");
		ctx.strokeStyle = grd;
````

