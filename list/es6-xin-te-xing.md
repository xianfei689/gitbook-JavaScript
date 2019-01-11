# ES6 新特性

ES6 新特性

[编辑](https://gitee.com/zhouxianfei/zhouxf.front.doc/wikis/ES6%20新特性?parent=JavaScript高级语法)

## 参考连接：

* [**ES6教程**](http://www.softwhy.com/article-8963-1.html)

### 1.函数默认参数

> ES5:

```javascript
var link = function (height, color, url) {
    var height = height || 50;
    var color = color || 'red';
    var url = url || 'http://azat.co';
    ...
}
```

> ES6:

```javascript
var link = function(height = 50, color = 'red', url = 'http://azat.co') {
  ...
}
```

### 2. 模版表达式

> ES5:

```javascript
var name = 'Your name is ' + first + ' ' + last + '.';
var url = 'http://localhost:3000/api/messages/' + id;
```

> ES6:

```javascript
var name = `Your name is ${first} ${last}. `;
var url = `http://localhost:3000/api/messages/${id}`;
```

### 3. 多行字符串

> ES5:

```text
var roadPoem = 
'Then
 took the other, 
as
 just 
as
 fair,nt'
    + 
'And
 having perhaps the better claimnt'
    + 
'Because
 it was grassy 
and
 wanted wear,nt'
    + 
'Though
as
for
 that the passing therent'
    + 
'Had
 worn them really about the same,nt';
```

> ES6:

```javascript
var roadPoem = 'Then took the other, as just as fair,nt'
    + 'And having perhaps the better claimnt'
    + 'Because it was grassy and wanted wear,nt'
    + 'Though as for that the passing therent'
    + 'Had worn them really about the same,nt';
```

### 4. 解构赋值

> 之前:

```javascript
var jsonMiddleware = require('body-parser').jsonMiddleware ;
var body = req.body,
   username = body.username,
   password = body.password;
```

> ES6:

```javascript
var {jsonMiddleware} = require('body-parser');
var {username, password} = req.body;
```

### 5. 箭头函数

> ES5:

```javascript
var _this = this
$('.btn').click(function(event){
  _this.sendData()
})
```

> ES6:

```javascript
$('.btn').click((event) =>{
  this.sendData()
})
```

### 6. let与const 关键字

可以把let看成var，只是它定义的变量被限定在了特定范围内才能使用，而离开这个范围则无效。const则很直观，用来定义常量，即无法被更改值的变量。

> 使用时拓展：

* let不会像var一样声明提前，只能在定义之后使用，之前使用会抛出ReferenceError；
* 并且只要作用域内有let声明的变量，这个变量就会被绑定，不受原来变量声明规则的影响。即ES6明确规定，如果区块中存在let和const命令，这个区块对这些命令声明的变量，从一开始就形成了封闭作用域。凡是在声明之前就使用这些命令，就会报错。这在语法上，称为“暂时性死区”（temporal dead zone，TDZ）。

```javascript
var tmp = 123;
if (true) {
  // TDZ开始
  tmp = 'abc'; // ReferenceError
  console.log(tmp); // ReferenceError

  let tmp; // TDZ结束
  console.log(tmp); // undefined

  tmp = 123;
  console.log(tmp); // 123
}
```

> const使用时拓展：

使用时需注意：

* 对常量重新赋值不会报错，只会默默地失败。
* 与let命令相同，只在声明所在的块级作用域内有效。
* const命令也不存在提升，只能在声明的位置后面使用，提前使用同样会抛出ReferenceError。
* 同样不可重复声明。
* const命令只是指向变量所在的地址，如果将const变量赋值为一个对象，则此常量储存的是一个地址，不可变的只是这个地址，但对象本身是可变的，依然可以为其添加新属性。如果真的想将对象冻结，应该使用Object.freeze方法。

> 拓展：

ES6声明变量的六种方法 ES5只有两种声明变量的方法：var和function ES6除了添加let和const，还有另外两种声明变量的方法：import命令和class命令。所以，ES6一共有6种声明变量的方法。

![](http://zhouxianfei.gitee.io/imgstore/front/javascript/4.0.png)


