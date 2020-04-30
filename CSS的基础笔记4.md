# CSS的基础笔记4

字体 font
---
font的属性
------
- color 前景色，也是设置字体颜色的方式。

- font-size 字体大小
> em相对于当前元素的一个font-size，rem相对于根元素的一个font-size。

- font-family 字体族（字体的格式-矢量图），这里是推荐用户使用字体不提供下载，不涉及版权问题。
> 可以写多个值，从左到右优先使用，从用户电脑中选择字体使用。<br/>
> 特殊值：serif 衬线字体；sans-serif 非衬线字体；monospace 等宽字体，一般可以写在字体的最后用来兜底，更多类别查看MDN。<br/>
@font-face可以将服务器的字体直接提供给用户去使用，里面有两个值，font-family指定字体的名字（css中font-family指定这个名字来使用），src指定字体路径，会出现几个问题，一个第一次加载速度慢的问题，第二个是字体版权问题，第三个是字体格式，一般是ttf，具体查看MDN。

```html
<style>
    @font-face {
        font-family: "myfont";    /* 自定义的字体名字 */
        src: url(../font/字体文件名.tff);  /* 字体文件的路径 */
    }
    p{
        fontfamily: myfont;   /*通过名字来使用服务器的字体*/
    }
</style>
```

<br/>

图标字体iconfont（比较重要）
---
> 网页中经常需要使用一些图标，可以通过图片来引入图标，但是图片比较大，并且非常不灵活，所以有了图标字体。通过font-face来引入字体形式的图标。<br/>
<ul>fontAwesome的使用
   <li>1.先下载fontAwesome; </li>
   <li>2.把css和webfonts文件夹移动到项目中;</li>
   <li>3.用link引入css/all开头任意一个css;</li>
   <li>4.用span或者i标签等加上类名来作为图标字体，可以设置字体大小颜色。</li>
</ul>

```html
<style>
  <link rel="stylesheet" href=".fa/css/all.css">   /* 引入fontAwesome文件 */
    li{
      list-style: none;
    }
    li::before{
      content: '\f1b0' ;   /*编码*/
      font-family: 'Font Awesome 5 free';
      font-weight: 900;     /*这两行都是根据不同编码去找对应的是fas还是fab对应的font-face下的字体*/
      color: blue;
      margin-right: 5px;
    }
</style>
<body>
  <i class="fas fa-bell"></i>  /* 用类名使用图标字体，class="fas/fab 图标名" */
  <span class="fas">&#xf0f3;</span>   /* 前面要先写类,然后通过实体来使用图标字体，&#x图标编码; */
  <ul>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
  </ul>
</body>
```

<br/>

<ul>阿里巴巴矢量图的使用，版权问题需要联系原作者
> 彩色的图标不要使用图标字体
  <li>1.进入官网找到心仪的图标；</li>
  <li>2.对心仪的图标加入购物车；</li>
  <li>3.在购物车中添加至项目；</li>
  <li>4.下载至本地；</li>
  <li>5.将除了html和demo的文件都移入项目中；</li>
  <li>6.用link引入iconfont.css文件；</li>
  <li>7.用span或者i标签等加上类名iiconfont来作为图标字体；</li>
  <li>8.具体使用看附带的demo.index里有多种方式，字体family都是iconfont，用法类似上面。</li>
  <li>9.要设置图标大小要对类名设置字体大小<li>
</ul>

```html
<style>
  <link rel="stylesheet" href="./iconfont/iconfont.css">    /* 引入阿里的图标字体 */
  i.iconfont{    /*设置i标签的图标大小*/
    font-size: 20px;
  }
  p::before{    /* 在p标签前添加图标字体符号，对li同理 */
    content: '\e625';   /* 编码在demo.html中 */
    font-famuly: 'iconfont';
    font-size: 20px;
  }
</style>
<body>
  <i class="iconfont icon-qitalaji">  /* 通过类名使用iconfont，编码在demo.html中*/
  <i class="iconfont">&#xe61c;</i>    /* 通过实体使用iconfont，编码在demo.html中*/
</body>
```

<br/>
行高 line height
---
> 行高指的是文字占有的实际高度，可以通过line height来设置行高。
- 行高可以直接指定大小，也可以直接设置整数，如果是整数就是当前字体的指定倍数，默认是1.33倍。
- 字体框就是字体存在的格子，设置font-size就是设置字体框的高度。
- 行高会在字体框的上下平均分配，所以行高等于高度一样可以做到单行文字在元素中垂直居中。
- 行高还经常用来设置文字的行间距，行间距 = 行高 - 字体大小
