# CSS的定位

## position
- 用于指定一个元素在文档中的定位方式
### 属性值：

1. static（默认值）
> 对象遵循常规流，此时4个定位偏移属性不会被应用。
```html
<style>
#div {
	position: static;
  	top: 50%;/*不会被应用*/
  	border: #000000 solid 3px;/*宽度100%，高度为内容高度*/
}
</style>
```

2. relative
> 对象遵循常规流，并且参照自身在常规流中的位置通过top、right、bottom、left这4个定位偏移属性进行偏移时不会影响常规流中的任何元素。
> relative(相对定位)是指给元素设置相对于原本位置的定位
```html
<style>
#div {
	position: relative;
	top: 50%;/*会被应用*/
	border: #000000 solid 3px;/*同static*/
}
</style>
```

3. absolute
> 对象脱离常规流，此时偏移属性参照的是离自身最近的定位祖先元素，如果没有定位的祖先元素，则一直回溯到body元素。盒子的偏移位置不影响常规流中的任何元素，其margin不与其他任何margin折叠。
> absolute(绝对定位)是指给元素设置绝对的定位
```html
<style>
#div {
	position: absolute;
	top: 50%;/*会被应用*/
	border: #000000 solid 3px;/*div块元素宽度和变成内容宽度，不再是100%*/
}
</style>
```

4. fixed
> 与absolute一致，但偏移定位是以窗口为参考。当出现滚动条时，对象会固定在窗口中。
```html
<style>
#div {
	position: fixed;
	top: 50%;/*会被应用*/
	border: #000000 solid 3px;/*同absolute*/
}
</style>
```

5. sticky（CSS3）粘性定位元素
> 对象在常态时遵循常规流。它就像是relative和fixed的合体，当在屏幕中时按常规流排版时为相对定位，当到屏幕外时相当于fixed绝对定位，该属性的表现是现实中你见到的吸附效果。
```html
//可以用作吸顶菜单栏，当
<style>
body{
	height: 3000px;
	border: #000000 solid 3px;
}
#dv1 {
	position: sticky;
	border: #000000 solid 3px;
	margin-top: 80px;/*当div移出屏幕外时无效*/
	top: 0px;/*当div移出屏幕外时生效*/
}
</style>
```

5. inherit(可以忽略)
> 继承父元素的position属性，我可以直接去复制父元素的position，暂时没发现有什么大的用处。
