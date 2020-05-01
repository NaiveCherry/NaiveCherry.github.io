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

