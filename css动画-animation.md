## CSS Animation
<br>

#### 2.1 基本用法

<br>
CSS Animation需要指定动画一个周期持续的时间，动画效果的名称。

 ```js
 div:hover {
   animation: 1s rainbow;
 }
 
 @keyframes rainbow {
   0% { background: #c00; }
   50% { background: orange; }
   100% { background: yellowgreen; }
 }
 
 ```
 
当鼠标悬停在div元素上时，会产生名为rainbow的动画效果，持续时间为1秒。需要用keyframes关键字，定义rainbow效果。

rainbow效果一共有三个状态，分别为起始（0%）、中点（50%）和结束（100%）。如果有需要，完全可以插入更多状态。

**默认情况下，动画只播放一次。infinite关键字，可以让动画无限次播放**。

```js
div:hover {
   animation: 1s rainbow infinite;
}
```
 
可以指定动画具体播放的次数，比如3次。

 ```js
 div:hover {
   animation: 1s rainbow 3;
 }
 ```

<br>
<br>

#### 2.2 animation-fill-mode

动画结束以后，会立即从结束状态跳回到起始状态。如果想让动画保持在结束状态，需要使用**animation-fill-mode**属性。

 ```js
 div:hover {
   animation: 1s rainbow forwards;
 }
 ```
**forwards表示让动画停留在结束状态。**

animation-fill-mode还可以使用下列值。

**（1）none：默认值，回到动画没开始时的状态。**

**（2）backwards：让动画回到第一帧的状态。**

**（3）both: 根据animation-direction（见后）轮流应用forwards和backwards规则。**



<br>
<br>

#### 2.3 animation-direction

动画循环播放时，**每次都是从结束状态跳回到起始状态**，再开始播放。animation-direction属性，可以改变这种行为。

<br>

如何使用animation-direction

 ```js
 @keyframes rainbow {
   0% { background-color: yellow; }
   100% { background: blue; }
 }
 ```
默认情况是，**animation-direction等于normal。**

 ```js
 div:hover {
   animation: 1s rainbow 3 normal;
 }
 ```
 
可以等于取alternate、reverse、alternate-reverse等值。


简单说，**animation-direction指定了动画播放的方向**，最常用的值是normal和reverse。浏览器对其他值的支持情况不佳，应该慎用。


<br>
<br>

#### 2.4 animation的各项属性

animation简写形式。

```js
div:hover {
   animation: 1s 1s rainbow linear 3 forwards normal;
 }
 ```
可以分解成各个单独的属性。

```js
div:hover {
   animation-name: rainbow;
   animation-duration: 1s;
   animation-timing-function: linear;
   animation-delay: 1s;
   animation-fill-mode: forwards;
   animation-direction: normal;
   animation-iteration-count: 3;
 }
```

<br>
<br>

#### 2.5 keyframes的写法
keyframes关键字用来定义动画的各个状态，它的写法相当自由。

 ```
 @keyframes rainbow {
   0% { background: #c00 }
   50% { background: orange }
   100% { background: yellowgreen }
 }
 ```
 
**0%可以用from代表，100%可以用to代表**

 ```
@keyframes rainbow {
   from { background: #c00 }
   50% { background: orange }
   to { background: yellowgreen }
}
```
如果省略某个状态，浏览器会自动推算中间状态，所以下面都是合法的写法。

```
@keyframes rainbow {
   50% { background: orange }
   to { background: yellowgreen }
 }

 @keyframes rainbow {
   to { background: yellowgreen }
 }
 ```
 
甚至，可以把多个状态写在一行。

 ```
 @keyframes pound {
   from，to { transform: none; }
   50% { transform: scale(1.2); }
 }
 ```
 
浏览器从一个状态向另一个状态过渡，是平滑过渡。steps 函数可以实现分步过渡。

```js
div:hover {
   animation: 1s rainbow infinite steps(10);
}
```

<br>
<br>

#### 2.6 animation-play-state

动画播放过程中，会突然停止。默认行为是跳回到动画的开始状态。

上面动画中，如果鼠标移走，色块立刻回到动画开始状态。

如果想让动画保持突然终止时的状态，就要使用animation-play-state属性。

```js
div {
     animation: spin 1s linear infinite;
     animation-play-state: paused;
 }

 div:hover {
   animation-play-state: running;
 }
``` 
上面的代码指定，没有鼠标没有悬停时，动画状态是暂停；一旦悬停，动画状态改为继续播放。




2.7 浏览器前缀
目前，IE 10和Firefox（>= 16）支持没有前缀的animation，而chrome不支持，所以必须使用webkit前缀。

也就是说，实际运用中，代码必须写成下面的样子。

 div:hover {
   -webkit-animation: 1s rainbow;
   animation: 1s rainbow;  
 }

 @-webkit-keyframes rainbow {
   0% { background: #c00; }
   50% { background: orange; }
   100% { background: yellowgreen; }
 }

 @keyframes rainbow {
   0% { background: #c00; }
   50% { background: orange; }
   100% { background: yellowgreen; }
 }



-end-

原文地址: http://www.ruanyifeng.com/blog/2014/02/css_transition_and_animation.html
