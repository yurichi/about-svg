整理整理……SVG
============

svg是基于xml的语言，主要用于绘制二维图像。


为什么要选择SVG？主要有这几方面的原因：
SVG 是可伸缩的矢量图形，在浏览器中改变尺寸，其图形质量不会有所损失。
相比其它位图，SVG图像文件更小，可压缩性更强。
SVG 可以被记事本等阅读器、搜索引擎访问。
SVG 图像中的文本是可选的，同时也是可复制的。
SVG 图像可以与DOM，CSS和JavaScript交互。
SVG 可以制作成整体或局部动画。

```
<svg width="300" height="200" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"> 
  <rect width="100%" height="100%" fill="green" /> 
</svg>
```
将SVG作为图像导入
```
<img src="example.svg" alt="My SVG example">
```
或

```
.my-image {
  background: url("example.png"); /* fallback */ 
  background-image: url("example.svg"); 
}

```
使用Object 或 iframe导入SVG图像

```
<object type="image/svg+xml" data="example.svg" class="example">
   My Example SVG <!-- fallback --> 
</object>

```

```
.example { 
  display: block; 
  margin: 5em auto; 
  border-radius: 10px;
 }
 
```
或

```
<iframe src="example.svg" class="example"></iframe>

```
将SVG作为Data URI导入
可以把SVG转成一个data URI,把它作为data导入。可以通过在线或离线的工具来进行转换（这有一个很棒的拖放工具），然后把你的data URI加入到一个<img>或<object>标签内，或是放到CSS中。
  
```
<img src="data:image/svg+xml;base64,[data]>
background: url(data:image/svg+xml;base64,[data]); 
<object type="image/svg+xml" data="data:image/svg+xml;base64,[data]> 
  fallback content here 
</object>

```
使用内联SVG

```
<body>
 <svg version="1.1" baseProfile="full" width="300" height="200" xmlns="http://www.w3.org/2000/svg" class="example">
   <rect width="100%" height="100%" fill="green" />
 </svg>
</body>

```

```
<body>
  <svg width="300" height="200" class="example">
    <rect width="100%" height="100%" fill="green" />
  </svg>
</body>

```
在SVG中嵌入image
相比把一个.svg文件嵌入到一个<img>标签中，反过来把一个位图图像嵌入到SVG代码中也是可以的。

```
<svg version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" width="300" height="200"> 
  <image width="300" height="200" xlink:href="path-to-image.png"/> 
</svg>

```

SVG图形和线条

 ######矩形 <rect>
  
 ######圆形 <circle>
  
 ######椭圆 <ellipse>
  
 ######线条 <line>
  
 ######折线 <polyline>
  
 ######多边形 <polygon>
  


矩形 <rect>
  
```
<svg width="300px" height="150px"> 
  <rect x="20" y="20" width="250px" height="125px" rx="5" ry="5" fill="teal" /> 
</svg>
```
```
x——定义矩形左上角的点的x坐标
y——定义矩形左上角的点的y坐标
rx——定义矩形四个圆角的x半径
ry——定义矩形四个圆角的y半径
width——定义矩形的宽度
height——定义矩形的高度
```
圆形 <circle>
  
```
<svg width="300px" height="300px"> 
  <circle cx="150" cy="150" r="100" fill="red" /> 
</svg>
```
```
cx——圆心的x坐标
cy——圆心的y坐标
r——圆的半径
```

椭圆 <ellipse>
  
```
<svg width="300px" height="300px"> 
  <ellipse cx="150" cy="150" rx="100" ry="75" fill="blue" /> 
</svg>
```
```
cx——椭圆中心点的x坐标
cy——椭圆中心点的y坐标
rx——定义椭圆的水平半径
ry——定义椭圆的垂直半径
```
线条 <line>

```
<svg width="300px" height="250px"> 
  <line x1="100" y1="200" x2="250" y2="50" stroke="#000" stroke-width="5" /> 
</svg>
```
```
x1——定义直线起点的x坐标
y1——定义直线起点的y坐标
x2——定义直线终点的x坐标
y2——定义直线终点的y坐标
```

折线 <polyline>
折线是一组相互连接的直线集合。使用SVG创建折线，你需要使用points这个属性，来定义你需要的任意数量的坐标点。
  
