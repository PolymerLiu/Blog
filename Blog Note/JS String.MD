# `JavaScript 的字符串是不可变的（immutable），String 类定义的方法都不能改变字符串的内容。像 String.toUpperCase() 这样的方法，返回的是全新的字符串，而不是修改原始字符串`
# charAt() 方法可返回指定位置的字符。
*  语法
#### stringObject.charAt(index) 
    1. (index) 必需。字符在字符串中的下标。
* 注释：
    * 字符串中第一个字符的下标是 0。如果参数 index 不在 0 与 string.length 之间，该方法将返回一个空字符串。


# charCodeAt() 方法可返回指定位置的字符的 Unicode 编码。这个返回值是 0 - 65535 之间的整数。
*  语法
#### stringObject.charCodeAt(index) 
    1. (index) 必需。字符在字符串中的下标。
* 注释：
    * 字符串中第一个字符的下标是 0。如果 index 是负数，或大于等于字符串的长度，则 charCodeAt() 返回 NaN


# concat() 方法用于连接两个或多个字符串。
*  语法
#### stringObject.concat(stringX,stringX,...,stringX)
    1. (stringX) 必需。将被连接为一个字符串的一个或多个字符串对象。
* 注释：
    * concat() 方法将把它的所有参数转换成字符串，然后按顺序连接到字符串 stringObject 的尾部，并返回连接后的字符串。请注意，stringObject 本身并没有被更改。
    * stringObject.concat() 与 Array.concat() 很相似
    * 使用 " + " 运算符来进行字符串的连接运算通常会更简便一些。


# indexOf() 方法可返回某个指定的字符串值在字符串中首次出现的位置。》》》(从前往后开始搜索)
*  语法
#### stringObject.indexOf(searchvalue,fromindex)
> * searchvalue 必需。规定需检索的字符串值。
> * fromindex	可选的整数参数。规定在字符串中开始检索的位置。它的合法取值是 0 到 stringObject.length - 1。如省略该参数，则将从字符串的首字符开始检索。
>   * 该方法将从头到尾地检索字符串 stringObject，看它是否含有子串 searchvalue。开始检索的位置在字符串的 fromindex 处或字符串的开头（没有指定 fromindex 时）。
如果找到一个 searchvalue，则返回 searchvalue 的第一次出现的位置。stringObject 中的字符位置是从 0 开始的。
* 注释：
    * indexOf() 方法对大小写敏感！
    * 如果要检索的字符串值没有出现，则该方法返回 -1。


# lastIndexOf() 方法可返回某个指定的`字符串值`在字符串中最后出现的位置。》》》(从后往前开始搜索)字段首次出现的位置
*  语法4
#### stringObject.lastIndexOf(searchvalue,fromindex)
    
    
# match() 方法
# replace() 方法  以后再看


# slice() 方法可提取字符串的某个部分，并以新的字符串返回被提取的部分。
*  语法
#### stringObject.slice(start,end) // start为起始下标 、end为结尾的下标（到end结束，但是不包括end）
> 返回值
  * 一个新的字符串。包括字符串 stringObject 从 start 开始（包括 start）到 end 结束（不包括 end）为止的所有字符。
> 说明
  * String 对象的方法 `slice()`、`substring()` 和 `substr(` （不建议使用）都可返回字符串的指定部分。
  * slice() 比 substring() 要灵活一些，因为它允许使用负数作为参数。slice() 与 substr() 有所不同，因为它用两个字符的位置来指定子串，而 substr() 则用字符位置和长度来指定子串。
  * 还要注意的是，String.slice() 与 Array.slice() 相似。
  
  
# split() 方法用于把一个字符串分割成字符串数组。
*  语法
#### stringObject.split(separator,howmany)
> * separator	必需。字符串或正则表达式，从该参数指定的地方分割 stringObject。
  * howmany	可选。该参数可指定返回的数组的最大长度。如果设置了该参数，返回的子串不会多于这个参数指定的数组。如果没有设置该参数，整个字符串都会被分割，不考虑它的长度
> 返回值
  * 一个字符串数组。该数组是通过在 separator 指定的边界处将字符串 stringObject 分割成子串创建的。返回的数组中的字串不包括 separator 自身。
  * 但是，如果 separator 是包含子表达式的正则表达式，那么返回的数组中包括与这些子表达式匹配的字串（但不包括与整个正则表达式匹配的文本）
> 注释
  * 如果把空字符串 ("") 用作 separator，那么 stringObject 中的每个字符之间都会被分割。
  * String.split() 执行的操作与 Array.join 执行的操作是相反的。


# strike() 方法用于显示加删除线的字符串。
*  语法
#### stringObject.strike()









