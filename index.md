---
layout: homepage
title: 以后这就是我的blog啦
date: 2015-04-16
modifiedOn: 2015-04-16
---
	
<h2 id="introduction">导论</h2>

- [前言](introduction/preface.html)
- [为什么学习JavaScript？](introduction/why.html)
- [JavaScript的历史](introduction/history.html)

<h2 id="grammar">基本语法</h2>

- [概述](grammar/basic.html)
- [数值](grammar/number.html)
- [字符串](grammar/string.html)
- [对象](grammar/object.html)
- [数组](grammar/array.html)
- [函数](grammar/function.html)
- [运算符](grammar/operator.html)		
- [数据类型转换](grammar/conversion.html)（基本完成）
- [错误处理机制](grammar/error.html)（基本完成）
- [编程风格](grammar/style.html)（基本完成）

{% comment %}

{% if site.posts.size != 0 %}

## 最新文章

{% for post in site.posts %}
* {{ post.date | date_to_string }} [{{ post.title }}]({{ post.url }})
{% endfor %}

{% endif %}

{% if site.pages.size != 0 %}

## 最新页面

{% for page in site.pages limit:5 %}
{% if page.url !='/index.html' %}
* [{{ page.title }}]( {{ page.url }})（{{ page.date }}）
{% endif %}
{% endfor %}

{% endif %}

{% endcomment %}
