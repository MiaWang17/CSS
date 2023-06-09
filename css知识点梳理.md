###CSS
####css语法格式
1、CSS 由两个主要的部分构成：选择器，以及一条或多条声明:
![示例图](./image/css.jpg)
2、CSS声明总是以分号 ; 结束，声明总以大括号 {} 括起来:
~~~
p {
  color: pink,
  font-size: 20px;
}
~~~
####css创建
######1、内部样式
在单个文档中使用style标签在文档头部定义内部样式表
~~~
  <style>
    body {
      background-color: pink;
    }
    #title {
      color: red;
    }
  </style>
~~~
######2、外部样式
当样式需要应用于很多页面时，就可以使用外部样式表，每个页面使用link标签链接到样式表,link 标签在文档头部
~~~
<head>
  <link rel="stylesheet" type="text/css" href="./index.css">
</head>
~~~
####盒模型
元素可以理解为盒子，它是有content(宽高) + padding(内边距) +border(边框)+margin(外边距组成)
1、标准盒模型
总宽度 = width + padding + border + margin组成，宽度同理
content宽度 = width
![](image/box1.png)
2、IE盒模型
总宽度 = width + margin
content宽度 = width - border - padding
![](image/box2.png)

Demo: box.html
######3、内联样式
由于要将表现和内容混杂在一起，内联样式会损失掉样式表的许多优势。慎用这种方法，例如当样式仅需要在一个元素上应用一次时,可以使用内联样式。
~~~
<p style="color:sienna;margin-left:20px">这是一个段落。</p>
~~~
####文档流
文档流指的是HTML中元素在计算布局排版的过程中,所有处于文档流中的元素会自动的从左到右(非块级元素),从上到下块级块元素)的排列规则
######元素在排版中的定位类型分为三种:
(1)文档流:块级格式化的块级盒子, 行内格式化的行内盒子以及相对定位的块级盒子和行内盒子

(2)浮动(float)

(3)绝对定位(position:absolute/fixed)
####css基础选择器
#####一、常用选择器包含
######1、标签选择器
HTML标签名作为选择器
######2、类选择器
给元素添加class属性，可以对一个或某几个标签增加样式
语法：
~~~
  <div class="center">文本居中111</div>
  <p class="center">文本居中222</p>
  .center {
    text-align: center;
  }
~~~
######3、id选择器
给元素添加id属性来设置id选择器，css用#定义
*id选择器唯一
*通常class用于css布局，id用于js操作对象
~~~
  <div id="title">id选择器</div>
  #title {
    color: red;
  }
~~~
问题扩展：页面上写了相同id样式会怎样？
#####二、群组选择器
语法：选择器1,选择器2,选择器3,...{}
作用：对多个选择器同时设置相同样式
~~~
  h1,.box,.color {
    text-align: center;
  }
  p,.color {
    color: red
  }
~~~
#####三、关系选择器
######1、后代选择器
写法：父级 后代{}
~~~
  .offspring p {
    width: 200px;
    height: 200px;
    background: powderblue;
  }
~~~

######2、子代选择器
写法：父>子{}
~~~
  .father>p {
    width: 100px;
    height: 100px;
    background: peachpuff;
  }
~~~
######3、相邻兄弟选择器
指定选择器后面紧挨着的兄弟选择器
写法：指定选择器+兄弟{}
~~~
  .brother+p {
    width: 200px;
    height: 200px;
    background: pink;
  }
~~~
######4、通用兄弟选择器
指定选择器后面所有兄弟选择器
写法：指定选择器~兄弟{}
~~~
  .brother2~p {
    width: 200px;
    height: 200px;
    background: pink;
  }
