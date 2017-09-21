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

## 7.JSON 的了解？
* JSON(JavaScript Object Notation) 是一种轻量级的数据交换格式。它是基于JavaScript的一个子集。数据格式简单, 易于读写, 占用带宽小。
* 格式：采用键值对，例如：{'age':'12', 'name':'back'}

## 8.call() 和 apply() 的区别和作用？
* apply()函数有两个参数：第一个参数是上下文，第二个参数是参数组成的数组。如果上下文是null，则使用全局对象代替。
* 如：function.apply(this,[1,2,3]);
* call()的第一个参数是上下文，后续是实例传入的参数序列。
* 如：function.call(this,1,2,3);

# 第二章节
## 1.JS数组去重(三种方法)
```javascript
<font size="3">Array.prototype.unique1 = function () {
  var n = []; //一个新的临时数组
  for (var i = 0; i < this.length; i++) //遍历当前数组
  {
    //如果当前数组的第i已经保存进了临时数组，那么跳过，
    //否则把当前项push到临时数组里面
    if (n.indexOf(this[i]) == -1) n.push(this[i]);
  }
  return n;
}

Array.prototype.unique2 = function()
{
    var n = {},r=[]; //n为hash表，r为临时数组
    for(var i = 0; i < this.length; i++) //遍历当前数组
    {
        if (!n[this[i]]) //如果hash表中没有当前项
        {
            n[this[i]] = true; //存入hash表
            r.push(this[i]); //把当前数组的当前项push到临时数组里面
        }
    }
    return r;
}

Array.prototype.unique3 = function()
{
    var n = [this[0]]; //结果数组
    for(var i = 1; i < this.length; i++) //从第二项开始遍历
    {
        //如果当前数组的第i项在当前数组中第一次出现的位置不是i，
        //那么表示第i项是重复的，忽略掉。否则存入结果数组
        if (this.indexOf(this[i]) == i) n.push(this[i]);
    }
    return n;
}</font>
```

## 2.js操作获取和设置cookie
```javascript
<font size="3">//创建cookie
function setCookie(name, value, expires, path, domain, secure) {
    var cookieText = encodeURIComponent(name) + '=' + encodeURIComponent(value);
    if (expires instanceof Date) {
        cookieText += '; expires=' + expires;
    }
    if (path) {
        cookieText += '; expires=' + expires;
    }
    if (domain) {
        cookieText += '; domain=' + domain;
    }
    if (secure) {
        cookieText += '; secure';
    }
    document.cookie = cookieText;
}

//获取cookie
function getCookie(name) {
    var cookieName = encodeURIComponent(name) + '=';
    var cookieStart = document.cookie.indexOf(cookieName);
    var cookieValue = null;
    if (cookieStart > -1) {
        var cookieEnd = document.cookie.indexOf(';', cookieStart);
        if (cookieEnd == -1) {
            cookieEnd = document.cookie.length;
        }
        cookieValue = decodeURIComponent(document.cookie.substring(cookieStart + cookieName.length, cookieEnd));
    }
    return cookieValue;
}

//删除cookie
function unsetCookie(name) {
    document.cookie = name + "= ; expires=" + new Date(0);
}</font>
```

## 3.ajax 有那些优缺点?如何解决跨域问题?
* 优点：
	* （1）通过异步模式，提升了用户体验.
	* （2）优化了浏览器和服务器之间的传输，减少不必要的数据往返，减少了带宽占用.
	* （3）Ajax在客户端运行，承担了一部分本来由服务器承担的工作，减少了大用户量下的服务器负载。
	* （4）Ajax可以实现动态不刷新（局部刷新）
* 缺点：
	* （1）安全问题 AJAX暴露了与服务器交互的细节。
	* （2）对搜索引擎的支持比较弱。
	* （3）不容易调试。
* jsonp、 iframe、window.name、window.postMessage、服务器上设置代理页面。

## 4.JavaScript原型，原型链 ? 有什么特点？
* （1）原型对象也是普通的对象，是对象一个自带隐式的 __proto__ 属性，原型也有可能有自己的原型，如果一个原型对象的原型不为null的话，我们就称之为原型链。
* （2）原型链是由一些用来继承和共享属性的对象组成的（有限的）对象链。

## 5.GET和POST的区别，何时使用POST？
* GET：一般用于信息获取，使用URL传递参数，对所发送信息的数量也有限制，一般在2000个字符
* POST：一般用于修改服务器上的资源，对所发送的信息没有限制。
* GET方式需要使用Request.QueryString来取得变量的值，而POST方式通过Request.Form来获取变量的值，也就是说Get是通过地址栏来传值，而Post是通过提交表单来传值。
* 然而，在以下情况中，请使用 POST 请求：
	* 无法使用缓存文件（更新服务器上的文件或数据库）
	* 向服务器发送大量数据（POST 没有数据量限制）
	* 发送包含未知字符的用户输入时，POST 比 GET 更稳定也更可靠

## 6.请解释一下 JavaScript 的同源策略
* 概念:同源策略是客户端脚本（尤其是Javascript）的重要的安全度量标准。它最早出自Netscape Navigator2.0，其目的是防止某个文档或脚本从多个不同源装载。
* 这里的同源策略指的是：协议，域名，端口相同，同源策略是一种安全协议。
* 指一段脚本只能读取来自同一来源的窗口和文档的属性。
* 为什么要有同源限制？
* 我们举例说明：比如一个黑客程序，他利用Iframe把真正的银行登录页面嵌到他的页面上，当你使用真实的用户名，密码登录时，他的页面就可以通过Javascript读取到你的表单中input中的内容，这样用户名，密码就轻松到手了。

## 7.Flash、Ajax各自的优缺点，在使用中如何取舍？
* Flash适合处理多媒体、矢量图形、访问机器；对CSS、处理文本上不足，不容易被搜索。
* Ajax对CSS、文本支持很好，支持搜索；多媒体、矢量图形、机器访问不足。
* 共同点：与服务器的无刷新传递消息、用户离线和在线状态、操作DOM

## 8.什么是闭包？
* 闭包，官方对闭包的解释是：一个拥有许多变量和绑定了这些变量的环境的表达式（通常是一个函数），因而这些变量也是该表达式的一部分。闭包的特点：
    * （1）作为一个函数变量的一个引用，当函数返回时，其处于激活状态。
    * （2） 一个闭包就是当一个函数返回时，一个没有释放资源的栈区。
* 简单的说，Javascript允许使用内部函数---即函数定义和函数表达式位于另一个函数的函数体内。而且，这些内部函数可以访问它们所在的外部函数中声明的所有局部变量、参数和声明的其他内部函数。当其中一个这样的内部函数在包含它们的外部函数之外被调用时，就会形成闭包。

## 9.javascript里面的继承怎么实现，如何避免原型链上面的对象共享
* 用构造函数和原型链的混合模式去实现继承，避免对象共享可以参考经典的extend()函数，很多前端框架都有封装的，就是用一个空函数当做中间变量

## 10.ajax过程
* (1)创建XMLHttpRequest对象,也就是创建一个异步调用对象.
* (2)创建一个新的HTTP请求,并指定该HTTP请求的方法、URL及验证信息.
* (3)设置响应HTTP请求状态变化的函数.
* (4)发送HTTP请求.
* (5)获取异步调用返回的数据.
* (6)使用JavaScript和DOM实现局部刷新.

## 
## 