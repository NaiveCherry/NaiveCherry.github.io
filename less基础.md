# less基础
> less是一门css的预处理语言，是css的增强版，可以通过less实现编写更少的代码实现更强大的样式。<br/>
对变量的支持，比css3有更好的兼容性，对mixin的支持，语法大致和css一致，但是添加了许多对css的拓展。

<br/>

基本语法：
---
- 后缀为less，内容还是可以写css代码。在vscode装easy less插件后可以自动编译成css文件。
- less的单行注释//开头不会被解析到css中，多行注释/**/会被解析到css中。
- 可以在外围的选择器样式里面写里面的选择器样式，编译后会自动变成css的语法。
```
.box{
  width: 200px;
  div{		//对box中的div设置样式
    width: 150px;
    margin: 0 auto;
    img{	//对box中的div中的img设置样式
      width:100%;
    }
  }
}
```

<br/>

变量
---
> 用于存储属性值，可以任意修改这个值，变量值直接使用@变量名来使用，作为一部分值时使用@{变量名}的形式使用<br/>
如果冲突使用就近原则，可以先使用后声明（不建议）。

```
@a:100px;	//@开头，a是变量名，100px是值。
@c:box1;	//也可以存储选择器名。
@d:color;	//也可以存储属性名。

//使用方法
.body{
	@b:#bfa;	//局部声明
	width:@a;
	@{d}:@b;
}
.@{c}{	//使用类选择器时，前面要加. id加#，并且是作为一部分，用@{变量名}来使用。
	width:@a;
}
```

```
body{
	width: 200px;
	heigth: $width;		//可以用$引用其他属性名的值。
}
```

<br/>

less中特别的选择器
---
- &：表示外一层的选择器，也可以当作外层选择器的替代符
- >：子元素选择器
- 后代选择器直接写在祖先样式内部就可以生效
- extend：拓展，对当前选择器拓展选择器的样式（选择器分组）
```
.p1{
	width: 100px;
	height: 200px;
}
.p2:extend(.p1){	//在.p1的样式基础上拓展样式，获得p1的样式方式是选择器分组。
	color: red;
}

.p3{
	.p1();	//可以拿到p1设置的样式，叫做mixin混合函数，把p1的样式复制过来，性能比extend差一点。
}

//使用类选择器时可以在选择器后添加一个括号，这时候实际上就是创建了一个mixins混合函数，不被调用就不显示。
.p4(){
	width: 100px;
}
```

<br/>

混合函数
---
除了上面提到的使用，主要使用方式是配合参数传递使用。
```
.test(@w,@h,@bd-color){	//其中@w和@h是形参，也可以不传递值提前设置好默认值，变量名后面冒号接属性值。
	width: @w;
	height: @h;
	border: 1px solid @bd-color;
}

div{
	.test{100,100,#bfa}	//100代表值也是实参，在使用带有形参的混合函数时，需要写实参传递给函数
	.test{@bd-color: #bfa, @w: 100px,@h :100px}	//默认是需要按照顺序写，或者是
}
```
> less有很多编程语言的语法，也有自带的系统函数。例如average()可以取平均值，颜色也是数值可以取平均数。<br/>
> darken(颜色，百分比)，darken函数是颜色加深函数，百分比是加深的百分比，0%为不变，100%是黑色。4

<br/>

less的一点特性补充
---
- less属性值可以进行加减乘除等运算。
```
width: 100px - 20px;
```
- import 引入，写在代码最上方，和java导包和link类似，可以对样式表进行合并，达到模块化处理。
```
@import "路径/样式文件名.less"
```

<br/>

sourceMap
---
作用：让调试显示的css行数改成对应的less行数<br/>

修改方法：<br/>
1.先复制less介绍中有关sourceMap的"less.compile:"内容<br/>
2.vscode的设置——>扩展——>Easy LESS configuration，点击Easy LESS configuration下面的“在settings.json中编辑” <br/>
3.在最后一行代码后加逗号，换行粘贴之前复制的less.compile。把compres属性值改成false，把sourceMap改成true，out改成true。
