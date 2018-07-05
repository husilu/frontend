# frontend
前端面试
前端面试

<font color='red'>Es基础知识点</font>

值类型VS引用类型

值类型：Boolean、String、Number、undefined、Null。按照值传递。（复制一份存入栈内存）

引用类型：Object类的所有。按照共享传递，指向同一个内存地址。

原型和原型链

1：所有的引用类型（数组，对象，函数）都具有对象特征，即可自由扩展属性。（null除外）

2：所有的引用类型（数组，对象，函数）都有一个proto属性，属性值是一个普通的对象，也就是其构造函数的prototype

3：所有的引用类型（数组，对象，函数）都有一个prototype属性，属性值是一个普通的对象。

原型

如果一个对象的某个属性不存在的时候就会去它的proto中找，即它的构造函数的prototype中寻找。

hasOwnProperty判断这个属性是不是对象本身的属性。

执行上下文

先把代码中 即将执行的变量，函数声明都拿出来，变量先暂时赋值为undefined。var 关键字表示存入执行上下文。

函数的执行上下文会多出this，arguments和函数的参数。this的值是在执行的时候才能确认，定义的时候不能确认。

this执行分为4种：

1：作为构造函数执行

2：作为对象属性执行

3：作为普通函数执行

4：用于call，apply，bind

闭包

依据的是函数定义时的作用域链，而不是函数执行时。

主要两个应用场景：

函数作为返回值。

函数作为参数传递。

异步

异步是什么？即不会阻塞后面程序的运行。

需要异步的原因是js是单线程运行的，不能一心二用。

异步使用场景：

1：定时setTimeout  setInterval

2：网络请求 如 ajax <img> 加载

module（ES6模块化的使用）

在一个文件或者模块中，export，import可以有多个，export default 仅有一个。

通过export导出时，在导入的时候要加{}.export default就不用。

Class

取代之前构造函数初始化对象的形式。

class className{

constructor(x,y){

this.x=x;

this.y=y;}

add(){return this.x+this.y}

}

使用class来实现继承：

class Dog extends Animal {

constructor(x,y,name){

super(x,y)//调用父类的constructor(x, y)

this.name=name}}

ES6中新增的数据类型

set(类似数组.不会有重复的)和map(类似对象)

Set:

const set = new Set([1,2,3,4,4])

console.log(set) // Set(4)[1,2,3,4].

set.size()获取元素数量

set.add()set添加元素 返回set实例本身

delete()删除元素

has()返回一个布尔值表示该值是否是set实例的元素

set实例的遍历：

keys()返回键名的遍历器

values()返回键值的遍历器 ps：因为set没有键名，所以key()和values()返回的值都是一样的

entries()返回键值对的遍历器

forEach()使用回调函数遍历每个成员

set.forEach((value,key)=>{console.log(key+''+value)});

Map:

用法和普通对象基本一致 它能用非字符串或者数字作为key

const map = new Map()

const obj ={p:'Hello world'}

map.set(obj,'OK');

map.get(obj)

map.has(obj)

Map实例的遍历方法：

keys(),values().entries()

Promise

3-2-1.

3个状态，2个过程，1个方法。

状态：pending,fulfilled,rejected.

过程：pending ->fulfilled(resolve)  pending->rejected(reject)

方法：then()

<font color="red">Web Api</font>

Bom

1:navigator  navigator.userAgent 查询浏览器是什么浏览器

2：screen  screen.width screen.height

3:location

4:history

Dom

获取父元素 parentElement

获取子元素 childNodes

删除元素 removeChild(child[0])

阻止事件冒泡 e.stopPropagation()

事件代理：

类似于要使用jq的事件绑定要使用on来绑定，来给页面生成之后动态生成的某个元素添加事件。

（我是这么理解的，原来小册不是这么写的，它写了具体的实现方法）

Ajax

var xhr =new  XMLHttpRequest();

xhr.onreadyStateChange=function(){

if(xhr.readyState==4){

if(xhr.status==200){

	xhr.responseText()

}}

}

xhr.open('method','url',false)

xhr.send(null)

Fetch Api

fetch('url'{

method:'',

headers:'',

body:'',

mode:'',

...}).then(function())

跨域

协议，域名，端口。

script.img.link这三个标签不受同源策略影响。

解决跨域1: JSNOP,2:服务器端配置http header

存储

cookie 服务器和客户端进行信息传递。但是cookie也具备浏览器端存储的能力。

document.cookie=...

存储量小，只有4kb

所有HTTP请求都带着cookie

LocalStorage和sessionStorage

Http请求不会带。存储量5MB。LocalStorage永久，sessionStorage有时间限制。

<font color="red">CSS</font>

清除浮动

.clearfix:after{

content:'';

display:table;

clear:both;

}

盒子模型

border-box   css中设置的宽度就是 内容宽度+padding+border 

content-box css中设置的宽度就是  内容宽度

flex布局

flex:2的宽度为flex:1的二倍。

垂直水平居中

absolute+transtion:transform(-50%,-50%)

css3动画

1:@keyframes定义一个动画

2：设置动画

@keyframes testAnimation { 

0%   {background: red; left:0; top:0;}

 25%  {background: yellow; left:200px; top:0;} 

50%  {background: blue; left:200px; top:200px;} 

75%  {background: green; left:0; top:200px;} 

100% {background: red; left:0; top:0;}

 }

针对一个 CSS 选择器来设置动画，例如针对div元素设置动画 

div { width: 100px; 

height: 50px; 

position: absolute; 

animation-name: myfirst; 

animation-duration: 5s; 

}

重绘和回流

 重绘：指的是当页面中的元素不脱离文档流，而简单地进行样式的变化，比如修改颜色、背景等，浏览器重新绘制样式

 回流：指的是处于文档流中 DOM 的尺寸大小、位置或者某些属性发生变化时，导致浏览器重新渲染部分或全部文档的情况... 



<font color="red">浏览器相关知识点</font>

加载页面和渲染过程

加载过程：

URL->DNS->IP->发送HTTP请求->server

server->返回HTTP请求(html格式的字符串)

渲染过程：

HTML->DOM树

CSS->CSSOM树

CSSOM+DOM整合形成RenderTree

根据RenderTree开始渲染和展示

遇到<script>时候会阻塞渲染

解析过程中，如果遇到和<link href="..."> 和 <script src="..."> 这种外链加载 CSS 和 JS 的标签，浏览器会异步下载，下载过程和上文中下载 HTML 的流程一样。只不过，这里下载下来的字符串是 CSS 或者 JS 格式的。 

性能优化

优化原则和方向

性能优化的原则是以更好的用户体验为标准，具体就是实现下面的目标：

1. 多使用内存、缓存或者其他方法
2. 减少 CPU 和GPU 计算，更快展现

优化的方向有两个：

- 减少页面体积，提升网络加载
- 优化页面渲染

减少页面体积，提升网络加载

- 静态资源的压缩合并（JS 代码压缩合并、CSS 代码压缩合并、雪碧图）
- 静态资源缓存（资源名称加 MD5 戳）
- 使用 CDN 让资源加载更快

优化页面渲染 CSS 放前面，JS 放后面 

懒加载（图片懒加载、下拉加载更多）

 减少DOM 查询，对 DOM 查询做缓存 

减少DOM 操作，多个操作尽量合并在一起执行（DocumentFragment） 

事件节流 尽早执行操作（DOMContentLoaded） 使用 SSR 后端渲染，数据直接输出到 HTML 中，减少浏览器使用 JS 模板渲染页面 HTML 的时间..