```
<svg width="300px" height="300px"> 
  <polyline points="10 10, 50 50, 75 175, 175 150, 175 50, 225 75, 225 150, 300 150" fill="none" stroke="#000"/> 
</svg>
```
多边形 <polygon>

```
<svg width="300px" height="200px"> 
  <polygon points="10 10, 50 50, 75 175, 175 150, 175 50, 225 75, 225 150, 300 150" fill="red" stroke="#000"/>
 </svg>
 ```
SVG渲染
SVG使用的是“画家算法”的渲染方式。也就是说它一次只对应绘制一个操作，后边的操作可以覆盖前边的操作。类似于CSS的级联。找个例子来说明会更清晰一些。
```
<svg width="300" height="200" xmlns="http://www.w3.org/2000/svg">
  <rect width="100%" height="100%" fill="green" />   
  <rect width="50%" height="50%" fill="purple" />
</svg>
```
上边的代码显示的结果是一个绿色的矩形，还包含了一个较小的紫色矩形。因为在代码中，紫色矩形写在绿色矩形后边，所以紫色的矩形会显示在绿色矩形的顶部，相对会更靠近查看图形的人。


填充属性fill
```
<rect class="rectangle" width="100%" height="100%" fill="red" /> 
<circle class="circle" cx="150" cy="150" r="100" fill="#039" />
```
或
```
.rectangle {fill: red;} .circle {fill: #039;}
```
默认情况下的填充颜色是 black 或者 #000000 ，所以如果你不想要你的图形被填充的话，你需要显式地设置 fill 为 none 。

fill-rule 属性

关于图形（或线条）的内部区域，是由 fill-rule 属性决定的，它有 nonzero 和 evenodd 两个值。
nonzero—这个规则通过从canvas上的某个点往任一方向绘制射线到无穷远，然后检查图形的线段和射线相交的点，来确定“内部区域”。从0开始计数，每次路径线段是从左到右穿过射线就加一，从右到左的就减一。通过计算交叉点，如果结果是0，则这个点在路径外边，不然，就是在里边。


evenodd—这个规则通过从canvas上某个点往任一方向绘制射线到无穷远，然后计算给定图形上线段路径和该射线交叉点的数量。如果这个数是奇数，那么该点在图形内部；如果是偶数，该点在图形外部。


fill-opacity 属性
它的取值应在0（透明）和1（不透明）之间，和CSS的opacity属性一样
描边属性
stroke颜色值 和 stroke-width测量值 属性
```
stroke="blue" 
stroke="#347559 
stroke-width="3px" 
stroke-width="1em" 
stroke-width="2%"
```

当 stroke-width 的值为百分比时，表示它是当前视图的百分比值。
```
<svg width="300px" height="150px">
   <ellipse cx="150" cy="75" rx="100" ry="75" fill="none" stroke="blue" stroke-width="3px" /> 
</svg>
```


stroke-opacity 属性
stroke-opacity="0.25"


stroke-linecap 属性
stroke-linecap 属性可以让你在线条末端控制图形。
你可以选择对接(butt)、方形(square)和圆形(round).



stroke-linejoin 属性
stroke-linejoin 属性也是类似的，但是它控制的是两条线段之间的衔接。你可以在绘制折线时使用它。它有三个值，尖角(miter)、圆角(round)和斜角(bevel)


如果你设置 miter 作为 linejoin 的值，它的线条就会呈锐角连接，而且尖角可能超过了描边的厚度。

stroke-miterlimit 属性
stroke-miterlimit 属性给 miter-length 和 stroke-width 之间的比率做了限制，它的比值范围应大于或等于1。当比值不在这个范围的时候， stroke 就会被转换成斜角（bevel）。

stroke-dasharray 属性
stroke-dasharray 是用于设置虚线的属性。你可以使用它来设置每条划线长度以及划线之间空格的大小。
```
<svg width="600px" height="300px">   
  <line x1="0" y1="20" x2="600" y2="20" stroke="#000" stroke-width="3" stroke-dasharray="10 2" />   
  <line x1="0" y1="40" x2="600" y2="40" stroke="#000" stroke-width="3" stroke-dasharray="5 10" />   
  <line x1="0" y1="60" x2="600" y2="60" stroke="#000" stroke-width="3" stroke-dasharray="1 1" />   
  <line x1="0" y1="80" x2="600" y2="80" stroke="#000" stroke-width="3" stroke-dasharray="10" />
</svg>
```
第一个值是划线的长度，
第二个值是各个划线之间的空格大小。
如果你只设置了一个值（如上面的最后一个示例），它会默认设置相同划线长度和划线空格。



