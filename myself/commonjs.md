---
title: CommonJS�淶
layout: page
category: myself
date: 2015-04-17
modifiedOn: 2015-04-17
---

## ����

CommonJS�Ƿ�������ģ��Ĺ淶��Node.js����������淶��

����CommonJS�淶��һ���������ļ�����һ��ģ�顣ÿһ��ģ�鶼��һ��������������Ҳ����˵���ڸ�ģ���ڲ�����ı������޷�������ģ���ȡ�����Ƕ���Ϊglobal��������ԡ�

```javascript

global.warming = true;

```

��������waiming���������Ա�����ģ���ȡ����Ȼ���������ǲ��Ƽ������ģ���������÷�����ʹ��module.exports����

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

�������ͨ��module.exports���󣬶�����һ���������ú�������ģ���ⲿ���ڲ�ͨ�ŵ�������

����ģ��ʹ��require�������÷�����ȡһ���ļ���ִ�У���󷵻��ļ��ڲ���module.exports���󡣼ٶ���һ��һ���򵥵�ģ��example.js��

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

## �ο�����

- Addy Osmani, [Writing Modular JavaScript With AMD, CommonJS & ES Harmony](http://addyosmani.com/writing-modular-js/)
- Pony Foo, [A Gentle Browserify Walkthrough](http://blog.ponyfoo.com/2014/08/25/a-gentle-browserify-walkthrough)
