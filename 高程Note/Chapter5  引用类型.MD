# 5.1 object 类型
> ##创建Object 实例的方式有两种。

###第一种是使用new 操作符后跟Object 构造函数
```javascript
var person = new Object();
person.name = "Nicholas";
person.age = 29;
```

###另一种方式是使用对象字面量表示法
```javascript
var person = {
name : "Nicholas",
age : 29
};
```
* 在这个例子中，左边的花括号（{）表示对象字面量的开始，因为它出现在了表达式上下文（expression context）中。ECMAScript中的表达式上下文指的是能够返回一个值（表达式）。赋值操作符表示后面是一个值，所以左花括号在这里表示一个表达式的开始。同样的花括号，如果出现在一个语句上下文（statement context）中，例如跟在if 语句条件的后面，则表示一个语句块的开始。




# 5.2 Array 类型
> ##创建Array 实例的方式有两种。
### 第一种是使用Array 构造函数
```javascript
var colors = new Array();
```
###创建数组的第二种基本方式是使用数组字面量表示法
```javascript
var colors = ["red", "blue", "green"]; // 创建一个包含3 个字符串的数组
var names = []; // 创建一个空数组
var values = [1,2,]; // 不要这样！这样会创建一个包含2 或3 项的数组
var options = [,,,,,]; // 不要这样！这样会创建一个包含5 或6 项的数组
```
## 与对象一样，在使用数组字面量表示法时，也不会调用Array 构造函数
## 5.2.1 检测数组
### instanceof
* value instanceof Array // 仅针对一个全局作用域而言 （如果value为Array，返回true）
### Array.isArray()
* Array.isArray(value)  //  这个方法的目的是最终确定某个值到底是不是数组，而不管它是在哪个全局执行环境中创建的。（如果value为Array，返回true）


## 5.2.2 转换方法
### 所有对象都具有toLocaleString()、toString()和valueOf()方法
```javascript
var colors = ["red", "blue", "green"]; // 创建一个包含3 个字符串的数组
console.log(colors.toString()); // "red,blue,green"
console.log(colors.valueOf()); //  ["red", "blue", "green"]
alert(colors); // ""red,blue,green    由于alert()要接收字符串参数，所以它会在后台调用toString()方法，由此会得到与直接调用toString()方法相同的结果。
```
### `数组继承的toLocaleString()、toString()和valueOf()方法，在默认情况下都会以逗号分隔的字符串的形式返回数组项`。而如果使用join()方法，
则可以使用不同的分隔符来构建这个字符串。join()方法只接收一个参数，即用作分隔符的字符串，然后返回包含所有数组项的字符串。请看下面的例子
```javascript
var colors = ["red", "green", "blue"];
alert(colors.join(",")); //red,green,blue
alert(colors.join("||")); //red||green||blue
```
## 5.2.6 操作方法
### concat()方法
* 连接两个或更多的数组，并返回结果。 `该方法创建原数组的一个副本，并不会改变原数组`
```javascript
var colors = ["red", "green", "blue"]; 
var colors2 = colors.concat("yellow", ["black", "brown"]); //  ["red", "green", "blue", "yellow", "black", "brown"]
var colors3 = colors.concat(); // ["red", "green", "blue"] 
```
### slice()
* 从某个已有的数组返回选定的元素
```javascript
var colors = ["red", "green", "blue", "yellow", "purple"];
var colors2 = colors.slice(1); // ["green", "blue", "yellow", "purple"]  从第一项到末尾
var colors3 = colors.slice(1,4) // ["green", "blue", "yellow"] 起始项到结束项，但不包含结束项
// 如果参数有负数，则参数加上数组长度。eg array.length=5, slice(-2,-1)与slice(3,4) 返回一样
// 如果结束位置小于起始位置，则返回空数组。
```




# 5.3 Date 类型
### 5.3.2 日期格式化方法
#### Date 类型还有一些专门用于将日期格式化为字符串的方法，这些方法如下。
 toDateString()——以特定于实现的格式显示星期几、月、日和年；
 
 toTimeString()——以特定于实现的格式显示时、分、秒和时区；
 
 toLocaleDateString()——以特定于地区的格式显示星期几、月、日和年；
 
 toLocaleTimeString()——以特定于实现的格式显示时、分、秒；
 
 toUTCString()——以特定于实现的格式完整的UTC 日期。
 
 与toLocaleString()和toString()方法一样，以上这些字符串格式方法的输出也是因浏览器而异的，因此没有哪一个方法能够用来在用户界面中显示一致的日期信息。





# 5.4 RegExp 类型
# 5.5 Function 类型 (无重载，即后声明的函数会覆盖前面声明的)
> ### 由于函数是对象，因此函数名实际上也是一个指向函数对象的指针，'不会与某个函数绑定.由于函数名仅仅是指向函数的指针'，因此函数名与包含对象指针的其他变量没有什么不同。换句话说，一个函数可能会有多个名字
```javascript
function sum(num1, num2){
    return num1 + num2;
}
alert(sum(10,10)); //20
var anotherSum = sum; // 使用不带圆括号的函数名是访问函数指针，而非调用函数。此时，anotherSum 和sum 就都指向了同一个函数
alert(anotherSum(10,10)); //20
sum = null;     // 将sum 设置为null，让它与函数“断绝关系”，但仍然可以正常调用anotherSum()。
alert(anotherSum(10,10)); //20
```

## 有三种定义函数的方法
   ###function关键字法（函数声明法）// 这种方法声明的函数会被解析器优先读取，使其在任何地方都可被调用
   ```javascript
    function sum (num1, num2) {
        return num1 + num2;
    }
```
   ###函数表达式法 // 表达式法则要等解析到此处时才生效    ,在执行到函数所在的语句之前，变量sum 中不会保存有对函数的引用
   ```javascript
    var sum = function(num1, num2){
        return num1 + num2;
    };
```
   ###Function 构造函数法    （不推荐）
   ```javascript
    var sum = new Function("num1", "num2", "return num1 + num2"); 
```
## 5.5.3 作为值的函数
```javascript
function createComparisonFunction(propertyName) {
    return function(object1, object2){
        var value1 = object1[propertyName];
        var value2 = object2[propertyName];
        if (value1 < value2){
        return -1;
        } else if (value1 > value2){
        return 1;
        } else {
        return 0;
        }
    };
}

var data = [{name: "Zachary", age: 28}, {name: "Nicholas", age: 29}];
data.sort(createComparisonFunction("name"));
alert(data[0].name); //Nicholas
data.sort(createComparisonFunction("age"));
alert(data[0].name); //Zachary


```
## 5.5.4 函数内部属性 (在函数内部,有两个特殊的对象：arguments 和this)
   ### arguments 是一个类数组对象，包含着传入函数中的所有参数    将arguments对象转化为标准的数组   var args = Array.prototype.slice.call(arguments);  
   > #### (该对象还有一个名叫callee 的属性，该属性是一个指针，指向拥有这个arguments 对象的函数)    ！！！arguments.callee 是获取当前调用函数的本体  （严格模式，arguments.callee 会导致错误。）
   > #### 当函数被调用时，它的arguments.callee对象就会指向自身，也就是一个对自己的引用。由于arguments在函数被调用时才有效，因此arguments.callee在函数未调用时是不存在的（即null.callee），且解引用它会产生异常
```javascript

function factorial(num){
    if (num <=1) {
    return 1;
    } else {
    return num * factorial(num-1)
    }
}

//解耦合版
function factorial(num){
    if (num <=1) {
    return 1;
    } else {
    return num * arguments.callee(num-1)
    }
}
```

### this对象 ----this引用的是函数执行的环境对象——或者也可以说是this 值（当在网页的全局作用域中调用函数时，this 对象引用的就是window）。

```javascript
window.color = "red";
var o = { color: "blue" };
function sayColor(){
alert(this.color);  //此处的this指向还未确定，其指向调用该函数的对象
}
sayColor(); //"red"     //  其等价于 window.sayColor()  即window对象调用了该函数
o.sayColor = sayColor;  //把sayColor函数赋值给对象O   。note！！！函数的名字仅仅是一个包含指针的变量而已。因此，即使是在不同的环境中执行，全局的sayColor()函数与o.sayColor()指向的仍然是同一个函数。
o.sayColor(); //"blue"  // O对象调用了改函数  ，所以this指向O对象
```

### 另一个函数对象的属性：caller   这个属性中保存着调用当前函数的函数的引用，如果是在全局作用域中调用当前函数，它的值为null
   > 在一个函数调用另一个函数时，被调用函数会自动生成一个caller属性，指向调用它的函数对象。如果该函数当前未被调用，或并非被其他函数调用，则caller为null。
```javascript
function outer(){
    inner();    
}
function inner(){
    alert(inner.caller)     //  于下方语句是等效的，下方解耦合更彻底
    alert(arguments.callee.caller)  //  arguments.callee
}
outer();    //  显示的是outer() 函数的源码
inner();    //  结果为null
```



## 5.5.5 函数属性和方法 (属性：length 和prototype  方法：apply()和call( )
   ### length属性 其值为形式参数的个数
```javascript
function sum(num1, num2){
return num1 + num2;
}
alert(sum.length); //2
```

   ### prototype属性
   > #### 对于ECMAScript 中的引用类型而言，prototype 是保存它们所有实例方法的真正所在。
   > #### 换句话说，诸如toString()和valueOf()等方法实际上都保存在prototype 名下，只不过是通过各自对象的实例访问罢了。
   > #### 在创建自定义引用类型以及实现继承时，prototype 属性的作用是极为重要的（第6 章将详细介绍）。
   > #### 在ECMAScript 5 中，prototype 属性是不可枚举的，因此使用for-in 无法发现。
   
   ### apply()和call() 方法    //  这两个方法的用途都是在特定的作用域中调用函数，实际上等于设置函数体内this 对象的值
   > 以上两方法不同之处在于，传入的第二个参数不一样，其取决于传递给函数的数据类型，对象用apply，否则call
   ```javascript
function sum(num1, num2){
    return num1 + num2;
}
function callSum1(num1, num2){  //callSum1()在执行sum()函数时传入了this 作为this 值（因为是在全局作用域中调用的，所以传入的就是window 对象）和arguments 对象
    return sum.apply(this, arguments); // 传入arguments 对象
}
function callSum2(num1, num2){
    return sum.apply(this, [num1, num2]); // 传入数组
}
alert(callSum1(10,10)); //20
alert(callSum2(10,10)); //20
```

```javascript
function sum(num1, num2){
    return num1 + num2;
}
function callSum(num1, num2){
    return sum.call(this, num1, num2);
}
alert(callSum(10,10)); //20
```

### 传递参数并非apply()和call()真正的用武之地；它们真正强大的地方是能够扩充函数赖以运行的作用域
```javascript
window.color = "red";
var o = { color: "blue" };
function sayColor(){
    alert(this.color);
}
sayColor(); //red
sayColor.call(this); //red  //  显式地在全局作用域中调用函数的方式，结果当然都会显示"red"
sayColor.call(window); //red
sayColor.call(o); //blue    //此时函数体内的this 对象指向了O对象，

```
> #### 以上4种方法都是在调用函数，后三种通过调用     函数的call（）方法     改变函数的执行环境

> #### 使用call()（或apply()）来扩充作用域的最大好处，就是对象不需要与方法有任何耦合关系。
> #### 在前面例子的第一个版本中，我们是先将sayColor()函数放到了对象O中（O.sayColor = sayColor;），然后再通过O 来调用它的；而在这里重写的例子中，就不需要先前那个多余的步骤了。

### bind()方法。这个方法会创建一个函数的实例，其`this 值会被绑定到传给bind()函数的值`。例如：

```javascript
window.color = "red";
var o = { color: "blue" };
function sayColor(){
    alert(this.color);
}
var objectSayColor = sayColor.bind(o);
objectSayColor(); //blue
```
> #### 在这里，sayColor()调用bind()并传入对象o，创建了objectSayColor()函数。
> #### object-SayColor()函数的this 值等于o，因此即使是在全局作用域中调用这个函数，也会看到"blue"。这种技巧的优点请参考第22 章。

### toLocaleString()和toString()方法
   #### 每个函数继承的toLocaleString()和toString()方法始终都返回函数的代码

