stroke-dasharray 属性可以做的东西还有很多很多。虽然我之前的示例是它只接受一组值作为参数，但是它也可以接受多组值，并使用逗号来分隔每一组值。
```
<svg width="600px" height="60px"> 
  <line x1="0" y1="20" x2="600" y2="20" stroke="#000" stroke-width="3" stroke-dasharray="10 4, 5 10, 1 1, 10 30" /> 
</svg>
```

stroke-dashoffset 属性
最后一个属性是 stroke-dashoffset ，它可以让你设置需要图案延迟绘制的距离。它可以接受任何单位的值，同样的，如果使用的是百分比，就是相对于当前视图的百分比。
```
<svg width="600px" height="60px">     
  <line x1="0" y1="20" x2="600" y2="20" stroke="#000" stroke-width="3" stroke-dasharray="10 4, 5 10, 1 1, 10 30" stroke-dashoffset="10" />
</svg>
```
再回去看看上一段内容。 stroke-dashoffset 属性的结果和我最初的期望完全不符。我的初衷是设置一个偏移量，将图案的绘制起点往后移。可是结果恰恰相反，偏移量是让图案往前移的。
这是应用了偏移量和没有应用偏移量的同一个图案。




图形和线条
线条没有什么内部填充，但是如果它是折线的话，可能就可以被填充了。折线可以看成是由每条有端点的线段组成的多边形。
SVG属性和CSS
可以添加内联CSS，也可以直接在你的CSS文件中设置样式
路径元素
```
<svg> 
  <path d="path data" /> 
</svg>
```
定义的路径(d)使用了不同的指令，移动到一个新的点，然后绘制不同的直线和曲线。

路径元素可以带有一个pathLength属性。这个属性接收一个非负数作为值，并使用这个值来覆盖浏览器计算的路径长度。
```
<svg>   
  <path d="path data" pathLength="non-negative-number" />
</svg>
```
不同路径的数据指令
直线指令
moveto(M 或 m):移动到新的位置
lineto(L 或 l):从当前坐标画一条直线到一个新坐标
horizontal lineto(H 或 h):画一条水平线到新坐标
vertical lineto(V 或 v):画一条垂直线到新坐标
closepath(Z 或 z):关闭当前路径
你不需要将指令拼写出来，使用指令字母即可。指令字母大写表示坐标位置是绝对位置，指令字母小写表示坐标位置时相对位置。
moveto和lineto指令
```
<svg width="600" height="400"> 
  <path d="M 50 50 l 0 300 l 200 0 l 0 -300 l -200 0" fill="none" stroke="#000" stroke-width="2px" /> 
</svg>
```
路径的数据以移动到一个坐标为 x=50 y=50 (M 50 50)的点为开始，每条路径都需要以一个moveto指令为开始。
接下来是一个lineto指令，这里设置一个小写字母 l (l 0 300)。这个指令指的是从当前坐标（50 50）画一条直线到相对坐标 (0 300)。也就是说，直线会在水平方向绘制0px，在垂直方向绘制300px。
接着，是另一个lineto指令 (l 200 0)，绘制一条200px的水平线。后面的两条指令是 (l 0 -300)和 (l -200 0)，这两条指令绘制了另外两条线，一条水平线和一条垂直线，和初始的水平线和垂直线在相反的方向上。
closepath指令
```
<svg width="600" height="400">     
  <path d="M 50 50 l 0 300 l 200 0 l 0 -300 Z" fill="none" stroke="#000" stroke-width="2px" />
</svg>
```
这里的代码和第一个示例绘制出的图形是一样的，不同的一点是：我用一个closepath指令(Z)替换了最后一个lineto指令(l)。因为没有指定坐标，所以使用 Z 和 z 效果是一样的。
正如你所看到的，它和前面的示例效果完全一样，但是closepath使得我们可以不需要指定最后一组坐标。

horizontal lineto 和 vertical lineto指令
```
<svg width="600" height="400"> 
  <path d="M 50 50 v 300 h 200 v -300 Z" fill="none" stroke="#000" stroke-width="2px" /> 
</svg>
```
这里使用了vertical lineto(v)和hosizontal lineto(h)指令替换了中间的三个lineto指令。这两个指令只需要x和y两个坐标值中的一个，另一个值它会自己确定为0

