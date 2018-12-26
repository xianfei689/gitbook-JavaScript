闭包（closure）

[编辑](https://gitee.com/zhouxianfei/zhouxf.front.doc/wikis/闭包（closure）?parent=JavaScript高级语法)

```js
　　function f1(){

　　　　var n=999;

　　　　function f2(){
　　　　　　alert(n); 
　　　　}

　　　　return f2;

　　}

　　var result=f1();

　　result(); // 999
```

> f2函数，就是闭包
>
> \*\* 闭包：\*\* 我的理解是，闭包就是能够读取其他函数内部变量的函数。
>
> Javascript语言中，只有函数内部的子函数才能读取局部变量，因此可以把闭包简单理解成"定义在一个函数内部的函数"。
>
> 在本质上，闭包就是将函数内部和函数外部连接起来的一座桥梁。
>
> 闭包的用途：一个是前面提到的可以读取函数内部的变量，另一个就是让这些变量的值始终保持在内存中。
>
> **闭包的注意点**

1）由于闭包会使得函数中的变量都被保存在内存中，内存消耗很大，所以不能滥用闭包，否则会造成网页的性能问题，在IE中可能导致内存泄露。解决方法是，在退出函数之前，将不使用的局部变量全部删除。

2）闭包会在父函数外部，改变父函数内部变量的值。所以，如果你把父函数当作对象（object）使用，把闭包当作它的公用方法（Public Method），把内部变量当作它的私有属性（private value），这时一定要小心，不要随便改变父函数内部变量的值。

> **如果你能理解下面两段代码的运行结果，应该就算理解闭包的运行机制了。**

```js
var
 name = 
"The Window"
;

　　
var
 object = {
　　　　name : 
"My Object"
,

　　　　getNameFunc : 
function
()
{
　　　　　　
return
function
()
{
　　　　　　　　
return
this
.name;
　　　　　　};

　　　　}

　　};

　　alert(object.getNameFunc()()); 
//The Window
```

```js
var
 name = 
"The Window"
;

　　
var
 object = {
　　　　name : 
"My Object"
,

　　　　getNameFunc : 
function
()
{
　　　　　　
var
 that = 
this
;
　　　　　　
return
function
()
{
　　　　　　　　
return
 that.name;
　　　　　　};

　　　　}

　　};

　　alert(object.getNameFunc()());
//My Object
```



