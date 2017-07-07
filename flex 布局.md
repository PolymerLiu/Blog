设置flex布局后，子元素的clear、float、vertical-align属性将失效
行内元素也可使用flex布局。display：inline-flex

#共有6个属性(规定属性值的第一个为默认值)
* flex-direction  //决定主轴方向 row | row-reverse | column | column-reverse
* flex-wrap  //定义如何换行   nowrap |　wrap | wrap-reverse
* flex-flow  //	flex-flow 属性是flex-direction属性和flex-wrap属性的简写形式，默认值为row nowrap
* justify-content  //	定义项目在主轴上的对齐方式
	* justify-content：flex-start	//	左对齐
	* justify-content：flex-end	//	右对齐
	* justify-content：center	//	居中
	* justify-content：space-between	//	两端对齐，项目之间的间隔都相等
	* justify-content：space-around	// 每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍



* align-items  //	定义项目在交叉轴上如何对齐。
	* align-items:	stretch（默认值）	//	如果项目未设置高度或设为auto，将占满整个容器的高度
	* align-items:	flex-start	//	交叉轴的起点对齐。
	* align-items:	flex-end	// 交叉轴的终点对齐。
	* align-items:	center	//	交叉轴的中点对齐
	* align-items:	baseline	//	项目的第一行文字的基线对齐。


* align-content  //	属性定义了多根轴线的对齐方式(与align-items的主要区别)。如果项目只有一根轴线，该属性不起作用。
	* align-content：stretch（默认值）。轴线占满整个交叉轴
	* align-content：flex-start。与交叉轴的起点对齐。
	* align-content：flex-end。与交叉轴的终点对齐。
	* align-content：center。与交叉轴的中点对齐。
	* align-content：space-between。与交叉轴两端对齐，轴线之间的间隔平均分布。
	* align-content：space-around。每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍。


	