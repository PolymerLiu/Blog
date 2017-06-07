## 初次认识闭包
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