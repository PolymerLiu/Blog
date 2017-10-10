设置flex布局后，子元素的clear、float、vertical-align属性将失效
行内元素也可使用flex布局。display：inline-flex

#容器共有6个属性(规定属性值的第一个为默认值)
> #### flex-direction  //决定主轴方向 row | row-reverse | column | column-reverse
> #### flex-wrap  //定义如何换行   nowrap |　wrap | wrap-reverse
> #### flex-flow  //	flex-flow 属性是flex-direction属性和flex-wrap属性的简写形式，默认值为row nowrap

## justify-content 
> ### 定义项目在主轴上的对齐方式
#### justify-content：flex-start	（默认值）//	左对齐
#### justify-content：flex-end	//	右对齐
#### justify-content：center	//	居中
#### justify-content：space-between	//	两端对齐，项目之间的间隔都相等
#### justify-content：space-around	// 每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍



## align-items  
> ### 定义项目在交叉轴上如何对齐。
#### align-items:	stretch（默认值）	//	如果项目未设置高度或设为auto，将占满整个容器的高度
#### align-items:	flex-start	//	交叉轴的起点对齐。
#### align-items:	flex-end	// 交叉轴的终点对齐。
#### align-items:	center	//	交叉轴的中点对齐
#### align-items:	baseline	//	项目的第一行文字的基线对齐。


## align-content
> ### 属性定义了多根轴线的对齐方式(与align-items的主要区别)。如果项目只有一根轴线，该属性不起作用。
#### align-content：stretch（默认值）。轴线占满整个交叉轴
#### align-content：flex-start。与交叉轴的起点对齐。
#### align-content：flex-end。与交叉轴的终点对齐。
#### align-content：center。与交叉轴的中点对齐。
#### align-content：space-between。与交叉轴两端对齐，轴线之间的间隔平均分布。
#### align-content：space-around。每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍。

# 项目共有6个属性

## 4.1 order 
> ### 属性定义项目的排列顺序。`数值越小，排列越靠前`，默认为0。
```css
.item {
  order: 0 1;
}
```


## 4.2 flex-grow
> ### 属性定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大。
```css
.item {
  flex-grow: number; /* default 0 */
}
```
> ### 如果所有项目的`flex-grow属性都为1，则它们将等分剩余空间（如果有的话）`。如果一个项目的flex-grow属性为2，其他项目都为1，则前者占据的剩余空间将比其他项多一倍。


## 4.3 flex-shrink
> ### 属性定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小
```css
.item {
  flex-shrink: number; /* default 1 */
}
```
> ### 如果所有项目的flex-shrink属性都为1，当空间不足时，都将等比例缩小。如果一个项目的flex-shrink属性为0，其他项目都为1，则空间不足时，前者不缩小。


## 4.4 flex-basis属性
> ### 属性定义了在分配多余空间之前，项目占据的主轴空间（main size）。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为auto，即项目的本来大小。
```css
.item {
  flex-basis: auto; /* default auto */
}
```
> ### 它可以设为跟width或height属性一样的值（比如350px），则项目将占据固定空间。


## 4.5 flex属性
> ### flex属性是flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto。后两个属性可选。
```css
.item {
  flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]
}
```
> * 该属性有两个快捷值：auto (1 1 auto) 和 none (0 0 auto)。
> * 建议优先使用这个属性，而不是单独写三个分离的属性，因为浏览器会推算相关值。



## 4.6 align-self  * 较align-items多了一个 auto，其他都一样
> ### 属性允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch。
```css
.item {
  align-self:  auto  flex-start  flex-end  center  baseline  stretch;
}
```




	