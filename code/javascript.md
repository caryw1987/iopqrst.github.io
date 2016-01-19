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


## javascript 操作样式 class 

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

## 常用到的计算

### 获取 m 到 n 之间的整数随机数

```javascript
// 包含m, 不包含n
function rnd(m,n) {
  return Math.ceil(Math.random() * (n - m) + m);
}

// 包含n, 不包含m
function rnd(m,n) {
  return Math.floor(Math.random() * (n - m) + m);
}

```

### 角度弧度互转

```javascript

/**
 * 弧度转角度
 */
function a2d(n) {
    return n * 180 / Math.PI;
}

/**
 * 角度转弧度
 */
function d2a(n) {
    return n * Math.PI / 180;
}
```

## IE浏览器版本低于8,提示用户升级

```javascript

// from http://g.alicdn.com/aliyun/console/1.3.13/scripts/browser-not-supported.js

window._browserIsNotSupported = true;
if(window.attachEvent){
  window.attachEvent('onload', function(){
    var lowestSupportedIEVersion = 8;
    if(window.LOWEST_IE_VERSION != undefined){
      lowestSupportedIEVersion = window.LOWEST_IE_VERSION;
    }
    var el = document.createElement('div'),
        elStyle = el.style,
        docBody = document.getElementsByTagName('body')[0],
        linkStyle = 'color:#06F;text-decoration: underline;';
    el.innerHTML =	'尊敬的用户：<br />'+
        '使用阿里云控制台需要安装Internet Explorer更新版本的浏览器，'+
        '请<a href="http://windows.microsoft.com/zh-cn/internet-explorer/download-ie" style="'+linkStyle+'" target="_blank">下载安装IE' + lowestSupportedIEVersion + '</a>（或更新）。'+
        '也可以在其他浏览器，'+
        '如<a href="http://www.google.com/intl/zh-CN/chrome/" style="'+linkStyle+'" target="_blank">Chrome</a>'+
        '或<a href="http://www.firefox.com.cn/download/" style="'+linkStyle+'" target="_blank">Firefox</a>火狐中打开控制台。';
    // elStyle.width = '100%';
    elStyle.width = '720px';
    elStyle.color = '#000';
    elStyle.fontSize = '14px';
    elStyle.lineHeight = '180%';
    elStyle.margin = '60px auto';
    elStyle.backgroundColor = '#fffbd5';
    elStyle.border = '1px solid #CCC';
    elStyle.padding = '24px 48px';

    docBody.innerHTML = '';
    docBody.appendChild(el);
    // docBody.insertBefore(el,docBody.firstChild);
  });
}

```
## 判断对象是否包含某个属性

### hasOwnProperty 用来判断某个对象是否含有指定的自身属性。该方法会忽略掉那些从原型链上继承到的属性。

```js
//常规的方式，包括我之前在循环中判断都是以该值是否为空来判断的，其实：
// 

obj.hasOwnProperty(prop); 

```

### in, 判断对象中的属性，一个字符串类型的属性名或者数字类型的数组索引。包含自身属性及从父及（原型链中继承过来的属性）

```js

// 判断原型中有该属性，但是自己属性中没有的属性
function hasPropertyInPrototype(obj, prop) {
	return !obj.hasOwnProperty(prop) && prop in obj;
}

```

## 与 Array 相关的的

### Array 的 remove 实现

```javascript

/**
 * 删除数组中的元素，（下面的写法为以后js提供remove做兼容）
 */
Array.prototype.remove = Array.prototype.remove || function(obj) {
	for (var i = 0; i < this.length; i++) {
		if (this[i] == obj) {
			this.splice(i, 1);
			i--;
		}
	}
}

```

### 判断是否为数组类型 ： isArray

#### 1、首先我会想到 `typeof` 来判断

```js
// typeof操作符。对于Function、String、Number、Undefined这几种类型的对象来说，不会有什么问题，但是针对Array的对象就没什么用途了： 

typeof [] ;
typeof null ； // 两个都返回object，其实是无法判断到底是不是数组的，
```

#### 2、于是，又想到了 `instanceof` ,`instanceof` 用来检测对象的原型链是否指向构造函数的prototype对象

```js
var arr = []; 
alert(arr instanceof Array); // true 
```

#### 3、对象的`constructor`属性。除了`instanceof`，我们还可以利用每个对象都具有`constructor`的属性来判断其类型，于是乎我们可以这样做: 

```js
var arr = [];   
alert(arr.constructor == Array); // true
```

