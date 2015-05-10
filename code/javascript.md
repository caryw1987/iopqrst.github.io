---
title: javascript-代码段
layout: page
category: code
date: 2015-04-21
modifiedOn: 2015-04-21
---

## apply、call 和 bind 的区别

### apply 使用

根据CommonJS规范，一个单独的文件就是一个模块。每一个模块都是一个单独的作用域，也就是说，在该模块内部定义的变量，无法被其他模块读取，除非定义为global对象的属性。

```javascript

global.warming = true;

```
### call 使用

上面代码的waiming变量，可以被所有模块读取。当然，这样做是不推荐，输出模块变量的最好方法是使用module.exports对象。

```javascript

var i = 1;
var max = 30;

module.exports = function () {
  for (i -= 1; i++ < max; ) {
    console.log(i);
  }
  max *= 1.1;
};

```
### bind 使用

上面代码通过module.exports对象，定义了一个函数，该函数就是模块外部与内部通信的桥梁。

加载模块使用require方法，该方法读取一个文件并执行，最后返回文件内部的module.exports对象。假定有一个一个简单的模块example.js。

{% highlight javascript %}

// example.js

console.log("evaluating example.js");

var invisible = function () {
  console.log("invisible");
}

exports.message = "hi";

exports.say = function () {
  console.log(message);
}

{% endhighlight %}


## javascript class 实现操作

### 方式一 最基本的方式

````javascript

function hasClass(ele,cls){
	return ele.className.match(new RegExp('(\\s|^)'+cls+'(\\s|$)'));
}

function addClass(ele,cls) {
	if (!hasClass(ele,cls)) {
		ele.className += " "+cls;
	}
}

function removeClass(ele,cls) {
	var reg = new RegExp('(\\s|^)'+cls+'(\\s|$)');
	ele.className=ele.className.replace(reg,' ');
}

````

### 方式二 扩展 classList 实现

```javascript

function addClass() {
	
}


````

## 参考链接

- Addy Osmani, [Writing Modular JavaScript With AMD, CommonJS & ES Harmony](http://addyosmani.com/writing-modular-js/)
- Pony Foo, [A Gentle Browserify Walkthrough](http://blog.ponyfoo.com/2014/08/25/a-gentle-browserify-walkthrough)
- 血糖高管,[xtgg.com](http://www.xtgg.com)
- 云健康, [bskcare.com]












[bskcare.com]: http://www.bskcare.com "云健康系统"