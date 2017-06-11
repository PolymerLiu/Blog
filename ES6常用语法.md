# ES6常见语法

# let  
#### ES5只有全局作用域和函数作用域，没有块级作用域，这带来很多不合理的场景。

#### 第一种场景就是你现在看到的内层变量覆盖外层变量。而let则实际上为JavaScript新增了块级作用域。用它所声明的变量，只在let命令所在的代码块内有效。

```javascript
let name = 'zach'

while (true) {
    let name = 'obama'
    console.log(name)  //obama
    break
}

console.log(name)  //zach
```


#### 第二个var带来的不合理场景就是用来计数的循环变量泄露为全局变量

```javascript
var a = [];
for (var i = 0; i < 10; i++) {
  a[i] = function () {    
    console.log(i);
  };
}
a[6](); // 10
```

* 上面代码中，变量i是var声明的，在全局范围内都有效。所以每一次循环，新的i值都会覆盖旧值，导致最后输出的是最后一轮的i的值。而使用let则不会出现这个问题。

```javascript
var a = [];
for (let i = 0; i < 10; i++) {
  a[i] = function () {    
    console.log(i);
  };
}
a[6](); // 6
```

#### 再来看一个更常见的例子，了解下如果不用ES6，而用闭包如何解决这个问题。

```javascript
var clickBoxs = document.querySelectorAll('.clickBox')
for (var i = 0; i < clickBoxs.length; i++){
    clickBoxs[i].onclick = function(){        
        console.log(i)
    }
}
```

* 我们本来希望的是点击不同的clickBox，显示不同的i，但事实是无论我们点击哪个clickBox，输出的都是5。下面我们来看下，如何用闭包搞定它。

```javascript
function iteratorFactory(i){
    var onclick = function(e){
        console.log(i)
    }    
    return onclick;
}
var clickBoxs = document.querySelectorAll('.clickBox')
for (var i = 0; i < clickBoxs.length; i++){
    clickBoxs[i].onclick = iteratorFactory(i)
}
```

# const
#### const也用来声明变量，但是声明的是常量。一旦声明，常量的值就不能改变。
* 当我们尝试去改变用const声明的常量时，浏览器就会报错。const有一个很好的应用场景，就是当我们引用第三方库的时声明的变量，用const来声明可以避免未来不小心重命名而导致出现bug：
* const monent = require('moment')

