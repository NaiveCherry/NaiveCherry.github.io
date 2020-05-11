# CSS的基础笔记6

过渡 transition
---
> 通过过渡可以指定一个属性发生变化时的切换方式，可以创建一些很好的效果，提高用户体验。

过渡是写在元素样式中的，需要先写好通过伪类或者其他触发事件变化后的属性值。

<br/>

transition-property 过渡的属性
------
> 指定要执行的过渡属性，多个属性之间用逗号隔开，如果是所有属性就用all，all同时也是默认值。

注：大部分属性都支持过渡效果，宽高度、边距、边框、定位、颜色等数值类都可以使用，不可以是无效数值，例如auto。

<br/>

transition-duration 过渡时间
------
> 指定过渡效果持续时间，单位一般用秒（s）和毫秒（ms），1s=1000ms 。

<br/>

transition-timing-function 过渡的时序函数
------
> 指定过渡的动画速度。
- ease：默认值，慢速开始，然后加速，最后减速。
- linear：匀速运动。
- ease-in：加速运动，慢速开始，一直加速。
- ease-out：减速运动，快速开始，最后减速。
- ease-in-out：先加速，中间快，后减速，类似ease。
- cubic-bezier（）：自定义贝塞尔曲线来指定时序函数。
- steps（）：分步执行，括号为分为几段执行，可以用来做图片人物动画效果。
> steps可以有第二个值，end/start，end表示时间结束执行过渡，start表示时间开始执行过渡。

<br/>

transition-deley 过渡的延迟
------
> 指定过渡效果经过一断时间后执行。

<br/>

一般情况下常用简写属性transition，如果有延迟，那么延迟的属性值要写在持续时间的后面，其他没有次序要求。

<br/>

动画 animation
---
关键帧
------
要设置动画效果，必须先设置一个关键帧，关键帧设置了动画执行的每一个步骤
```
@keyframes test {   <!-- test表示关键帧名字 -->
  <!-- from表示动画的开始位置,可以使用百分比 -->
  from{
    margin-left: 0px;
  }
  
  <!-- to表示动画的结束位置，可以使用百分比 -->
  to{
    margin-left: 700px;
  }
  
}
```
<br/>

animation-name 动画使用的名字
------
> 通过设置属性值为关键帧名字，来使用关键帧

<br/>

animation-duration 动画的执行时间
------
> 动画的执行时间,属性值单位可以使用毫秒和秒。

<br/>

animation-delay 动画的延迟
------
> 动画经过一段时间后执行动画。

<br/>

animation-timing-function 动画的时序函数
------
> 和延迟的使用方法一致

<br/>
animation-iteration-count 动画的迭代，代表动画执行的次数
------
> 属性值可以写数字，或者infinite表示无限执行。

<br/>
animation-direction 动画运行的方向
------
- normal：默认值，每次都是从from到to执行。
- reverse：每次都是从to到from执行。
- alternate：在从form到to和从to到from循环执行。
- alternate-reverse：在从to到form和从frome到to循环执行。

<br/>

animation-play-state 动画的执行状态
------
- running：默认值，动画执行
- paused：动画暂停

<br/>

animationg-fill-mode 动画的填充模式
------
- none：默认值，动画执行完毕回到原来的位置。
- forwards：动画执行完毕元素会停止在动画结束的位置。
- backwards：动画延迟等待时，元素就会处于开始的状态。
- both：具备backwards和forwards的特点。

简写属性animation和过渡类似，如果有延迟，要写在动画时间的后面，其他没有顺序要求。
