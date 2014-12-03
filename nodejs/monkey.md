---
title: process对象
category: nodejs
layout: page
date: 2014-10-20
modifiedOn: 2014-10-20
---

process对象提供node进程本身的信息。它可以通过全局变量process访问，不必使用require命令加载。

## 属性

process对象提供一系列属性，用于返回系统信息。

- **process.argv**：返回当前进程的命令行参数数组。
- **process.env**：返回一个对象，成员为当前shell的环境变量，比如process.env.HOME。
- **process.execPath**：node执行文件所在的目录，比如`/usr/lcoal/bin/node`。
- **process.installPrefix**：node的安装路径的前缀，比如`/usr/local`，则node的执行文件目录为`/usr/local/bin/node`。
- **process.pid**：当前进程的进程号。
- **process.platform**：当前系统平台，比如Linux。
- **process.stdout**：指向标准输出。
- **process.stdin**：指向标准输入。
- **process.stderr**：指向标准错误。
- **process.title**：默认值为“node”，可以自定义该值。
- **process.version**：Node的版本，比如v0.10.18。