#### 4、2/3在一般的情况下已经可以满足我们的需求，但是在某个包含多个框架（frame/iframe）页面的情况下却又不成立, 因为实际上就存在两个以上不同的全局执行环境，从而存在两个以上不同版本的`Array`构造函数 

```js

var iframe = document.createElement('iframe'); 
document.body.appendChild(iframe); 
xArray = window.frames[window.frames.length-1].Array; 
var arr = new xArray(1,2,3); // [1,2,3] 
// 哎呀！ 
arr instanceof Array; // false 
// 哎呀呀！ 
arr.constructor === Array; // false

//由于每个iframe都有一套自己的执行环境，跨frame实例化的对象彼此是不共享原型链的，因此导致上述检测代码失效
```

#### 5、最终解决方法

```js

function isArray(obj) {
  return Object.prototype.toString.call(obj) === '[object Array]'; 
}

```

### 使用sort对数组进行排序

```js

// 1、对数字进行排序

var arr = [30, 0.3, 22,190, 311, 222];
arr.sort();
[0.3, 190, 22, 222, 30, 311] 	// 很显然结果不是我们想要的

// ---
var arr = [30, 0.3, 22,190, 311, 222];
arr.sort(function(a,b) {
	return a - b;
});
[0.3, 22, 30, 190, 222, 311]	// 结果正确	

// 2、对字母进行排序

var arr = ['Alert', 'CQ','banana'];

console.info ( arr.sort() );
// ["Alert", "CQ", "banana"] 	// 结果与我们预期的不同


// --
var arr = ['alert', 'cQ','banana'];

console.info ( arr.sort() );
// ["alert", "banana", "cQ"] // 似乎是我们想要的结果，往下看

// --
var arr = ['alert', 'cQ2','banana', 'cq1'];

console.info ( arr.sort() );
// ["alert", "banana", "cQ2", "cq1"] // 按理说cQ2应该排在cq1的后面，于是想到数字的比较方式

// ---
var arr = ['alert', 'cQ2','banana', 'cq1'];

console.info ( arr.sort(function(a,b) {
    return a - b;
}) );
["alert", "cQ2", "banana", "cq1"] // 这样也不行

// ---
var arr = ['alert', 'cQ2','banana', 'cq1'];

console.info ( arr.sort(function(a,b) {
    if( a > b) {
        return 1;
    } else if(a < b) {
        return -1;
    } else {
        return 0;
    }
}) );
// ["alert", "banana", "cQ2", "cq1"] 	//还是不行

// ---
var arr = ['alert', 'cQ2','banana', 'cq1'];

console.info ( arr.sort(function(a,b) {
    a = a.toLowerCase(), b = b.toLowerCase();

    if( a > b) {
        return 1;
    } else if(a < b) {
        return -1;
    } else {
        return 0;
    }
}) );
//["alert", "banana", "cq1", "cQ2"] // 这才是我们想要的结果，（但对于B2，ba这两个该2在前还是在后需要根据需求在做处理了，这里默认是按照字符编码顺序来的。2->50,a -> 97)

```
> **说一下我们在这里犯过的几个错误**
> 
> - 操作符 `-` 的错误使用： 直接拿数字的比较方式对字母进行比较， 比如 a - b 的使用。操作数是字符串/boolean/null/undefined时，后台会调用Number()函数将其转化为数字，然后再根据相应的规则执行减法计算，如果转换结果是NaN，则减法结果就是NaN; `if(NaN) {}` 这样的条件永远不成立，则排序就无从谈起了。所以我们该用 `>` 和 `<` 判断。

> - 操作符 `<` 和 `>`的错误使用： 对于数字是不会出现问题的，错误主要出现在对字符串（这里值得是字母组成的字符串，不对汉字进行讨论）的操作， 看一下个例子：
> ```js
> var result = "Brick" < "alphabet"; // true；
> var result = "Brick".toLowerCase() < "alphabet".toLowerCase(); // false
> ```
> 原因：在比较字符串时，实际比较的是两个字符串中对应位置的每个字符的字符编码。已知大写字母的字符编码（A-Z -> 65-90）全部小于小写的字符编码(a-z -> 97-122) 。数字对应（0-9 -> 48-> 57）。

### 页面加载完成，执行多个函数

```js
function addLoadEvent(func) {
	var oldonload = window.onload;
	if (typeof window.onload != 'function') {
		window.onload = func;
	} else {
		window.onload = function() {
			oldonload();
			func();
		}
	}
}
```

### insertAfter 

