---
layout: hexo
title: hexo + github page 搭建的总结
date: 2017-06-07 20:05:21
tags: hexo
---

作为一个初次接触git和hexo的菜菜鸟，即使是按照手把手教导教程，依然会碰到各种问题。在将近一个星期的折腾后，终于告一段落了。

在 windows 中安装hexo的前置条件为：

- [node.js](https://nodejs.org/)
- [git 客户端](https://git-scm.com/)

此外，还需要拥有一个 [github 账号](https://github.com/)。

<!-- more -->

在安装好node.js 跟 。git客户端后，在要安装hexo的文件夹上单击右键选择 git bush。在弹出的bush界面中输入

{% codeblock lang:bash %}
npm install hexo-cli -g
{% endcodeblock %}

这里就遇到了第一个坑：在无响应很久以后报错，无法安装。在各种google以后发现是源被墙的过，同时发现了一个很适合像我这种小白使用的工具——nrm。

nrm 是一个 NPM 源管理器，允许你快速地在如下 NPM 源间切换：

- [npm](https://www.npmjs.org)
- [cnpm](http://cnpmjs.org)
- [strongloop](http://strongloop.com)
- [european](http://npmjs.eu)
- [australia](https://npmjs.org.au)
- [nodejitsu](https://www.nodejitsu.com)
- [taobao](http://npm.taobao.org)
  输入以下代码安装使用

```bash
npm install -g nrm
nrm ls #列出可选源
nrm use cnpm #切换至cnpm源
```

使用nrm还有一个好处就是切换源以后还可以继续用 npm 命令进行安装而不需要换成如：cnpm，这样的命令，在后期hexo初始化的时候可以避免很多问题。

想要详细了解nrm，请到[https://github.com/Pana/nrm](https://github.com/Pana/nrm)。

在解决好这个问题之后，就可以对hexo进行初始化了。

```js
hexo init
```



这篇即打算做练习又打算做总结，先写到这里，有空再更。