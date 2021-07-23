# CSS的基础笔记5

text 文本属性
---

text-align 文本的水平对齐
------
- left 左对齐
- right 右对齐
- center 居中对齐
- justify 两端对齐

vertical-align 元素的垂直对齐
------
- baseline 默认值，基线对齐
- top 顶部对齐
- bottom 底部对齐
- middle 居中对齐（以x的中线对齐，不够标准）
- 可以指定值，能达到更好的显示效果。
> 图片等替换元素也是用字体的基线对齐，会有缝隙，通过设置非基线对齐可以解决。

text-decoration 设置文本修饰
------
- none 默认值，不设置
- nuderline 下划线
- line-through 删除线
- overline 上划线
> 可以在值后面增加颜色和线条样式，IE不兼容。

white-space 设置网页如何处理空白和换行
------
- normal 默认
- nowrap 不换行
- pre 保留，会保留代码写的空白

text-overflow
------
- ellipsis 溢出内容显示省略号

> 不换行配合overflow和text-overflow可以做到一行文本超出区域隐藏用省略号替代。

<br/>

背景 background
---
background-color 背景颜色和background-image 背景图片
------
```
<style>
    /* 设置背景颜色常见的几种方式 */
    background-color: red;
    background-color: rgba()/rgb();
    background-color: #fff/#ffffff;
    /* 设置背景图片的路径，注意默认会平铺 */
    background-image: url(../img/1.png);
</style>
```
- 可以同时设置背景图片和背景颜色，如果图片是透明的，那背景颜色就可以成为背景色。
- 如果图片小于元素，则背景图片会自动平铺，铺满屏幕
- 如果背景的图片大于元素，图片会无法完全显示

> 可以通过设置不同状态切换不同的背景图片来模拟做到一些动画显示效果，但是图片是外部资源，外部资源是按需加载，如果第一次网速太慢图片切换会不连贯，缓存后就正常显示了，所以用雪碧图来一次加载。

<br/>

background-repeat 背景的重复方式
------
- repeat 默认值，背景会沿着x轴和y轴重复铺满
- repeat-x 沿着x轴重复
- repeat-y 沿着y轴重复
- no-repeat 背景图片不重复

> 可以通过重复做到一个像素宽/高的渐变完成一条渐变栏，或者一张小图片达到有规律的大图片效果。

<br/>

background-position 用来设置背景图片的位置
------
- 通过方位词设置图片位置
> top、left、right、bottom、center几个表示方位的词，使用其中两个组合来设置图片的位置，相对于一个九宫格,如果只写一个值，默认第二个值是center。
- 通过设置偏移量设置图片位置

```html
<style>
    /* 第一个值是水平方向的偏移量，第二个值是垂直方向的偏移量，可以为负数 */
    background-position: 50px 30px;
</style>
```

> 常常会用在雪碧图中，通过设置x、y轴的值，x负数向右移动，y轴负数向下移动等操作，取要用的部分左上角的坐标，解决图片加载时不好的用户体验。

<br/>

backgroun-clip 设置背景在容器中的显示方式
------
- border-box 默认值，背景会出现在边框的下面
- padding-box 背景不会出现在边框，只出现在内容区和内边距
- content-box 背景只会出现在内容区

<br/>

background-origin 背景图片的偏移量计算的原点（设置从什么地方开始显示图片）
------
- padding-box 默认值，background-position从内边距处开始计算
- content-box 背景图片的偏移量从内容区处开始计算
- border-box 背景图片的偏移量从边框开始计算

<br/>

background-size 设置背景图片的大小
------
- cover 图片比例不变，将元素铺满，内容可能会显示不全
- contain 保持图片比例不变，将图片在元素完整显示
- 其他值：

```html
<style>
    background-size: 200px 200px;       /* 第一个值为设置宽度，第二个设置高度 */
    background-size: 200px;     /* 第一个值是宽度，第二个值保持图片宽高比自动设置 */
    background-size: 100% 100%;     /* 按比例显示 */
    background-size: 100% auto;      /* 设置其中一个值为比例，另一个值保持宽高比自动设置 */
<style>
```

<br/>

