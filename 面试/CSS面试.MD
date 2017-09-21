## 1.介绍一下标准的CSS的盒子模型？低版本IE的盒子模型有什么不同的？
* （1）有两种， IE 盒子模型、W3C 盒子模型。
* （2）盒模型： 内容(content)、填充(padding)、边界(margin)、 边框(border)。
* （3）区  别： IE的content部分把 border 和 padding计算了进去。

## 2.CSS优先级算法如何计算？
* 优先级就近原则，同权重情况下样式定义最近者为准;
* 载入样式以最后载入的定位为准;
* 优先级为:
* !important >  id > class > tag
* important比内联优先级高(style)

## 3.为什么要使用CSS sprites
* CSS Sprites其实就是把网页中一些背景图片整合到一张图片文件中，再利用CSS的“background-image”，“background-position”的组合进行背景定位，这样可以减少很多图片请求的开销，因为请求耗时比较长；请求虽然可以并发，但是如果请求太多会给服务器增加很大的压力。。

## 4.display:none和visibility:hidden的区别？
* display:none  隐藏对应的元素，在文档布局中不再给它分配空间，它各边的元素会合拢，就当他从来不存在。
* visibility:hidden  隐藏对应的元素，但是在文档布局中仍保留原来的空间。

## 5.position的absolute与fixed区别
* absolute浮动定位是相对于父级中设置position为relative或者absolute最近的父级元素
* fixed浮动定位是相对于浏览器视窗的

## 6.IE 8以下版本的浏览器中的盒模型有什么不同？
* IE8以下浏览器的盒模型中定义的元素的宽高不包括内边距和边框