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

// 角度转弧度
function a2d() {
	
}

// 弧度转角度
function d2a() {
	
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


## 参考链接

- Addy Osmani, [Writing Modular JavaScript With AMD, CommonJS & ES Harmony](http://addyosmani.com/writing-modular-js/)
- Pony Foo, [A Gentle Browserify Walkthrough](http://blog.ponyfoo.com/2014/08/25/a-gentle-browserify-walkthrough)
- 血糖高管,[xtgg.com](http://www.xtgg.com)
- 云健康, [bskcare.com]












[bskcare.com]: http://www.bskcare.com "云健康系统"