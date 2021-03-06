# 闭包

闭包（closure）

 闭包其实是**一个主动执行的代码块**，这个代码块的特殊之处是可以**永久保存局部变量**，但又**不污染全局变量，可以形成一个独立的执行过程**，因此我们**经常用闭包来定义组件**。

闭包的特点

* 闭包，是指有权访问另外一个函数作用域中变量的函数。a函数内，创建一个b函数。
* 指函数内部保留变量，被另外一个函数访问
* 有权访问另外一个函数作用域内变量的函数都是闭包。
* 变量被引用着，就不会被回收
* 技术上，所有js函数都是闭包，都是对象，关联到作用域链
* 造成原始作用域链不释放，造成内存泄露

闭包的场景

* 闭包替代全局变量
* 函数外或其他函数中访问某一个函数内部参数
* 函数执行之前，为要执行后一个函数提供具体的参数
* 为函数执行之前提供质优在函数执行或引用时才能知道的具体参数
* 为节点循环绑定click 事件，在事件函数中使用档次循环的值或节点，而不是最后一次循环的值或节点

```javascript
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

```javascript
　　var name = "The Window";
　　var object = {
　　　　name : "My Object",
　　　　getNameFunc : function(){
　　　　　　return function(){
　　　　　　　　return this.name;
　　　　　　};
　　　　}
　　};
　　alert(object.getNameFunc()()); //The Window
```

```javascript
　　var name = "The Window";

　　var object = {
　　　　name : "My Object",
　　　　getNameFunc : function(){
　　　　　　var that = this;
　　　　　　return function(){
　　　　　　　　return that.name;
　　　　　　};
　　　　}
　　};
　　alert(object.getNameFunc()());//My Object
```

