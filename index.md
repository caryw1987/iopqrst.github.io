---
layout: homepage
title: 以后这就是我的blog啦 :)
title_en: Yi hou zhe jiu shi wo de bo ke le :)
date: 2015-04-16
modifiedOn: 2015-04-16
---
	
<h2 id="introduction">导论</h2>

- [前言](introduction/preface.html)
- [为什么学习JavaScript？](introduction/why.html)
- [JavaScript的历史](introduction/history.html)

<h2 id="myself">我自己做测试的部分</h2>

- [CommonJS规范](myself/commonjs.html)
- [接口评估](myself/interface.html)

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