~~~
######5、伪类选择器
######1、以child结尾
在指定元素子集的所有元素中选择
:first-child 第一个子元素
:last-child 最后一个子元素
:nth-child(n) 第n个子元素
*nth-child() 
n: 第几个子元素
even或者2n 选中偶数位的元素
odd或者2n+1选中奇数位的元素
######2、以type结尾
在指定元素子集的相同元素中选择
:first-of-type 第一个子元素
:last-of-type 最后一个子元素
:nth-of-type(n) 第n个子元素
######3、hover
鼠标滑过时修改样式
######6、伪元素选择器
伪元素选择器可以利用css创建标签元素，而不需要HTML标签，简化HTML结构
::before 在元素内部的前面插入内容
::after 在元素内部的后面插入内容
#####注：
* before和after创建了一个元素，属于行内元素
* 新创建的元素在文档树中找不到，所以叫伪元素
* 语法：element::before{}
* before和after必有content属性（因为w3c规定的content的初始值为none，none不能生成为元素）
####选择器权重
!important >内联样式 > id > 类选择器 > 标签选择器
* 第一优先级：css属性+!important 拥有最高权限
* 第二优先级：给标签加style，即内联样式  权值1000
* 第三优先级：id选择器，#id｛｝ 权值100
* 第四优先级：class选择器、伪类选择器 权重10
* 第五优先级：元素选择器、伪元素选择器  权值1
####属性及继承关系
######1、常用属性
* 字体：
1、font-size: 文字大，浏览器默认的大小是16px, 支持的最小字体是12px
2、font-weight: 文本粗细 100-900  bold/bolder 加粗  normal = 400 正常
3、color：字体颜色 red; #000; raba();
* 文本：
1、line-height 行高
2、text-aline 水平对齐方式 left(默认)、center、right
* 背景: background-color
* 边框及圆角：border 、 border-radius
1、border-style: 边框线形
  属性值： solid: 实线 dashed: 虚线 dotted: 点线 double:双实线
2、border-width 线宽 
3、border-color 颜色
4、复合写法border: 1px solid red
5、圆角border-radius
定义元素显示模式：display (block、inline、inline-block)及区别
* display:
block: 块元素（div, p）独占一行，可设置宽高
inline: 行内元素（span, i，input）和相邻行内或行内块元素，在一行，宽高设置无效
inline-block: 行内块元素、和相邻行内或行内块元素，在一行，可设置宽高
none: 标签隐藏，不占位
* 定位：poition(top、left、right、bottom)
relative: 相对定位：即相对于元素的正常位置进行定位
absolute: 绝对定位： 相对于第一个定位的父级元素进行定位
fixed: 相对于浏览器窗口的位置。使用固定定位的元素无论如何滚动浏览器窗口元素
的位置都是固定不变的。
#####题目：页面内所有元素，字体样式设置为绿色
######2、继承
可继承的属性：以上属性的字体、文本
####问题： 两个块块元素在同一行，一个在最左侧，一个在最右侧
#####浮动：float(脱离文档流)
浮动后，块元素可占据一行
问题：浮动会脱离文档流，不在文档流中站位，如果父级元素没有高度，就会影响后面的标准流
######办法：清除浮动
清除浮动的策略是: 闭合浮动
* clear: both(只有在块元素中生效)
* 1、额外标签法（隔墙法）
在浮动元素的末尾添加一个空标签（必须是块标签），设置clear:both
缺点：增加无意义的标签（结构查）
* 2、利用伪元素after属性
```
  display: block;
  content: '';
  clear: both;
```
问题:一个元素水平垂直居中？
#####flex布局
任何一个容器都可以指定为 Flex 布局。
~~~
.box {
  display:block
}
~~~
flex布局，有两条轴，主轴和交叉轴
![例图](./image/flex1.png)
flex-direction：属性决定主轴的方向（即项目的排列方向）。
~~~
.box {
  flex-direction: row | row-reverse | column | column-reverse;
}
~~~
![](./image/flex2.png)
justify-content：属性定义了项目在主轴上的对齐方式
~~~
.box {
  justify-content: flex-start | flex-end | center | space-between | space-around;
}
~~~
align-items属性定义项目在交叉轴上如何对齐。
![](./image/flex3.png)
~~~
.box {
  align-items: flex-start | flex-end | center | baseline | stretch;
}
![](./image/flex4.png)
~~~
####学习参考文档：
http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html
https://blog.csdn.net/TriDiamond6/article/details/106048140
####作业
1、实现如下图效果
![](./image/作业1.png)
2、完成如下页面
* tab栏文字间距相同，鼠标划过时，字体颜色变为蓝色
* 书皮图片，鼠标划过时，有放大效果
* 底部'个人博客'不一直在页面最下方，不跟随页面滚动
![](./image/22.png)

