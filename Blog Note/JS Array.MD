`JS Array对象定义的方法都不能改变数组的内容，而仅仅会返回数组的一个副本。`
# concat()  方法 用于连接两个或多个数组。
*  语法
#### arrayObject.concat(arrayX,arrayX,......,arrayX)
    1. (arrayX)必需。该参数可以是具体的值，也可以是数组对象。可以是任意多个
```javascript
var colors = ["red", "green", "blue"]; 
var colors2 = colors.concat("yellow", ["black", "brown"]); //  ["red", "green", "blue", "yellow", "black", "brown"]
var colors3 = colors.concat(); // ["red", "green", "blue"] 
```
* 返回值：
    * 返回一个新的数组。该数组是通过把所有 arrayX 参数添加到 arrayObject 中生成的。如果要进行 concat() 操作的参数是数组，那么添加的是数组中的元素，而不是数组。


# join()  方法 把数组中的所有元素放入一个字符串
*  语法
#### arrayObject.join(separator)
    1. (separator)可选。指定要使用的分隔符。如果省略该参数，则使用逗号作为分隔符
```javascript
var colors = ["red", "green", "blue"]; 
var colors3 = colors.join(); // "red,green,blue"
var colors4 = colors.join('.'); // red.green.blue
```
* 返回值：
    * 返回一个字符串。该字符串是通过把 arrayObject 的每个元素转换为字符串，然后把这些字符串连接起来，在两个元素之间插入 separator 字符串而生成的。


# slice()  方法 从已有的数组中返回选定的元素。
*  语法
#### arrayObject.slice(start,end)
    1. (start)必需。规定从何处开始选取。如果是负数，那么从数组尾部开始算起
    2. (end)可选。规定从何处结束选取。如果是负数，那么从数组尾部开始算起
```javascript
var colors = ["red", "green", "blue", "yellow", "purple"];
var colors2 = colors.slice(1); // ["green", "blue", "yellow", "purple"]  从第一项到末尾
var colors3 = colors.slice(1,4) // ["green", "blue", "yellow"] 起始项到结束项，但不包含结束项
// 如果参数有负数，则参数加上数组长度。eg array.length=5, slice(-2,-1)与slice(3,4) 返回一样
// 如果结束位置小于起始位置，则返回空数组。
```
* 返回值：
    * 返回一个新的数组，包含从 start 到 end （不包括该元素）的 arrayObject 中的元素
    
* 说明
    * 请注意，该方法并不会修改数组，而是返回一个子数组。如果想删除数组中的一段元素，应该使用方法 Array.splice()。
    
    
    
# splice()  方法 向/从数组中添加/删除项目，然后返回被删除的项目。》》》（splice方法会改变原数组）
*  语法
#### arrayObject.splice(index,howmany,item1,.....,itemX)
    1. (index)	必需。整数，规定添加/删除项目的位置，使用负数可从数组结尾处规定位置。
    2. (howmany)必需。要删除的项目数量。如果设置为 0，则不会删除项目。
    2. (itemX)可选。向数组添加的新项目。
```javascript
var colors = ["red", "green", "blue"];
var removed = colors.splice(0,1); // 删除第一项
alert(colors); // green,blue
alert(removed); // red，返回的数组中只包含一项
removed = colors.splice(1, 0, "yellow", "orange"); // 从位置1 开始插入两项
alert(colors); // green,yellow,orange,blue
alert(removed); // 返回的是一个空数组
removed = colors.splice(1, 1, "red", "purple"); // 插入两项，删除一项
alert(colors); // green,red,purple,orange,blue
alert(removed); // yellow，返回的数组中只包含一项
```
* 返回值：
    * 返回被删除项目的新数组，如果有的话
    
* 说明
    * splice() 方法可删除从 index 处开始的零个或多个元素，并且用参数列表中声明的一个或多个值来替换那些被删除的元素。
      如果从 arrayObject 中删除了元素，则返回的是含有被删除的元素的数组。
      
      
# indexOf()  返回要查找的项在数组中的位置，或者在没找到的情况下返回-1
*  语法
#### arrayObject.indexOf(searchvalue,fromindex)
    1. (searchvalue)	要查找的项
    2. (fromindex)  （可选的）表示查找起点位置的索引
