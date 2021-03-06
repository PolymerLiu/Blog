#　原生JS forEach()和map()遍历
### 共同点：
* 1.都是循环遍历数组中的每一项。
* 2.forEach() 和 map() 里面每一次执行匿名函数都支持3个参数：数组中的当前项item,当前项的索引index,原始数组input。
* 3.匿名函数中的this都是指Window。
* 4.只能遍历数组。
### 1.forEach() 没有返回值。
```javascript
var ary = [12,23,24,42,1];  
var res = ary.forEach(function (item,index,input) {  
       input[index] = item*10;  
})  
console.log(res);//-->undefined;  
console.log(ary);//-->会对原来的数组产生改变；  
```
### 2.map() 有返回值，可以return 出来。
```javascript
var ary = [12,23,24,42,1];  
var res = ary.map(function (item,index,input) {  
    return item*10;  
})  
console.log(res);//-->[120,230,240,420,10];  
console.log(ary);//-->[12,23,24,42,1]；  
```
#### 兼容写法：
> 不管是forEach还是map在IE6-8下都不兼容（不兼容的情况下在Array.prototype上没有这两个方法）,那么需要我们自己封装一个都兼容的方法，代码如下：
```javascript
/** 
* forEach遍历数组 
* @param callback [function] 回调函数； 
* @param context [object] 上下文； 
*/  
Array.prototype.myForEach = function myForEach(callback,context){  
    context = context || window;  
    if('forEach' in Array.prototye) {  
        this.forEach(callback,context);  
        return;  
    }  
    //IE6-8下自己编写回调函数执行的逻辑  
    for(var i = 0,len = this.length; i < len;i++) {  
        callback && callback.call(context,this[i],i,this);  
    }  
} 

/** 
* map遍历数组 
* @param callback [function] 回调函数； 
* @param context [object] 上下文； 
*/  
Array.prototype.myMap = function myMap(callback,context){  
    context = context || window;  
    if('map' in Array.prototye) {  
        return this.map(callback,context);  
    }  
    //IE6-8下自己编写回调函数执行的逻辑  
    var newAry = [];  
    for(var i = 0,len = this.length; i < len;i++) {  
        if(typeof  callback === 'function') {  
            var val = callback.call(context,this[i],i,this);  
            newAry[newAry.length] = val;  
        }  
    }  
    return newAry;  
}  
```
# jQuery $.each()和$.map()遍历 (共同点：即可遍历数组，又可遍历对象。)
### 1.$.each() 没有返回值。
* $.each()里面的匿名函数支持2个参数：当前项的索引i，数组中的当前项n。
* 如果遍历的是对象，k 是键，n 是值。
```javascript
$.each( ["a","b","c"], function(i, n){  
     alert( i + ": " + n );  
});  
```
```javascript
$("span").each(function(i, n){  
     alert( i + ": " + n );  
});  
```
```javascript
$.each( { name: "John", lang: "JS" }, function(k, n){  
     alert( "Name: " + k + ", Value: " + n );  
});  
```
### 2.$.map()有返回值，可以return 出来。
* $.map()里面的匿名函数支持2个参数和$.each()里的参数位置相反：数组中的当前项n，当前项的索引i。
* 如果遍历的是对象，i 是值，n 是键。如果是$("span").map()形式，参数顺序和$.each()  $("span").each()一样。
```javascript
var arr=$.map( [0,1,2], function(n){  
     return n + 4;  
});  
console.log(arr); 
```
```javascript
$.map({"name":"Jim","age":17},function(i,n){  
     console.log(i+":"+n);  
}); 
```