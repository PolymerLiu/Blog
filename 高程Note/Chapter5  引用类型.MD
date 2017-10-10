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
> ### 由于函数是对象，因此函数名实际上也是一个指向函数对象的指针，不会与某个函数绑定.由于函数名仅仅是指向函数的指针，因此函数名与包含对象指针的其他变量没有什么不同。换句话说，一个函数可能会有多个名字
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
   ```javascript3
    var sum = new Function("num1", "num2", "return num1 + num2"); 
```