background-attachment 设置背景图片是否跟随元素移动（用的较少）
------
- scroll 默认值，背景图片跟随元素移动
- fixed 背景图片会固定在页面中

<br/>

background 背景简写属性
------
所有背景相关样式都可以通过该样式来设置，可以写多个值，没有顺序要求，但是size值必须在position值后面且中间用/隔开，clip值必须在origin值后面，没有必须要写的属性。

```html
<style>
    background: center center/contain no-repeat;       /* 第一个值是position的x轴，第二个是y轴，斜杠后面的是size属性值，第四个值是不重复 */
    background: border-box content-box;     /* 第一个值是origin值，第二个是clip的值，如果只写一个就是表示origin */
</style>
```

<br/>

雪碧图
------
> 多张小图组成的一张大图，为了解决请求多次加载造成闪烁，给用户不好的体验，而把小图组成大图一次加载全部，通过设置元素大小，背景图片设置为雪碧图，通过background-position来做到雪碧图的显示。

```
<style>
div{
    width: 200px;
    height: 100px;      /* 设置元素大小 */
    background-image:url(../img/1.png);     /* 把雪碧图作为背景 */
    background-position: 50px 50px;     /* 用定位来显示雪碧图显示区域，显示区域左上角点的坐标是50 50 */
}
</style>
```

<br/>

背景渐变
------
> 通过渐变可以设置一些复杂的背景颜色，可以实现从一个颜色到其他颜色过渡的效果，渐变是图片，需要通过background-imgae来设置。

## line-gradient 线性渐变
> 默认情况下是一种颜色逐渐过渡到其他颜色，颜色从左到右依次平均分布显示。

<br/>

线性渐变的属性值
- to left 从右到左
- to right 从左到右
- to bottom 从上到下
- to top 从下到上
- xdeg deg表示度数，可以通过角度调整
- xturn turn表示圈数，1圈等于360°，类似角度。

```html
<style>
    background-image: linear-gradient(red,yellow);      /* 从上往下颜色逐渐过渡 */
    background-image: linear-gradient(to right,red,yellow);      /* 从左往右颜色逐渐过渡 */
    background-image: linear-gradient(to right,red,yellow,#bfa);        /* 设置多个值，默认情况平均分布 */
    background-image: linear-gradient(0deg,red,yellow);     /* 设置渐变方向的角度 */     
    background-image: linear-gradient(to top right,red,yellow);         /* 渐变设置方向组合 */
    background-image: linear-gradient(0.5turn,red,yellow);      /* 渐变旋转半圈 */
</style>
```

<br/>

手动指定线性渐变的分布情况
```html
<style>
    background-image: linear-gradient(red 50px,yellow);      /* 红色延展到50像素开始开始向黄色渐变 */
    background-image: linear-gradient(red 50px,yellow 100px);       /* 红色延展到50像素开始向黄色渐变,到100像素结束渐变  */
    background-image：linear-gradient(red 0px,yellow 200px);        /* 如果像素是200像素高，那么这就是默认，红色从0开始往黄色渐变，到200像素结束 */
</style>
```

- repeating-line-gradient 重复渐变效果，需要配合手动指定分布情况，按照像素范围平铺。
> no-repeat 背景重复效果对渐变的重复不起作用

<br/>

## radial-gradient 径向渐变，从原点向外圈渐变
> 默认情况下，径向渐变形状是根据形状来计算的圆心的，正方形对应的圆形，长方形对应的椭圆形。

```
<style>
    background-image:radial-gradient(100px 100px,red,yellow);       /* 红色向黄色渐变到水平方向大小100px，垂直方向大小100px，其他地方都是黄色 */
</style>
```

大小的属性值：
- circle：正圆
- ellipse：椭圆
- closest-side：渐变延伸到最近的侧边停止
- farthest-side：渐变延伸到最远的侧边停止
- closest-corner：渐变延伸到最近的边角停止
- farthest-corner：渐变延伸到最远的边角停止
<br/>
位置的属性值：
- at x y：设置原点的坐标轴，x和y可以是center、top、left、right、bottom

> 语法 radial-gradient（大小 at 位置，颜色 位置，颜色 位置，颜色位置）
