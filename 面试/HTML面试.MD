# 第一章节
## 1.几大浏览器对应的内核
* IE-Trident
* Chrome Safari-Webkit
* FireFox-Gecko
* Opera-presto
## 2.清除浮动有哪些方式？比较好的方式是哪一种？
* （1）父级div定义height。
* （2）结尾处加空div标签clear:both。
* （3）父级div定义伪类:after和zoom。
* （4）父级div定义overflow:hidden。
* （5）父级div定义overflow:auto。
* （6）父级div也浮动，需要定义宽度。
* （7）父级div定义display:table。
* （8）结尾处加br标签clear:both。
## 3.Doctype作用？标准模式与兼容模式各有什么区别?
* <!DOCTYPE>告知浏览器的解析器用什么文档标准解析这个文档。DOCTYPE不存在或格式不正确会导致文档以兼容模式呈现。
* 标准模式的排版和JS运作模式都是以该浏览器支持的最高标准运行。在兼容模式中，页面以宽松的向后兼容的方式显示,模拟老式浏览器的行为以防止站点无法工作。
## 4.页面导入样式时，使用link和@import有什么区别？
* link属于XHTML标签，除了加载CSS外，还能用于定义RSS,定义rel连接属性等作用；而@import是CSS提供的，只能用于加载CSS;
* 页面被加载的时，link会同时被加载，而@import引用的CSS会等到页面被加载完再加载;
* import是CSS2.1 提出的，只在IE5以上才能被识别，而link是XHTML标签，无兼容问题;
## 5.介绍一下你对浏览器内核的理解？
* 主要分成两部分：渲染引擎(layout engineer或Rendering Engine)和JS引擎。
* 渲染引擎：负责取得网页的内容（HTML、XML、图像等等）、整理讯息（例如加入CSS等），以及计算网页的显示方式，然后会输出至显示器或打印机。浏览器的内核的不同对于网页的语法解释会有不同，所以渲染的效果也不相同。所有网页浏览器、电子邮件客户端以及其它需要编辑、显示网络内容的应用程序都需要内核。
* JS引擎则：解析和执行javascript来实现网页的动态效果。最开始渲染引擎和JS引擎并没有区分的很明确，后来JS引擎越来越独立，内核就倾向于只指渲染引擎。
## 5.html5有哪些新特性？
* 绘画 canvas;
* 用于媒介回放的 video 和 audio 元素;
* 本地离线存储 localStorage 长期存储数据，浏览器关闭后数据不丢失;
* sessionStorage 的数据在浏览器关闭后自动删除;
* 语意化更好的内容元素，比如 article、footer、header、nav、section;
* 表单控件，calendar、date、time、email、url、search;
* 新的技术webworker, websocket, Geolocation;
## 6.简述一下你对HTML语义化的理解？
* 用正确的标签做正确的事情。
* html语义化让页面的内容结构化，结构更清晰，便于对浏览器、搜索引擎解析;
* 即使在没有样式CSS情况下也以一种文档格式显示，并且是容易阅读的;
* 搜索引擎的爬虫也依赖于HTML标记来确定上下文和各个关键字的权重，利于SEO;
* 使阅读源代码的人对网站更容易将网站分块，便于阅读维护理解。




# 第二章节

## 1.请描述一下 cookies，sessionStorage 和 localStorage 的区别？
* cookie是网站为了标示用户身份而储存在用户本地终端（Client Side）上的数据（通常经过加密）。
* cookie数据始终在同源的http请求中携带（即使不需要），记会在浏览器和服务器间来回传递。
* sessionStorage和localStorage不会自动把数据发给服务器，仅在本地保存。
* 存储大小：
	* cookie数据大小不能超过4k。
	* sessionStorage和localStorage 虽然也有存储大小的限制，但比cookie大得多，可以达到5M或更大。
* 有期时间：
	* localStorage    存储持久数据，浏览器关闭后数据不丢失除非主动删除数据；
	* sessionStorage  数据在当前浏览器窗口关闭后自动删除。
	* cookie          设置的cookie过期时间之前一直有效，即使窗口或浏览器关闭

## 2.iframe有那些缺点？
* iframe会阻塞主页面的Onload事件；
* 搜索引擎的检索程序无法解读这种页面，不利于SEO;
* iframe和主页面共享连接池，而浏览器对相同域的连接有限制，所以会影响页面的并行加载。
* 使用iframe之前需要考虑这两个缺点。如果需要使用iframe，最好是通过javascript动态给iframe添加src属性值，这样可以绕开以上两个问题。

## 3.如何实现浏览器内多个标签页之间的通信?
* WebSocket、SharedWorker
* 也可以调用localstorge、cookies等本地存储方式。
* localstorge另一个浏览上下文里被添加、修改或删除时，它都会触发一个事件，我们通过监听事件，控制它的值来进行页面信息通信。

