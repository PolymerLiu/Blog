## javascript 代码运行分俩个阶段
* 预解析 ---把所有函数定义(function () {})提前,所有的变量声明提前，变量的赋值不提前
* 执行 --- 从上到下执行  (setTimeout,setInterval, ajax中的回掉函数，事件中的函数需要触发执行)
 
## for 循环之闭包


### 所有输出结果都为3版本
```javascript
var data = []; 
for(var i = 0, i < 3, i++){
    data[i] = function(){
        console.log(i);     //  这里只是声明了一个 函数，并未调用，无法使用for里边的i。。。。到for外边调用时，此时i已经变为3
    }
}
// for 循环完毕之后，i的值变为3（为全局变量）
data[0]();   //  3     data[0]=function(){console.log(i)  此i为for循环之外的i}
data[1]();   //  3
data[2]();   //  3
```

### 输出结果依次为0,1,2版本
```javascript
var data = [];
for(var i = 0, i<3, i++){
    data[i] = (function(k) {


        return function () {
            console.log(k);
        }



    }) (i);  // 此  i  为立即执行函数的的实际参数，，并把其值赋值给形式参数  k
}
// for 循环完毕之后，i的值变为3（为全局变量）
data[0]();   //  0
data[1]();   //  1
data[2]();   //  2
```



## 初识闭包
```javascript
(function() {
    /**闭包详解*/
    function fun() {
        var num = 10; // 让fun以外的函数   使用num(变量)的值      这样就可以创建闭包
        console.log(num);
    }



    function outFun() { //本函数执行结果是返回inFun函数的函数体，即function inFun()  {console.log(num);}
        var num = 10;

        function inFun() {
            console.log(num);
        }
        return inFun; //(此句为闭包核心)  该行代码作为  本函数的执行结果    因为函数不调用是不会执行的
    }

    //赋值运算符(=)  是从右往左计算的
    var demo = outFun(); //  本段代码就是  把调用outFun函数的结果(返回inFun函数的函数体)  赋值给demo
    //    outFun()    返回的是   function inFun()  {console.log(num);}
    //  等同于    var demo = function inFun() {console.log(num);}

    var demo = function inFun() {
            console.log(num);
        } //  把一个函数赋值给一个变量，那么   该变量就成为一个函数

    demo(); //  接下来就调用这个函数


    /**
     *如上 demo这个函数   使用outFun函数内的变量   这一过程就形成了一个闭包
     */



    //其实每一个 函数都是  一个小闭包   (当函数引用全局变量的时候)
    var key = 10;

    function one() {
        console.log(key);
    }



    /**闭包实例*/
    function outerFun() {
        var a = 0; ///每次调用 outerFun函数    a都会被清零;
        function innerFun() {
            a++;
            alert(a);
        }
        return innerFun;
    }

    var obj = outerFun();
    obj();   obj(); //   1   2

    var obj2 = outerFun();
    obj2();  obj2(); //  1   2

    /**闭包原理 ：
     * 如果想要使用某个函数内的变量，直接是无法使用的(因为有作用域的存在)。
     * 但是我们可以曲线救国，，通过在该函数内内置一个函数，，然后再把内置函数return出来，
     * 然后在外面调用这个内置函数
     */
})();
```
### 闭包优点：不会产生全局变量，实现属性私有化
### 闭包缺点：闭包中的数据会常驻内存，在不用的时候要删掉否则会导致内存溢出

# 对象

## 基本数据类型
* number string boolean null undefined (object 非基本数据类型)
* 基本数据类型不能自定义属性和方法，，而对象可以

## 声明对象
* var obi = new Object();
* var obj = {};    字面量式;  推荐

## 自定义对象的属性、方法
* var obj = {};

* obj.age = 55;     //自定义属性
* obj.age;     //调用属性

* obj.showAge = function () {alert(55)};    //自定义方法
* obj.showAge();   //调用方法

## 封装对象
```javascript
(function (){
    function person(name, age) {
        var obj={};
        obj.name=name;
        obj.age=age;
        obj.showName= function () {
            console.log(""+name);
        }
        obj.showAge= function () {
            console.log(""+age);
        }
        return obj;   // 最后一定要把这个对象返回
    }

    var xiaoming = person("小明",12);  //利用person函数来创建一个小明对象
    console.log(xiaoming.name);   //调用xiaoming的name属性
    console.log(xiaoming.age);
    xiaoming.showAge();     //调用xiaoming的showAge()方法
}) ();
```



## this new 
```javascript

