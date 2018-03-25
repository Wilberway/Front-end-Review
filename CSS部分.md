CSS部分

1. CSS盒模型

   标准盒模型： 宽度 = 内容的宽度（content) + border + padding + margin

   低版本IE盒模型：宽度 = 内容的宽度(content + border +padding) + margin

2. box-sizing属性

   默认为content-box

   content-box: W3C的标准盒模型，设置元素的宽高为content部分的宽高

   border-box: IE传统盒模型，设置元素的宽高为border + padding + content部分的宽高

3. CSS选择器的优先级

   元素选择器 1

   class选择符 10

   id选择符 100

   元素标签 1000

   1) !important声明的样式优先级最高，如果冲突再进行计算。

   2) 如果优先级相同，则选择最后出现的样式。

   3) 继承得到的优先级最低。

4. CSS的伪类和伪元素

   伪类：:nth_child :checked :active :hover...

   伪元素： :before :after :first-line...

5. CSS3有哪些新特性：

   1) RGBA和透明度

   2) background-image background-origin(content-box/padding-box/border-box) background-size background-repeat

   3) word-wrap(对长的不可分割的单词换行) 

   4) 文字阴影 text-shadow: 5px 5px 5px #FF0000 (水平阴影，垂直阴影，模糊距离，阴影颜色)

   5) font-face属性：定义自己的字体

   6) 圆角 border-radius

   7) 边框图片 border-image: url(border.png) 30 30 round

   8) 盒阴影 box-shadow: 10px 10px 5px #888888

   9) 媒体查询 定义两套css，当视口尺寸变化时会采用不同的属性

6. CSS3的弹性布局(flexbox)

   提供一种更高效的方式对容器中的条目进行布局、对其和分配空间。再传统的布局方式中，block布局是把块在垂直方向从上到下依次排列，inline布局是在水平方向排列。

7. CSS常见的兼容性问题

   1) 不同了浏览器的标签默认的padding和margin不一样。

   2) IE6双边距bug：块属性标签float后，又有横行的margin情况下，在IE6显示margin比设置的大。hack: display:inline; 将其转化为行内属性。

   3) 渐进识别的方式(CSS hack)

   ```css
   {
     background-color: #f1ee18;/*所有识别*/
     .background-color: #00deff;/*IE6、7、8识别*/
     +background-color: #a200ff:/*IE6、7识别*/
     _background-color: #1e0bd1:/*IE6识别*/
   }
   ```

   4) 设置较小高度标签（一般小于10px），在IE6、7中高度超出自己设置的高度。hack：给超出自己高度的标签设置overflow: hidden; 或者设置行高line-height小于你设置的高度。

   5) IE可以使用常规属性方法获取标签的自定义属性，也可以使用getAttribute()获取自定义属性。Firefox下，只能通过getAttribute()获取自定义属性。

   6) Chrome中文界面下默认会将小于12px的文本强制按照12px显示，可以通过加入css属性-webkit-text-size-adjust: none;解决

   7) 超链接访问过后hover样式就不出现了，被点击访问过的超链接样式不在具有hover和active了。解决方法是改变CSS属性的排列顺序： L-V-H-A(love hate): a:link{} a:visited{} a:hover{} a:active{}