```js
function insertAfter(newElement, targetElement) {
	var parent = targetElement.parentNode;
	if (parent.lastChild == targetElement) {
		parent.appendChild(newElement);
	} else {
		parent.insertBefore(newElement, targetElement.nextSibling);
	}
}
```

### resize image

```js
// 忘了从哪里复制的了
var resizePicWidth = function(selector, pic_width) {
	$(selector + " img").each(function() {
		var img = $(this);
		var realWidth; //真实的宽度
		var realHeight; //真实的高度
		//这里做下说明，$("<img/>")这里是创建一个临时的img标签，类似js创建一个new Image()对象！
		$("<img/>").attr("src", $(img).attr("src")).load(function() {
			/*
			  如果要获取图片的真实的宽度和高度有三点必须注意
			  1、需要创建一个image对象：如这里的$("<img/>")
			  2、指定图片的src路径
			  3、一定要在图片加载完成后执行如.load()函数里执行
			 */
			realWidth = this.width;
			realHeight = this.height;
			//如果真实的宽度大于规定的宽度就按照100%显示
			if (realWidth >= pic_width) {
				$(img).css("width", (pic_width) + "px");
			} else { //如果小于浏览器的宽度按照原尺寸显示
				$(img).css("width", realWidth + 'px');
			}
		});
	});
};

```

### 获取jquery 获取浏览器宽高、滚动条高度、屏幕的宽高

```js
;(function($) {
	$.extend($.browser, {
		client: function() {
			return {
				width: document.documentElement.clientWidth,
				height: document.documentElement.clientHeight,
				bodyWidth: document.body.clientWidth,
				bodyHeight: document.body.clientHeight
			};
		},
		scroll: function() {
			return {
				width: document.documentElement.scrollWidth,
				height: document.documentElement.scrollHeight,
				bodyWidth: document.body.scrollWidth,
				bodyHeight: document.body.scrollHeight,
				left: document.documentElement.scrollLeft + document.body.scrollLeft,
				top: document.documentElement.scrollTop + document.body.scrollTop
			};
		},
		screen: function() {
			return {
				width: window.screen.width,
				height: window.screen.height
			};
		},
		isIE6: $.browser.msie && $.browser.version == 6,
		isMinW: function(val) {
			return Math.min($.browser.client().bodyWidth, $.browser.client().width) <= val;
		},
		isMinH: function(val) {
			return $.browser.client().height <= val;
		}
	})
})(jQuery);
```

### 点点滴滴

````js

* Get element by id
 */	
function get(element){
	if (typeof element == "string")
		element = d.getElementById(element);
	return element;
}

/**
 * Attaches event to a dom element
 */
function addEvent(el, type, fn){
	if (w.addEventListener){
		el.addEventListener(type, fn, false);
	} else if (w.attachEvent){
		var f = function(){
		  fn.call(el, w.event);
		};			
		el.attachEvent('on' + type, f)
	}
}


/**
 * Creates and returns element from html chunk
 */
var toElement = function(){
	var div = d.createElement('div');
	return function(html){
		div.innerHTML = html;
		var el = div.childNodes[0];
		div.removeChild(el);
		return el;
	}
}();

function hasClass(ele,cls){
	return ele.className.match(new RegExp('(\\s|^)'+cls+'(\\s|$)'));
}

function addClass(ele,cls) {
	if (!hasClass(ele,cls)) ele.className += " "+cls;
}

function removeClass(ele,cls) {
	var reg = new RegExp('(\\s|^)'+cls+'(\\s|$)');
	ele.className=ele.className.replace(reg,' ');
}

/**
 * 根据样式名称（单个）获取元素
 * @param {Object} obj 在那个元素下查找 document/[元素对象]
 * @param {Object} cls 样式名称
 */
function getClassEles(obj, cls) {
	if (obj.getElementsByClassName) {
		return obj.getElementsByClassName(cls);
	} else {
		var tags = obj.getElementsByTagName('*');
		var aTargetEles = [];

		var oReg = new RegExp('(\\s|^)' + cls + '(\\s|$)');
		for (var i = 0; i < tags.length; i++) {
			if (tags[i].className.match(oReg)) {
				aTargetEles.push(tags[i]);
			}
		}
		return aTargetEles;
	}
}

````

## 参考链接
- isArray，[Javascript数组类型检测：编写更强壮的isArray函数](http://scriptfans.iteye.com/blog/318821, "Javascript数组类型检测：编写更强壮的isArray函数")
- isArray，《JavaScript高级程序设计(3） - 第5章引用》
- array排序部分， 《JavaScript高级程序设计(3） - 操作符/Number数值转换》