样式、空格和逗号
对于使用空格，你应该有一些调节措施。你可以通过移动或者添加空格，使得各个指令以及整个路径的数据阅读起来更简明。
```
<svg width="600" height="400">   
  <path d="M50 50  v300  h200  v-300  Z" fill="none" stroke="#000" stroke-width="2px" />
</svg>
```
在这里，我去掉了一些指令和它们的第一个值之间的空格。我还在最后一个坐标之后、下一条指令之前添加了额外的空格。
虽然逗号不是必要的，你也可以在每条指令后边使用他们来分隔x和y坐标。你不能在指令之间使用逗号，但是你可以在坐标之间使用。
```
<svg width="600" height="400">   
  <path d="M50,50  v300  h200  v-300  Z" fill="none" stroke="#000" stroke-width="2px" />
</svg>
```
我在路径起点的x和y值之间添加了一个逗号。我可以保留它们之间的空格，但是考虑到坐标之间没有空格的话更容易阅读。在这方面你可以灵活一些。


曲线指令
曲线指令一共有三组，和直线指令一样，指令字母大写表示坐标位置是绝对坐标，指令字母小写表示坐标位置是相对坐标。
三次贝塞尔曲线指令 (C, c, S, s)
二次贝塞尔曲线指令 (Q, q, T, t)
椭圆弧线 (A, a)
三次贝塞尔曲线指令
我会假设你已经对贝塞尔曲线很熟悉，可能你已经在某些图形编辑器里绘制过。我就不解释他们的数学原理了，但是你可以通过定义一个起点和终点，以及两个控制点（一个控制起点，一个控制终点），绘制一条贝塞尔曲线。
三次贝塞尔曲线指令的格式为：
```
C (or c) x1,y1 x2,y2 x,y 
```
这里
x1,y1 是曲线起点的控制点坐标
x2,y2 是曲线终点的控制点坐标
x,y 是曲线的终点坐标
曲线的起点是上一条指令的终点，所以我们不需要再次设置。
举个例子吧，我会像之前一样，所有的示例都使用内联SVG。
```
<svg width="600" height="300">   
  <path d="M100,200  C100,100  400,100  400,200"    fill="none" stroke="#000" stroke-width="2px" />
</svg>
```
我从一个SVG元素开始，给它设置宽度和高度值，还有一个填充以及描边。希望你现在对这几个属性都已经很熟悉。
路径从点(100,200)开始，这也是曲线的起点。三次贝塞尔曲线指令(C)绘制曲线，第一个控制点的坐标是(100,100)，第二个控制点是(400,100)。终点坐标是(400,200)。


曲线从第一个控制点的方向开始，然后转弯，再根据第二个控制点的方向到达曲线终点。


像直线一样，你不需要只用一条曲线就结束绘制。你可以把曲线一条一条连接起来然后创建更复杂的曲线。
```
<svg width="600" height="300">   
  <path d="M100,200  C100,100  400,100  400,200  c100,200  400,100  300,0" fill="none" stroke="#000" stroke-width="2px" />
</svg>
```
在这里，我添加了第二条贝塞尔曲线来连接第一条。你可以看到他们之间的衔接不是很平滑。


通常，在连接曲线时，第二条曲线的起点控制点是第一条曲线终点控制点的对称点。
幸运的是，你不必弄清楚如何计算控制点的反射。S 和 s 指令是让浏览器帮你计算对称点的快捷方式，使用(S s)指令创建对称的控制点很容易。
```
<svg width="600" height="300">     
  <path d="M100,200              
           C100,100  400,100  400,200              
           s100,100 300,0"      
  fill="none" stroke="#000" stroke-width="2px" />
</svg>
```
在这里我用了一个相对定位的指令(s)快捷地创建了第二条曲线，来匹配使用相对坐标的曲线。你可以看到两条曲线连接的交点处相比之前平滑了很多。


这里是另外的两条曲线，这次使用的是绝对定位的指令(S)的快捷方式。
```
<svg width="600" height="300">     
  <path d="M100,200              
           C100,100 400,100 400,200              
           S400,100 300,0"     
  fill="none" stroke="#000" stroke-width="2px" />
</svg>
```


