## 1.介绍js的基本数据类型
* Number、String、Boolean、Undefined、Null

## 2.js有哪些内置对象？
* 数据封装类对象：Object、Array、Boolean、Number 和 String
* 其他对象：Function、Arguments、Math、Date、RegExp、Error

## 3.this对象的理解
* this总是指向函数的直接调用者（而非间接调用者）；
* 如果有new关键字，this指向new出来的那个对象；
* 在事件中，this指向触发这个事件的对象，特殊的是，IE中的attachEvent中的this总是指向全局对象Window

## 4.DOM怎样添加、移除、移动、复制、创建和查找节点
* createDocumentFragment()    //创建一个DOM片段
* createElement()   //创建一个具体的元素
* createTextNode()   //创建一个文本节点
* 
* appendChild()   //添加
* removeChild()   //移除
* replaceChild()   //替换
* insertBefore() //在已有的子节点前插入一个新的子节点
* 
* getElementsByTagName()    //通过标签名称
* getElementsByName()    //通过元素的Name属性的值(IE容错能力较强，会得到一个数组，其中包括id等于name值的)
* getElementById()    //通过元素Id，唯一性

## 5.null和undefined的区别？
* null是一个表示"无"的对象，转为数值时为0；undefined是一个表示"无"的原始值，转为数值时为NaN。
* undefined：
	* （1）变量被声明了，但没有赋值时，就等于undefined。
	* （2) 调用函数时，应该提供的参数没有提供，该参数等于undefined。
	* （3）对象没有赋值的属性，该属性的值为undefined。
	* （4）函数没有返回值时，默认返回undefined。
* null：
	* （1） 作为函数的参数，表示该函数的参数不是对象。
	* （2） 作为对象原型链的终点

## 6.new操作符具体干了什么呢?
* （1）创建一个空对象，并且 this 变量引用该对象，同时还继承了该函数的原型。
* （2）属性和方法被加入到 this 引用的对象中。
* （3）新创建的对象由 this 所引用，并且最后隐式的返回 this 。
## 
## 
## 
## 
## 
## 
## 
