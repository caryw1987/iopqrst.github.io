---
title: 我应该从现有项目上吸取什么教训？
layout: page
category: nonsense
date: 2015-04-19
modifiedOn: 2015-04-19
---


## 前端部分

1. 前端也要有自己明确的规范，保证所有人按照一种书写方式开发，避免代码混乱。


## 后台部分

1. 代码规范

2. 数据库 id 设计时要考虑清楚使用的场景，不要所有的 id 都使用递增的数字（这个问题深有体会呀）。


## 其他

1. 不要把接口文档写在word文档中，维护起来太费时了,而且查找相关接口也很费劲，网上有很多协同工具，而且也加入了版本控制，很方便，能节省很多时间。

2. svn /git 代码提交必须要详细的注释

## 总结

1. 代码规范要深抓并要严格执行代码规范，要形成文档（哪怕是一点一点的完善，也要保存为文档方便每个人查看，github其实是一个很好的选择）。一定要从开始就要求严格，否则，人员几轮变动后代码就会“面目全非”。

2. code review 是一定要做的，可以借助工具去实现。 目前存在的问题：没有寻找一种方便快捷的review 方式，导致没有时间去review 所有的代码，很多代码没有经过review直接提交，出现很多不必要的bug。


## JavaScript的发布和标准化

1995年12月4日，Netscape公司与Sun公司联合发布了JavaScript语言。值得一提的是，17天之后Ruby语言也发布了它的第一个版本。

1996年3月，Navigator 2.0浏览器正式内置了JavaScript脚本语言。

1996年8月，微软模仿JavaScript开发了一种相近的语言，取名为JScript（JavaScript是Netscape的注册商标，微软不能用），首先内置于IE 3.0。网景公司面临丧失浏览器脚本语言的主导权的局面。

1996年11月，网景公司决定将JavaScript提交给国际标准化组织ECMA，希望JavaScript能够成为国际标准，以此抵抗微软。

1997年7月，ECMA组织发布262号标准文件（ECMA-262）的第一版，规定了浏览器脚本语言的标准，并将这种语言称为ECMAScript。这个版本就是ECMAScript 1.0版。之所以不叫JavaScript，一方面是由于商标的关系，Java是Sun公司的商标，根据一份授权协议，只有Netscape公司可以合法地使用JavaScript这个名字，且JavaScript已经被Netscape公司注册为商标，另一方面也是想体现这门语言的制定者是ECMA，不是Netscape，这样有利于保证这门语言的开放性和中立性。因此，ECMAScript和JavaScript的关系是，前者是后者的规格，后者是前者的一种实现。在日常场合，这两个词是可以互换的。

1998年6月，ECMAScript 2.0版发布。

1999年12月，ECMAScript 3.0版发布，成为JavaScript的通行标准，得到了广泛支持。

## ECMAScript和JavaScript的版本

2007年10月，ECMAScript 4.0版草案发布，对3.0版做了大幅升级，预计次年8月发布正式版本。草案发布后，由于4.0版的目标过于激进，各方对于是否通过这个标准，发生了严重分歧。以Yahoo、Microsoft、Google为首的大公司，反对JavaScript的大幅升级，主张小幅改动；以JavaScript创造者Brendan Eich为首的Mozilla公司，则坚持当前的草案。


## 周边大事记


2012年，微软发布TypeScript语言。该语言被设计成JavaScript的超集，这意味着所有JavaScipt程序，都可以不经修改地在TypeScript中运行。同时，TypeScript添加了很多新的语法特性，主要目的是为了开发大型程序，然后还可以被编译成JavaScript运行。

2012年，Mozilla基金会提出[asm.js](http://asmjs.org/)规格。asm.js是JavaScript的一个子集，所有符合asm.js的程序都可以在浏览器中运行，它的特殊之处在于语法有严格限定，可以被快速编译成性能良好的机器码。这样做的目的，是为了给其他语言提供一个编译规范，使其可以被编译成高效的JavaScript代码。同时，Mozilla基金会还发起了[Emscripten](https://github.com/kripken/emscripten/wiki)项目，目标就是提供一个跨语言的编译器，能够将LLVM的位代码（bitcode）转为JavaScript代码，在浏览器中运行。因为大部分LLVM位代码都是从C / C++语言生成的，这意味着C / C++将可以在浏览器中运行。此外，Mozilla旗下还有[LLJS](http://mbebenita.github.io/LLJS/)（将JavaScript转为C代码）项目和[River Trail](https://github.com/RiverTrail/RiverTrail/wiki)（一个用于多核心处理器的ECMAScript扩展）项目。目前，在可以被编译成JavaScript的[语言列表](https://github.com/jashkenas/coffee-script/wiki/List-of-languages-that-compile-to-JS)上，共有将近40种语言。

2013年，Mozilla基金会发布手机操作系统Firefox OS，该操作系统的整个用户界面都使用JavaScript。

2013年，ECMA正式推出JSON的[国际标准](http://www.ecma-international.org/publications/standards/Ecma-404.htm)，这意味着JSON格式已经变得与XML格式一样重要和正式了。

2014年，微软推出JavaScript的Windows库WinJS，标志微软公司全面支持JavaScript与Windows操作系统的融合。

## 参考链接

- Axel Rauschmayer, [The Past, Present, and Future of JavaScript](http://oreilly.com/javascript/radarreports/past-present-future-javascript.csp)
- John Dalziel, [The race for speed part 4: The future for JavaScript](http://creativejs.com/2013/06/the-race-for-speed-part-4-the-future-for-javascript/)
- Axel Rauschmayer, [Basic JavaScript for the impatient programmer](http://www.2ality.com/2013/06/basic-javascript.html)
- resin.io, [Happy 18th Birthday JavaScript! A look at an unlikely past and bright future](http://resin.io/happy-18th-birthday-javascript/)
