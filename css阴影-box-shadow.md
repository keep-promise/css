#### 1.box-shadow属性语法
**box-shadow 属性接受值最多由五个不同的部分组成。**
box-shadow: offset-x offset-y blur spread color position;
**offset-x: X轴偏移量 **  

**offset-y: Y轴偏移量 **
**blur: 阴影模糊半径 **
**spread: 阴影扩展半径 **
**color: 阴影颜色 **
**position: 投影方式 **
box-shadow 属性没有子属性，这些组成部分的顺序更加重要，尤其是那些长度值。

<br>

#### 2.offset-x X轴偏移量
阴影水平方向的偏移
**值为正数时，阴影在元素的右侧**
**值为负数时，阴影在元素的左侧**

box-shadow: 20px 0px 10px 0px rgba(0,0,0,0.5) 
box-shadow: -20px 0px 10px 0px rgba(0,0,0,0.5) 

<br>

#### 3.offset-y
阴影竖直方向的偏移
**值为正数时，阴影在元素的下方**
**值为负数时，阴影在元素的上方**

box-shadow: 0px 20px 10px 0px rgba(0,0,0,0.5)
box-shadow: 0px -20px 10px 0px rgba(0,0,0,0.5) 

<br>

#### 4.blur
阴影的模糊半径
**值为 0 意味着该阴影是固态而锋利的,完全完全没有模糊效果**
**blur 值越大，阴影更朦胧 / 模糊**
**负值是不合法的，会被修正成 0**
box-shadow: 0px 0px 0px 0px rgba(0,0,0,0.5) 
box-shadow: 0px 0px 20px 0px rgba(0,0,0,0.5) 
box-shadow: 0px 0px 50px 0px rgba(0,0,0,0.5) 

<br>

#### 5.spread
阴影扩展半径
**值为正，则整个阴影都延展扩大**
**值为负值是，则缩小**
**前提是存在阴影模糊半径**
box-shadow: 0px 0px 0px 0px rgba(0,0,0,0.5) 
box-shadow: 0px 0px 20px 20px rgba(0,0,0,0.5) 
box-shadow: 0px 0px 50px 50px rgba(0,0,0,0.5) 

<br>

#### 6.color
阴影的颜色
box-shadow: 0px 0px 20px 10px #67b3dd 
box-shadow: 0px 0px 20px 10px rgba(0,0,0,0.5) 

<br>

#### 7.position
**可选值，其默认的投影方式是外阴影**
**取其唯一值inset外阴影变成内阴影**
box-shadow: 0px 0px 20px 10px #67b3dd
 box-shadow: 0px 0px 20px 10px rgba(0,0,0,0.5) inset
