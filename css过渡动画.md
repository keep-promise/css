### 第一部分：CSS Transition
#### 1.1 基本用法
在CSS 3引入Transition（过渡）这个概念之前，**CSS是没有时间轴的。也就是说，所有的状态变化，都是即时完成**。

演示例子，当鼠标放置于缩略图之上，缩略图会迅速变大。注意，缩略图的变大是瞬间实现的。下面是代码，相当简单。

 ```js
 img{
     height:15px;
     width:15px;
 }

 img:hover{
     height: 450px;
     width: 450px;
 }
 ```
transition的作用在于，指定状态变化所需要的时间。

```js
img{
     transition: 1s;
 }
 ```
图片放大的过程需要1秒。

可以指定transition适用的属性，比如只适用于height。

```js
img{
     transition: 1s height;
 }
 ```
 只有height的变化需要1秒实现，其他变化（主要是width）依然瞬间实现。


<br>
<br>

#### 1.2 transition-delay
<br>
在同一行transition语句中，可以分别指定多个属性。

 ```js
 img{
     transition: 1s height, 1s width;
 }
 ```
height和width的变化是同时进行的，跟不指定它们没有差别。
<br>
让height先发生变化，等结束以后，再让width发生变化。实现这一点很容易，就是为width指定一个delay参数。

 ```js
 img{
     transition: 1s height, 1s 1s width;
 }
 ```

width在1秒之后，再开始变化，也就是延迟（delay）1秒。  
<br>
delay的真正意义在于，**它指定了动画发生的顺序，使得多个不同的transition可以连在一起，形成复杂效果。**


<br>
<br>

#### 1.3 transition-timing-function
transition的状态变化速度（又称timing function），默认不是匀速的，而是逐渐放慢，叫做ease。

```js
img{
     transition: 1s ease;
 }
 ```
   
 <br>
除了ease以外，还包括

**（1）linear：匀速**

**（2）ease-in：加速**

**（3）ease-out：减速**

**（4）cubic-bezier函数：自定义速度模式**

最后那个cubic-bezier，可以使用[工具网站](https://cubic-bezier.com/#0,.55,1,.08)来定制。

 ```js
 img{
     transition: 1s height cubic-bezier(.83,.97,.05,1.44);
 }
 ```
产生一个最后阶段放大过度、然后回缩的效果。


<br>
<br>

#### 1.4 transition的各项属性
transition的完整写法如下。

```js
img{
     transition: 1s 1s height ease;
}
 ```
这其实是一个简写形式，可以单独定义成各个属性。

```js
 img{
     transition-property: height;
     transition-duration: 1s;
     transition-delay: 1s;
     transition-timing-function: ease;
 }
 ```

<br>
<br>

#### 1.5 transition的使用注意
（1）目前，各大浏览器（包括IE 10）都已经支持无前缀的transition，所以transition已经可以很安全地不加浏览器前缀。

（2）不是所有的CSS属性都支持transition，[链接](https://projects.verou.me/animatable/)。

（3）transition需要明确知道，开始状态和结束状态的具体数值，才能计算出中间状态。比如，height从0px变化到100px，transition可以算出中间状态。但是，transition没法算出0px到auto的中间状态，也就是说，如果开始或结束的设置是height: auto，那么就不会产生动画效果。类似的情况还有，display: none到block，background: url(foo.jpg)到url(bar.jpg)等等。




1.6 transition的局限
transition的优点在于简单易用，但是它有几个很大的局限。

**（1）transition需要事件触发，所以没法在网页加载时自动发生。**

**（2）transition是一次性的，不能重复发生，除非一再触发。**

**（3）transition只能定义开始状态和结束状态，不能定义中间状态，也就是说只有两个状态。**

**（4）一条transition规则，只能定义一个属性的变化，不能涉及多个属性。**

**CSS Animation就是为了解决这些问题而提出的。**

了解CSS Animation请查看下一篇
