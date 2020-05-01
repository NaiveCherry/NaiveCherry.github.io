# CSS的基础笔记5

text 文本属性
---

text-alingn 文本的水平对齐
------
- left 左对齐
- right 右对齐
- center 居中对齐
- justify 两端对齐

vertical-alingn 元素的垂直对齐
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

背景 background
---
background-color 背景颜色
------

background-image 背景图片
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
> 可以同时设置背景图片和背景颜色，如果图片是透明的，那背景颜色就可以成为背景色。
> 如果图片小于元素，则背景图片会自动平铺，铺满屏幕
> 如果背景的图片大于元素，图片会无法完全显示

<br/>

background-repeat 背景的重复方式
------
- repeat 默认值，背景会沿着x轴和y轴重复铺满
- repeat-x 沿着x轴重复
- repeat-y 沿着y轴重复
- no-repeat 背景图片不重复

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

<br/>

backgroun-clip 设置背景的位置
------
- border-box 默认值，背景会出现在边框的下面
- padding-box 背景不会出现在边框，只出现在内容区和内边距
- content-box 背景只会出现在内容区

background-origin 背景图片的偏移量计算的原点