他们看起来完全不一样，即使两条曲线之间的连接还是很平滑。接合的地方可能不平浅，但也是平滑的。你再绘制一条独立的曲线就能明白我的意思，只不过这次第二条曲线使用的是绝对定位的曲线。
```
<svg width="600" height="300">     
  <path d="M100,200               
           C100,100  400,100  400,200               
           C100,200  400,100  300,0"      
   fill="none" stroke="#000" stroke-width="2px" />
</svg>
```

如果你的曲线不能按照你想象的绘制出来，可能是因为你绝对定位和相对定位使用颠倒了。


二次贝塞尔曲线指令
你的直觉可能会告诉你，二次贝塞尔曲线指令会更复杂，还添加了一个额外的控制点。但是恰恰相反。
二次贝塞尔曲线指令只需要一个控制点，同时作为起点控制点和终点控制点。
```
<svg width="600" height="300">     
  <path d="M100,200              
           Q250,100 400,200"      
  fill="none" stroke="#000" stroke-width="2px" />
</svg>
```
我们还是使用moveto指令作为开始，绘制二次贝塞尔曲线。曲线的起点坐标是(100,200)，终点坐标是(400,200)，控制点坐标是(250，100)。


二次贝塞尔曲线指令也有一个快捷方法，(T 或 t)指令可以用来平滑多条曲线之间的连接。它和三次贝塞尔曲线指令中的快捷方式(S 或 s)是同样的效果，也有助于通过对称的控制点来平滑地开始绘制第二条曲线。
```
<svg width="600" height="300">   
  <path d="M100,200            
           Q250,100 400,200            
           T600 200"     
  fill="none" stroke="#000" stroke-width="2px" />
</svg>
```


二次贝塞尔曲线指令是比较容易使用的，因为它只需要一个控制点。但是三次贝塞尔曲线指令有额外的控制点，所以可以提供更多的控制。


椭圆弧线
三种曲线指令中的最后一种是椭圆弧线(A 或 a)。下面这个弧线指令绘制了一段椭圆，它是曲线指令里边需要最多参数的，格式如下：

```
A rx ry  x-axis-rotation  large-arc-flag  sweep-flag  x y 
```

这里
x,y 是弧线的终点
rx 是弧线在x轴方向的半径
ry 是弧线在y轴方向的半径
x-axis-rotation 是与x轴夹角的度数
椭圆弧绘制出的弧线是椭圆的一个片段。若rx和ry的值相同，则绘制出圆。
以下两个标志需要一些讲解。给定起点和终点坐标，以及rx ry x-axis-rotation的值，绘制出的弧线有四种可能，用下边的示例看起来比较清晰。
```
<svg width="600" height="300">
  <path d="M250,100  A120,80 0 0,0 250,200"     
    fill="none" stroke="red" stroke-width="5" />
    
  <path d="M250,100  A120,80 0 1,1 250,200"     
    fill="none" stroke="green" stroke-width="5"/>
    
  <path d="M250,100  A120,80 0 1,0 250,200"     
    fill="none" stroke="purple" stroke-width="5"/>
    
  <path d="M250,100  A120,80 0 0,1 250,200"     
    fill="none" stroke="blue" stroke-width="5"/>
</svg>
```



在四段弧线连接处的这两个点分别是起点（上）和终点（下），这三个椭圆都有相同的rx, ry, x-axis-rotation值。正如你看到的这四段不同的弧线，分别都是从起点绘制到终点。

这四段弧线的区别是 large-arc-flag 和 sweep-flag 参数的值。图中的红色和紫色弧线，sweep-flag的值都为0，红色弧线 large-arc-flag 的值为0，而紫色弧线 large-arc-flag 的值为1。它们的区别仅在于 large-arc-flag 值的不同。

对比这两段圆弧，你能猜出 large-arc-flag 值是用来干嘛的吗？值为0表示使用较小的弧线，值为1表示使用较大的弧线。

现在比较一下红色和蓝色弧线。这两段弧线的 large-arc-flag 值都为0，所以它们都是较小的弧线。但是红色弧线还有一个 sweep-flag 值为0，而蓝色的 sweep-flag 值为1。

蓝色弧线和红色弧线是关于起点和终点所在的坐标轴对称的。 sweep-flag 的值决定了是使用弧线(值为0)还是使用它的轴对称弧线(值为1)。
