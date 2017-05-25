# H5-Chart.js-Notes
记录一下chart.js的使用难点（很悲伤的故事）</p>
因为现在使用的chart.js是最新版本的，文档也基本都是英文的（中文的太不全面了），然后出现各种问题整个人都很难过。

# chart.js 的代码基本结构组成和基本使用
****

## chart.js的优缺点体验
为什么项目用到了chart.js ,原因很简单，总结起来无非两个 ： 
* 1 轻量级 （相对EChart等等的确是真的非常轻便，但是实现起来相对就更难啊）
* 2 免费（- -，这也是一个很重要的原因好吧）

## chart.js 的基本使用 
怎么使用chart.js , 其实chart.js的使用结构非常简单，我们实现一个图标通常有四步 ： 

### * 1 在html里面定义一个canvas标签，他只能通过外层的div来控制他的大小不能自定义canvas的大小
```
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
	</head>
	<body>
	<div style="width:75%;">
		<canvas id="canvas"></canvas>
	</div>
  </body>
 </head>
</html>
```


### * 2  定义这个图表整体数据显示的样式，通过是给他定义一个 ***datas***</p>
```
var datas = {
    labels: ["","",...],    //定义的是X轴显示的label
    datasets:[{   // 也是一个数组，如果有多个柱形或多个线性或者多个柱形多个线性结合,  那么一个｛｝就相当于一个图表对象，每个图表的对象可以给他设置相关属性，请看文档
      data:[...],   // 一个数组，就是图表上的各种数据
      label: "...",   // 图例设置
      id : "y-axis-1", //可以是字符串也可以是数字，对应下面option的Y轴或X轴的设置
      //定义的属性文档都有，详细的自己看，比如说有定义颜色的color ， 有定义线性图点的大小线的粗细等等
      ...，
      ...，
      ...},
    {},
    {},
    ...],
}
```

### * 3 定义这个图表的选项设置 （options），通常包括有：
 ###### 1 title 标题设置
 ###### 2 legend 图例，实际上就是点击这个按钮下面的数据显示或消失，
 ###### 3 tooltip 
 ###### 4 hover 设置悬浮在图表上显示的数据的提示数据的框块
 ###### 5 element 这个是一个重点坑，用来把在一个图表中添加数据文字图片等需要用到的
 ###### 6 animation 动画设置
```
var options = {
    responsive : boolean,   //true 则可以根据屏幕适配大小 ， false则是固定大小
    title :{
    
    },
    scales : {
      xAxes :[
          {
            display: boolean, //X轴相关数据的显示
            ticks:{   //X轴刻度表的显示的设置，属性看相关文档
                  
             }，
            title: {    //X轴标题的设置，属性看相关文档
              
             },
            girdLines:{  //对网格的设置，属性看相关文档
            
             }，
          },
          {},
          {},...
        ],
      yAxes :[ //同X轴差不多的设置
          {},
          {},
          {},
          ...
      ]},
   tooptip:{
   
   }, 
   legend:{
    
   },
}
```
### * 4 实现通过canvas的id来绘制图表
```
    var ctx = document.getElementById("canvas").getContext("2d");
    window.myLine = new Chart(ctx, {
        datas,
        options,
    });
```
##### 想了解更多请看我的Demo 或者是 查阅chary.js的官方文档
#### [chart.js 文档链接](http://www.chartjs.org/docs/#scales-common-configuration)
#### [chart.js github地址](https://github.com/chartjs/Chart.js)
