# CSS的基础笔记4

字体 font
---
font的属性
------
- color 前景色，也是设置字体颜色的方式。

- font-size 字体大小
> em相对于当前元素的一个font-size，rem相对于根元素的一个font-size。

- font-family 字体族（字体的格式-矢量图），这里是推荐用户使用字体不提供下载，不涉及版权问题。
> 特殊值：serif 衬线字体；sans-serif 非衬线字体；monospace 等宽字体，一般可以写在字体格式的最后用来兜底，更多类别查看MDN。<br/>
> 可以写多个值，从左到右优先使用，从用户电脑中选择字体使用。
> @font-face可以将服务器的字体直接提供给用户去使用，里面有两个值，font-family指定字体的名字（css中font-family指定这个名字来使用），src指定字体路径，会出现几个问题，一个第一次加载速度慢的问题，第二个是字体版权问题，第三个是字体格式，一般是ttf，具体查看MDN。

- 图标字体iconfont（比较重要）
> 网页中经常需要使用一些图标，可以通过图片来引入图标，但是图片比较大，并且非常不灵活，所以有了图标字体。通过font-face来引入字体形式的图标。<br/>
> fontawesome的使用，1.先下载fontawesome;2.把css和webfonts文件夹移动到项目中;3.用link引入css/all开头任意一个css;4.用span或者i标签等加上类名来作为图标字体，可以设置字体大小颜色。
```html
<i class="fas fa-bell"></i>  /* class="fas/fab 图标名" */
```
