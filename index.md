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

<h2 id="code">代码段搜集</h2>

- [javascript 部分](code/javascript.html)
- [java](code/java.html)
- [other](code/other.html)

<h2 id="nonsense">谈天说地</h2>

- [如果我是一个老板](nonsense/if-i-were-a-boss.html)
- [我应该从现有项目上吸取什么教训](nonsense/what-should-i-learn-from-the-existing-project.html)
- [我们之间的差距仅仅只是一所大学吗?](nonsense/the-gap-between-us-just-a-university.html)

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
